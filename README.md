# Wizardy-
A real-time hand &amp; finger tracking web app using MediaPipe. Detects up to two hands with 21 keypoints each, visualizes gestures, and displays FPS and stats — all running directly in your browser via webcam.

## Model precision choices

The app now ships exclusively with the <code>float16</code> MediaPipe Hand Landmarker build. In practice we observed negligible tracking differences between float16 and float32 for the gestures this demo highlights, while the smaller float16 asset:

- Downloads faster (especially on mobile networks) and unblocks the first-run experience.
- Uses less GPU/CPU memory, which helps underpowered laptops and phones stay responsive.
- Avoids driver quirks where float32 fails to obtain a GPU delegate and silently falls back to slower execution paths.

Because of these trade-offs we removed the float32 toggle entirely and recommend the single float16 option for every device.

### Verification snapshot

Manual smoke tests with pinch and open-palm gestures on a 720p webcam stream showed float16 tracking to be stable enough for the demo scenarios, even though float32 can deliver marginally steadier fingertips. The load-time savings and broader device compatibility from float16 outweighed the subtle accuracy gains, so the float32 build was retired.
