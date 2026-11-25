# DocStamp

**Privacy-first browser tool to redact Aadhaar/PAN digits, strip EXIF/GPS metadata, and stamp dated purpose watermarks on ID copies locally via HTML5 Canvas.**

[![License: MIT](https://img.shields.io/badge/License-MIT-3FB950.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![Stack: HTML / JavaScript](https://img.shields.io/badge/Stack-HTML%20%2F%20JavaScript-15E0ED.svg?style=flat-square)](https://github.com/shrijeetdev/docstamp)
[![Live Demo](https://img.shields.io/badge/Live%20demo-shrijeetdev.github.io-3FB950.svg?style=flat-square)](https://shrijeetdev.github.io/docstamp/)
[![Privacy: No Uploads](https://img.shields.io/badge/Privacy-No%20uploads-0D1117.svg?style=flat-square)](#privacy)

**[▶ Open the live tool](https://shrijeetdev.github.io/docstamp/)**

---

## Why it exists

Across India, sharing photocopies or scans of Aadhaar cards, PAN cards, passports, and driving licences is routine for rental agreements, KYC checks, job onboarding, hotel check-ins, bank accounts, and SIM card activations. Unmarked, full-number ID copies stored in messaging apps or third-party folders are easily leaked or reused without consent.

DocStamp lets you redact sensitive digits and stamp a clear, dated purpose across the document directly in your browser before sending it—without uploading your ID to an unknown web server.

---

## Features

- **100% Client-Side Processing:** Single self-contained `index.html` with zero external libraries, zero CDNs, and zero network requests.
- **Flexible Image Input:** Load JPG, PNG, or WebP images via drag-and-drop, file picker, or direct clipboard paste (`Ctrl+V` / `⌘V`), or test immediately with a built-in synthetic sample ID card.
- **Purpose Watermarks & Presets:** Tile custom diagonal text across the entire document with live controls for opacity (`5%`–`80%`), font size (`12px`–`54px`), rotation angle (`-65°` to `65°`), colour swatches/picker, and an optional solid purpose footer band. Includes one-click presets (`KYC`, `Rental agreement`, `Job application`, `Hotel check-in`, `Bank account`, `SIM card`, `Custom`) pre-filled with today's date in `en-IN` format.
- **Interactive Redaction Masks:** Drag with mouse or touch to create redaction boxes using either **Solid Black-Out** or **Pixelate** styles. Click any box to reposition it, drag corner handles to resize, undo the last mask, or press `Delete`/`Backspace` to remove a selected box.
- **Masked Aadhaar Helper:** One-click `+ Mask first 8 digits` button adds a pre-proportioned movable, resizable mask box designed to hide the first 8 digits while leaving the last 4 digits visible.
- **Clean Metadata-Stripped Export:** Re-encodes the flattened canvas into a fresh JPG (with adjustable quality from `50%`–`100%`) or lossless PNG, stripping embedded EXIF, camera, and GPS tags and displaying the resulting file size.
- **Accessible, Responsive Interface:** Automatic dark/light theme via `prefers-color-scheme`, keyboard navigation, visible focus states, `prefers-reduced-motion` support, and mobile layout support down to `375px`.

---

## How to use

1. **Load your document:** Click **Load Image**, drop a JPG/PNG/WebP file onto the canvas, paste from your clipboard, or click **Try a sample** to practice on a specimen card.
2. **Redact sensitive fields:** Drag across numbers, QR codes, or addresses to cover them with solid black-out or pixelation, or click **+ Mask first 8 digits** and adjust the box over your Aadhaar number.
3. **Configure your watermark:** Pick a purpose preset (such as `Rental agreement` or `KYC`), fill in the recipient name and verify the date, and adjust opacity, angle, colour, or the solid footer band.
4. **Download your protected copy:** Choose **JPG** or **PNG** and click **Download Protected Copy** to save a flattened, EXIF-free image.

---

## What is a Masked Aadhaar?

A **Masked Aadhaar** replaces the first 8 digits of a 12-digit Aadhaar number with blanked-out or masked characters while keeping only the **last 4 digits** visible for verification.

According to guidelines from the Unique Identification Authority of India ([UIDAI](https://uidai.gov.in)), sharing a masked copy is recommended for routine identity verification—such as hotel check-ins, travel, or SIM card issuance—where full Aadhaar number disclosure is not required, reducing the risk of unauthorized misuse while still proving identity.

---

## How it works

1. **Local Canvas Decoding:** When you select, drop, or paste a file, the browser reads it into memory via `FileReader` and renders it onto an HTML5 `<canvas>` element.
2. **Pixel-Level Flattening:** Redaction masks (solid fill or block-averaged pixelation), diagonal watermark text, and the optional footer banner are drawn directly onto the canvas bitmap.
3. **Metadata Stripping via Re-Encoding:** Calling `canvas.toBlob()` generates a brand-new JPEG or PNG binary stream from raw RGBA pixel data alone. Any original EXIF headers, device serials, timestamps, or GPS coordinates present in the source file are discarded during re-encoding.

---

## Privacy

- **Nothing leaves your browser:** DocStamp has no backend server, no cloud storage, no cookies, and no third-party analytics or tracking scripts.
- **Zero network requests:** You can disconnect from the internet after loading the page (or open `index.html` offline) and every feature continues to work identically.
- **Permanent redactions:** Masks are baked into the exported pixels rather than saved as reversible vector layers.

---

## Run locally & deploy

### Run locally
Because DocStamp has no build step or dependencies:
1. Clone or download this repository:
   ~~~bash
   git clone https://github.com/shrijeetdev/docstamp.git
   ~~~
2. Double-click `index.html` to open it directly in any modern browser, or serve the folder with any static file server (for example, `python3 -m http.server 8080`).

### Deploy your own copy on GitHub Pages
1. Fork or push this repository (`index.html`) to your GitHub account.
2. Open your repository on GitHub and go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**, select your `main` branch and `/ (root)` folder, and click **Save**.

---

## Contributing

Contributions, bug reports, and accessibility or usability improvements are welcome. Please open an issue or submit a pull request on [github.com/shrijeetdev/docstamp](https://github.com/shrijeetdev/docstamp) keeping the single-file, zero-dependency architecture intact.

---

## License

This project is open source and licensed under the [MIT License](https://opensource.org/licenses/MIT).

---

Made by [Shrijeet Singh](https://github.com/shrijeetdev). If this saved you time, a ⭐ helps others find it.
