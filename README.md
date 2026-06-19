# Learning-Vulkan
**Working through the [Vulkan Tutorial](https://docs.vulkan.org/tutorial/latest/00_Introduction.html) to learn low-level graphics programming with the Vulkan API**

---

## Sessions

### Session 1 - First Steps
**Goals:**
- [x] **Introduction:** Read through what Vulkan is, why it exists, and what the tutorial covers.
- [x] **Overview:** Get a high-level understanding of the Vulkan render loop and its key concepts.
- [x] **Development Environment:** Set up the full toolchain (Vulkan SDK, GLFW, GLM, compiler).
- [x] **Base Code:** Implement the application skeleton with main loop and GLFW window.

**Review & Progress Log:**
- **~12.06.2026 - Introduction, Overview and Development Environment**
  - Read through the motivation behind Vulkan and understood why it was introduced as an alternative to OpenGL and Direct3D. Unlike older APIs, Vulkan is fully explicit: the driver does almost nothing automatically, which means significantly more boilerplate but also far more control over performance and behavior.
  - Studied the high-level overview of the Vulkan render loop, covering the key objects that will appear throughout the tutorial: physical and logical devices, queue families, swap chains, render passes, and command buffers. Having this mental map early makes the later chapters much easier to follow.
  - Installed and configured the full development environment, including the Vulkan SDK with its bundled validation layers, GLFW for cross-platform window and input handling, and GLM as the math library. Verified that everything compiles and links correctly before moving on.

---

### Session 2 - Instance and Device Setup
**Goals:**
- [x] **Instance:** Create a VkInstance and enable validation layers.
- [x] **Validation Layers:** Set up the debug messenger via VK_EXT_debug_utils to catch API misuse.
- [x] **Physical Devices and Queue Families:** Pick a suitable GPU and query its queue families.
- [x] **Logical Device and Queues:** Create a VkDevice and retrieve the graphics and presentation queue handles.

**Review & Progress Log:**
- **19.06.2026 - Instance through Logical Device**
  - Created a VkInstance, which is the entry point into the Vulkan API and represents the connection between the application and the Vulkan library. Enabling validation layers at this stage allows the runtime to intercept API calls and report misuse during development.
  - Configured a debug messenger callback using VK_EXT_debug_utils so that validation layer output appears in the console. This requires explicitly creating and destroying a VkDebugUtilsMessengerEXT handle, as it is not active by default.
  - Iterated over the available physical devices, checked each one for the required queue family support, and selected the first suitable GPU. Vulkan exposes different queue families for graphics, compute, transfer, and presentation operations separately, so finding the right combination is an explicit step.
  - Created a logical device on top of the chosen physical device, which serves as the main interface for all further Vulkan calls, and retrieved the handles for the graphics and presentation queues.

---

### Session 3 - Presentation
**Goals:**
- [x] **Window Surface:** Create a VkSurfaceKHR via GLFW to connect Vulkan to the OS window.
- [ ] **Swap Chain:** Set up the swap chain for presenting rendered frames to the screen.
- [ ] **Image Views:** Create image views to access the swap chain images.
- [ ] **Graphics Pipeline - Introduction:** Read through the graphics pipeline overview.

**Review & Progress Log:**
- **19.06.2026 - Window Surface**
  - Created a VkSurfaceKHR using GLFW's built-in Vulkan integration, which abstracts away the platform-specific surface creation code that would otherwise differ between Windows, Linux, and macOS. The surface represents the connection between the Vulkan instance and the OS window, and is what the swap chain will later present rendered images to.
  - Reached the Swap Chain section - picking up here next session.

---

### Session 4 - Graphics Pipeline Basics
**Goals:**
- [ ] **Shader Modules:** Write basic GLSL shaders and compile them to SPIR-V for use in Vulkan.
- [ ] **Fixed Functions:** Configure the fixed-function pipeline stages (viewport, rasterizer, blending etc.).
- [ ] **Render Passes:** Define the attachments and subpasses used during rendering.
- [ ] **Pipeline Conclusion:** Assemble and create the full VkPipeline object.

---

### Session 5 - Drawing
**Goals:**
- [ ] **Framebuffers:** Create framebuffers that bind the render pass attachments to image views.
- [ ] **Command Buffers:** Allocate and record command buffers for rendering commands.
- [ ] **Rendering and Presentation:** Implement the draw loop with synchronization (semaphores, fences).
- [ ] **Frames in Flight:** Allow multiple frames to be processed concurrently.

---

### Session 6 - Vertex Buffers
**Goals:**
- [ ] **Swap Chain Recreation:** Handle window resize by recreating the swap chain.
- [ ] **Vertex Input Description:** Describe the vertex data layout to the pipeline.
- [ ] **Vertex Buffer Creation:** Allocate and fill a GPU-side vertex buffer.
- [ ] **Staging Buffer:** Use a staging buffer for efficient CPU-to-GPU data transfer.

---

### Session 7 - Uniforms and Textures
**Goals:**
- [ ] **Index Buffer:** Reduce vertex data duplication with an index buffer.
- [ ] **Descriptor Layout and Buffer:** Define uniform buffer descriptors and allocate the buffer.
- [ ] **Descriptor Pool and Sets:** Create descriptor sets to bind the uniform buffer to the pipeline.
- [ ] **Texture Images:** Load an image and upload it to a GPU-accessible format.

---

### Session 8 - Texture Mapping and Depth
**Goals:**
- [ ] **Image View and Sampler:** Create an image view and sampler to read the texture in shaders.
- [ ] **Combined Image Sampler:** Bind the texture to the descriptor set and sample it in the fragment shader.
- [ ] **Depth Buffering:** Add a depth attachment to handle correct 3D occlusion.
- [ ] **Loading Models:** Load a real OBJ model and render it with the full pipeline.

---

### Session 9 - Polish and Compute
**Goals:**
- [ ] **Generating Mipmaps:** Generate and use mipmaps for better texture quality at a distance.
- [ ] **Multisampling:** Enable MSAA to reduce aliasing on geometry edges.
- [ ] **Compute Shader:** Learn the compute pipeline and dispatch GPU compute work.
- [ ] **Ecosystem Utilities:** Explore useful Vulkan ecosystem tools (renderdoc, validation, profiling).
