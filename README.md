# bitImage - Image to LCD Bitmap Converter

[![Online Demo](https://img.shields.io/badge/Online%20Demo-colbot.github.io%2FbitImage-38bdf8?style=flat-square&logo=github)](https://colbot.github.io/bitImage/)
[![Language](https://img.shields.io/badge/Language-English%20%7C%20%E4%B8%AD%E6%96%87-10b981?style=flat-square)](#internationalization)
[![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](LICENSE)

**[English](README.md)** | **[简体中文](README_CN.md)**

**bitImage** is a pure, single-file HTML5 web tool designed to convert grayscale and color images into 1-bit depth bitmap masks for monochrome displays (LCD, OLED, E-Paper). It runs 100% locally in your browser with zero dependencies, providing real-time live preview, Floyd-Steinberg error-diffusion dithering, aspect-ratio-aware cropping, and instant C-array code export.

🌐 **Try it online:** [https://colbot.github.io/bitImage/](https://colbot.github.io/bitImage/)

---

## ✨ Features

- **🚀 100% Client-Side & Zero-Dependency**:
  - Encapsulated in a single self-contained HTML file ([`index.html`](index.html)).
  - Runs offline with zero external network requests or CDN dependencies.
  - Fully compatible with **Microsoft Edge**, **Google Chrome**, **Mozilla Firefox**, and **Safari**.
  - All image processing occurs strictly on your device—no data is uploaded to any server.

- **📁 Intuitive Image Loading & Built-in Test Pattern**:
  - Drag-and-drop or browse for local files (`PNG`, `JPEG`, `WEBP`, `BMP`, `GIF`, `SVG`).
  - Pre-loaded with a test pattern on startup so you can immediately experiment with all features.

- **📐 Flexible Target LCD Specifications**:
  - Customizable LCD resolution (width and height in pixels).
  - Built-in standard presets:
    - `128 × 64` (SSD1306 OLED, ST7920 graphic LCD)
    - `128 × 32` (Mini 0.91" OLED)
    - `256 × 64` (Wide Graphic LCD)
    - `84 × 48` (Nokia 5110 PCD8544)
    - `160 × 160` (Monochrome Square LCD)
    - `240 × 128` (T6963C LCD)
  - Non-square **Pixel Aspect Ratio**: configure custom **Pixel Width Ratio** and **Pixel Height Ratio** (e.g., $1.0 : 1.5$ or $2.0 : 1.0$).
  - Physical LCD aspect ratio lock constraint: maintains the true physical display ratio $(W \cdot R_w) : (H \cdot R_h)$ to avoid image distortion.

- **✂️ Interactive Crop Box with Anchor Handles**:
  - Draggable selection box over the image preview with rule-of-thirds alignment grid.
  - Smooth 8-handle anchor resizing with boundary clamping.
  - Click anywhere on the image preview to quickly re-center the crop box.
  - **Fit Selection to Full Image** button for rapid full-frame mapping.

- **⚙️ 1-Bit Binarization & Dithering**:
  - **Threshold Slider**: Dynamic `0` to `255` threshold mover with live numerical readout.
  - **Floyd-Steinberg Error-Diffusion Dithering**: Smooth gradients and natural photographic reproduction.
  - **Invert Bits**: One-click bitwise toggle (`0` ⇄ `1`) for active-high or active-low LCD driver ICs.
  - **Custom Color Pickers**: Customize active pixel color (Result 1) and background/off color (Result 0).
  - **Realistic Dot-Matrix Simulation**: Toggleable LCD pixel gap to simulate physical dot-matrix screens.

- **⚡ Real-Time Live Preview**:
  - Every adjustment (slider moves, handle drags, color picks, ratio tweaks) updates the LCD matrix preview immediately without needing a manual convert button.
  - Built-in Zoom selector (`Auto`, `1x`, `2x`, `3x`, `4x`, `6x`).
  - Live statistics: Total Pixels, Active Bits (1), Inactive Bits (0), and Buffer Byte Size.

- **💾 Developer Code Export**:
  - **C Array Format**:
    - `Horizontal (X-first, MSB)`
    - `Horizontal (X-first, LSB)`
    - `Vertical Page (SSD1306 / Nokia PCD8544)`
    - `Raw Hex Array`
  - One-click **Copy C Array** to clipboard.
  - Prominent **Download 1-Bit PNG** button.

- **🌍 Bilingual Support**:
  - One-click instant switching between **English** and **简体中文** (Chinese).

---

## 🚀 Getting Started

### 1. Online Access
Open [https://colbot.github.io/bitImage/](https://colbot.github.io/bitImage/) directly in any modern web browser.

### 2. Local Offline Usage
1. Clone the repository:
   ```bash
   git clone https://github.com/colbot/bitImage.git
   cd bitImage
   ```
2. Double-click or open [`index.html`](index.html) in your browser:
   ```bash
   # Linux
   xdg-open index.html
   # or
   firefox index.html

   # macOS
   open index.html

   # Windows
   start index.html
   ```

---

## 🛠️ Typical Workflow

1. **Load Image**: Drag and drop your image into the upload area or click browse.
2. **Select LCD Specs**: Pick a preset (e.g., `128x64`) or enter your target width, height, and pixel ratio.
3. **Adjust Target Area**: Drag and scale the crop box on the preview to choose the target region.
4. **Tune Binarization**:
   - Move the threshold slider to adjust lightness.
   - Toggle **Enable Dithering** to compare thresholding vs. Floyd-Steinberg error diffusion.
   - Check **Revert Result** if your LCD controller requires inverted bit polarity.
5. **Export**:
   - Choose your preferred driver format (`Horizontal MSB`, `Vertical Page`, etc.).
   - Click **Copy C Array** to paste the bitmap directly into your firmware / Arduino / C++ code.
   - Or click **Download 1-Bit PNG** to save the monochrome bitmap file.

---

## 📋 Driver Format Reference

| Format | Orientation | Byte Organization | Common Hardware |
| :--- | :--- | :--- | :--- |
| **Horizontal (MSB)** | Rows first (left to right, top to bottom) | 8 pixels per byte, leftmost pixel is MSB (bit 7) | Adafruit GFX, ST7920, epaper |
| **Horizontal (LSB)** | Rows first (left to right, top to bottom) | 8 pixels per byte, leftmost pixel is LSB (bit 0) | Various embedded microcontrollers |
| **Vertical Page** | Columns first in 8-pixel horizontal bands | 8 vertical pixels per byte, top pixel is LSB | SSD1306, SH1106, PCD8544 (Nokia 5110) |
| **Raw Hex Array** | Sequential 8-pixel chunks | Packed binary bytes in hexadecimal | Custom graphic pipelines |

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
