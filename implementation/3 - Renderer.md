# 3 - Renderer
In ICmd, renderer converts nodes into raw text.

## 3.1 - Principles

Renderer is the key part of a TUI framework and its optimization as a component that frequently outputs large buffer. ICmd designs a renderer with as little overhead as possible. The principles are as follows:

### Render when Necessary
Rendering is not a coherent process with fps in ICmd. Instead, thanks to the responsive framework, we can render specific parts only when they update. For example, when there is no external signal, the program will actually be static, so the renderer won't opt to run any update onto the console. Instead, if there is a click on a node which changes its background color into green, the renderer will receive the signal and perform updates. This technique eliminates a majority of trivial updates and greatly improves the overall performance.

### Never Print Extra things
Escape codes can stylize the output characters. So we can always print colorful texts onto the terminal. ICmd uses some technique to insert minimal escape codes and necessary characters while keeping the visual effect.

Escape codes can also control where to print. So temporally we compare the frame to be rendered with the last one and only update with difference. It is a more intuitive way that we can know which node is being rendered, precisely and subtly calculate where there is difference, and perform partial updates.