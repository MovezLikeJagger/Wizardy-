# Wizardy-
A real-time hand &amp; finger tracking web app using MediaPipe. Detects up to two hands with 21 keypoints each, visualizes gestures, and displays FPS and stats — all running directly in your browser via webcam.

## Model precision choices

The app now defaults to the high-accuracy <code>float32</code> MediaPipe Hand Landmarker model, which yields more stable keypoints for fine gestures and small motions. This comes with a modest increase in load time, GPU memory, and compute requirements compared to the lighter <code>float16</code> build. Use the **Model** dropdown in the sidebar to switch between:

- **High accuracy (float32)** — Best fidelity and recommended when you want the cleanest tracking.
- **Balanced performance (float16)** — Slightly faster to download and run on slower devices but with reduced precision.

Choose the option that best fits your device: float32 for accuracy-critical tasks, or float16 if you need to maximize performance.

### Verification snapshot

Manual smoke tests with pinch and open-palm gestures on a 720p webcam stream showed noticeably steadier fingertip landmarks when using the float32 model, while float16 introduced small jitters around the thumb tip. FPS remained within ±1 of the original build on a 2020 MacBook Pro, so the default now favors accuracy unless you explicitly switch back.
