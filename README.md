
3D Website application built with [Three.js](https://threejs.org/) that allows users to navigate 3D 

## Features
- **Boundary Constraints**: The user is strictly confined within the street's x and z boundaries, preventing escape from the model.
- **Fixed Controls**: Two buttons ("Forward (W)" and "Backward (S)") are fixed at the top center of the screen for intuitive movement along the street.
- **Mouse-Based Camera Control**: Click the canvas to lock the mouse pointer and rotate the camera using mouse movement.
- **Keyboard Support**: Move using `W` (forward), `S` (backward), `A` (left), and `D` (right) keys.
- **Responsive Design**: The scene adapts to window resizing for a consistent experience across devices.
- **Night Sky and Lighting**: A starry night sky background with ambient, directional, and point lighting enhances the visual experience.

## Prerequisites
- A modern web browser (e.g., Chrome, Firefox, Edge) with WebGL support.
- Internet access to load external dependencies (Three.js, GLTFLoader) and the 3D street model.

## Installation

1. Open `index.html` in a web browser. You can use a local server for better performance:
   ```bash
   npx http-server
   ```
   Then navigate to `http://localhost:8080` in your browser.

## Usage
1. Open the application in a web browser.
2. Click the canvas to enable pointer lock for mouse-based camera rotation.
3. Use the on-screen buttons or keyboard to navigate:
   - **Forward (W)**: Move forward along the street (z-axis).
   - **Backward (S)**: Move backward along the street.
   - **A**: Strafe left.
   - **D**: Strafe right.
4. The street extends infinitely as you move, with new segments loaded seamlessly.
5. The user is confined within the street boundaries (x: [-10, 10], z: within dynamic model bounds).

## Project Structure
- `index.html`: The main HTML file containing the application logic, styles, and Three.js code.
- External dependencies (loaded via CDN):
  - Three.js: `https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js`
  - GLTFLoader: `https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/loaders/GLTFLoader.js`
- 3D Model: Loaded from `https://6lj.github.io/3DWEB/model.glb`

## Technical Details
- **Three.js Version**: r128
- **Model Loading**: Uses GLTFLoader to load a 3D street model, scaled and positioned for seamless tiling.
- **Camera**: Perspective camera with a 90-degree field of view, locked at y=0.5 for consistent height.
- **Movement**: Restricted to the xz-plane with a move speed of 0.1 units per frame.
- **Boundaries**:
  - X-axis: Clamped to [-10, 10].
  - Z-axis: Dynamically adjusted based on loaded street segments, with a 2-unit margin.
- **Infinite Street**: New models are loaded at precise z-offsets when the camera approaches the edge of the current street segment, ensuring a continuous path.
- **Controls**: Fixed-position buttons at the top center (`position: fixed`, `z-index: 1000`) for forward/backward movement, supplemented by keyboard controls.

## Known Issues
- If the 3D model fails to load (e.g., due to network issues), an error message is displayed in the top-left corner.
- Performance may vary depending on the browser and device, especially when loading new street segments.

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Make your changes and commit (`git commit -m "Add your feature"`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a pull request.
