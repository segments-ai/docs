# WebGPU in Linux

{% hint style="warning" %}
WebGPU is not supported on all hardware setups. This guide provides a couple of things to verify, but there is **no guarantee** that it will work.
{% endhint %}

Rendering issues in WebGPU on Linux are frequently caused by browser configuration settings or hardware driver compatibility. This guide provides a structured approach to verifying, enabling, and optimizing WebGPU performance.

### 1. Initial Status Verification

The first step in troubleshooting is to determine if the browser currently recognizes and supports WebGPU.

1. Open Google Chrome and navigate to `chrome://gpu`.
2. Locate the **Graphics Feature Status** section.
3. Check the status of the **WebGPU** line:
   * **Hardware accelerated:** WebGPU is active.
   * **Disabled:** WebGPU is not currently active and requires manual configuration.

***

### 2. Driver Requirements (NVIDIA Users)

WebGPU performance on Linux is highly dependent on system drivers.

* **Proprietary Drivers:** It is essential to use official proprietary NVIDIA drivers at their latest version.
* **Open Source Drivers:** Alternative open-source drivers (such as Nouveau) often lack the necessary Vulkan support for WebGPU, leading to rendering failures or significant bugs.

Verify your driver version through your distribution’s software settings or by running `nvidia-smi` in the terminal.

***

### 3. Manual Browser Configuration

If WebGPU is listed as “Disabled,” the following internal browser flags should be modified to bypass default Linux restrictions.

1. **Enable Vulkan Support:** Navigate to `chrome://flags`, search for **Vulkan**, and set the status to **Enabled**.
2. **Override Software Rendering List:** Navigate to `chrome://flags/#ignore-gpu-blocklist` and set it to **Enabled**. This forces Chrome to utilize the GPU even if the hardware/driver combination is not officially supported.

If activating these flags doesn’t resolve the issue, try the approach in section 4.

***

### 4. CLI Launch flags

To ensure all browser flags are properly applied when launching chrome, it needs to launch a clean session. This ensures it doesn’t reuse previous settings.

To achieve that, we add an additional flag (`--user-data-dir="$HOME/.chrome-webgpu"`) to ensure it doesn’t conflict with already running processes.

```bash
google-chrome --user-data-dir="$HOME/.chrome-webgpu" --enable-features=Vulkan,VulkanFromANGLE --use-angle=vulkan --ignore-gpu-blocklist
```

If the browser feels like it isn’t running without issues or is unstable, we can force regular UI rendering to use GL and only render webgpu related things with Vulkan. To try this, add the following flag: `--use-angle=gl`

***

### 5. Dual graphics cards setup

In many Linux environments—particularly laptops with dual graphics (Intel and NVIDIA)—Chrome may default to the integrated Intel GPU rather than the high-performance NVIDIA hardware.

We need to set some environment variables so chrome knows which GPU to use:

```bash
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia google-chrome --user-data-dir="$HOME/.chrome-webgpu" --enable-features=Vulkan,VulkanFromANGLE --use-angle=vulkan --ignore-gpu-blocklist
```

#### Command Breakdown

* `__NV_PRIME_RENDER_OFFLOAD=1` and `__GLX_VENDOR_LIBRARY_NAME=nvidia`: Forces the application to utilize the discrete NVIDIA GPU.
* `--user-data-dir="$HOME/.chrome-webgpu"`: ensures a clean new instance of chrome is launched
* `--enable-features=Vulkan,VulkanFromANGLE`: Enables the Vulkan backend.
* `--use-angle=vulkan`: Directs the ANGLE graphics abstraction layer to use Vulkan.
* `--ignore-gpu-blocklist`: Bypasses the internal list of blocked hardware.

***

### 5. Summary and Reporting

After performing the steps above, return to `chrome://gpu` to verify that WebGPU now displays as **Hardware accelerated**.

\<aside>\
⚠️

WebGPU is not supported on all hardware setups. Note that even if chrome displays “**Hardware accelerated”** there is **no guarantee** that it works without issues.

\</aside>
