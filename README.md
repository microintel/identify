**Live:** https://microintel.github.io/identify/

# Identify — Face Recognition

A single-file, browser-based face detection and recognition app. Everything — camera capture, face detection, landmark tracking, expression analysis, and face recognition — runs **locally in the browser**. No server, no backend, no data leaves the device.

Developed by **Microintel**.

---

## Features

- **Live camera recognition** — detect and identify faces in real time from your webcam.
- **Image upload mode** — run detection and recognition on a single uploaded photo instead of a live feed.
- **Face registration** — register a person by name with one clear reference photo; their face descriptor (and a thumbnail) is stored locally.
- **Registered people list** — view everyone you've registered, each shown with their photo, with the option to delete them.
- **68-point facial landmarks** — optional overlay of detailed landmark points.
- **Expression detection** — optional overlay of detected expressions (happy, sad, surprised, etc.) with confidence bars.
- **Live readout** — face count, recognized count, peak count, and FPS while the camera is running.
- **Fully offline data storage** — registered people are stored in the browser's IndexedDB; nothing is uploaded anywhere.
- **Responsive layout** — a dedicated mobile layout (register/people section up top, camera below) and a wider two-column desktop layout that uses screen space efficiently.
- **Collapsible UI** — the Register/Registered People section can be fully collapsed, and the registration form only appears when you tap "+ Add New Person."

---

## Getting Started

1. Download `index.html`.
2. Open it in a modern browser (Chrome, Firefox, Safari, or Edge).
   - Camera access requires **HTTPS** or **localhost** — opening the file directly (`file://`) will work for image upload mode, but the camera will need to be served over `https://` or `http://localhost`.
3. Grant camera permission when prompted (only needed for Camera mode).

No build step, no npm install, no server setup required — it's a single static HTML file.

---

## How to Use

### Register a person
1. Open the **People** section (tap the header if it's collapsed).
2. Switch to the **Register Face** tab.
3. Tap **+ Add New Person**.
4. Enter a name and choose a clear, front-facing photo of the person.
5. The face descriptor and photo are saved locally in your browser.

### Recognize faces via camera
1. Make sure you're on the **Camera** mode (default).
2. Tap **Start Camera** and allow camera access.
3. Detected faces are boxed and labeled in real time; registered people are identified by name.
4. Tap **Stop** to end the session.

### Recognize faces in an uploaded image
1. Switch to **Upload** mode.
2. Tap **Choose Image** and select a photo.
3. Detected faces, landmarks, and expressions are analyzed automatically.

### Manage registered people
1. Open the **People** section → **Registered People** tab.
2. See everyone you've registered, with their photo.
3. Tap **Delete** to remove someone.

### Settings
- **68 Landmarks** — toggle the facial landmark overlay.
- **Expressions** — toggle the expression detection overlay and confidence bars.

---

## Tech Stack

- **[face-api.js](https://github.com/justadudewhohacks/face-api.js)** (v0.22.2) — face detection, landmarks, expressions, and recognition, powered by TensorFlow.js, running entirely client-side.
- **SSD MobileNet v1** — the underlying face detector model.
- **IndexedDB** — local, persistent storage for registered people (name, face descriptor, and photo).
- **Vanilla HTML/CSS/JavaScript** — no frameworks, no build tools.

---

## Privacy

All processing — detection, recognition, and storage — happens entirely in your browser. Photos and face descriptors are stored in your browser's IndexedDB and are never transmitted to any server. Clearing your browser data (or using a different browser/device) will remove all registered people.

---

## Browser Support

Requires a modern browser with support for:
- `getUserMedia` (camera access)
- IndexedDB
- Canvas 2D
- WebGL (used internally by TensorFlow.js/face-api.js for inference)

Camera access requires a secure context (`https://` or `http://localhost`).

---

## Known Limitations

- Recognition accuracy depends on photo quality, lighting, and camera resolution.
- Only one face should be present in a registration photo.
- Face data is stored per-browser/per-device and does not sync across devices.

---

## License

Face detection/recognition powered by the open-source [face-api.js](https://github.com/justadudewhohacks/face-api.js) library (MIT License).
