# Bezier 2 — Generative Art

[![Live Demo](https://img.shields.io/badge/demo-live-green?style=for-the-badge)](https://reyrove.github.io/Bezier-2-Generative-Art)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

> **Animated generative bezier curves.** Each refresh creates a unique, continuously rotating composition of smooth closed bezier curves with dynamic movement, gradient colors, and seed-based patterns.

## 🎨 Live Demo

<div align="center">
  <a href="https://reyrove.github.io/Bezier-2-Generative-Art" target="_blank">
    <img src="demo-screenshot.jpg" alt="Bezier 2 Website Demo" width="800" style="border-radius: 12px; box-shadow: 0 8px 32px rgba(0,0,0,0.4);"/>
  </a>
  <br><br>
  <a href="https://reyrove.github.io/Bezier-2-Generative-Art" target="_blank">
    <img src="https://img.shields.io/badge/🌐_View_Live_Demo-0a0a0a?style=for-the-badge&logo=githubpages&logoColor=white&color=c9a84c" alt="View Live Demo" width="300"/>
  </a>
  <br>
  <em>Click the image or button to experience the generative art</em>
</div>

## 👕 Apparel Preview

<div align="center">
  <img src="Bezier-2.jpg" alt="Bezier 2 on T-Shirt" width="600" style="border-radius: 12px; box-shadow: 0 8px 32px rgba(0,0,0,0.3);"/>
  <br>
  <em>Bezier 2 artwork printed on a T-shirt</em>
</div>

## ✨ Features

- **Animated Bezier Curves** — Smooth closed curves with organic, flowing motion
- **Dynamic Point Movement** — Control points move independently creating living patterns
- **Gradient Colors** — Smooth color transitions between two random colors
- **Continuous Rotation** — Artwork rotates at a unique speed
- **Rich Color Palettes** — 28 dark backgrounds, 28 foreground colors
- **Seed-Based** — Every composition is unique and reproducible via its seed
- **Save & Share** — Download as PNG with seed in filename
- **Apparel Mode** — Preview artwork on a T-shirt mockup
- **Responsive** — Works on desktop, tablet, and mobile
- **fxhash Compatible** — Ready for fxhash platform with parameter controls
- **Keyboard Shortcuts**:
  - `R` — Regenerate
  - `S` — Save image
  - `T` — Toggle apparel view

## 🎨 Artwork Details

| Parameter | Range | Description |
|-----------|-------|-------------|
| **Number of Control Points** | 3–30 | Points that define the bezier curve |
| **Background Color** | 28 options | Random dark/light color palette |
| **Foreground Colors** | 28 options | Two random colors for gradient |
| **Rotation Speed** | Variable | Random unique rotation speed |
| **Movement Speed** | Variable | Each point moves independently |

## 🚀 Quick Start

### Local Development

```bash
# Clone the repository
git clone https://github.com/reyrove/Bezier-2-Generative-Art.git

# Navigate to the directory
cd Bezier-2-Generative-Art

# Open in browser
open index.html
# or use a live server
```

### Deploy to GitHub Pages

1. Push to GitHub
2. Go to Settings → Pages
3. Select branch `main` and root folder
4. Your site will be live at `https://reyrove.github.io/Bezier-2-Generative-Art`

## 🧠 How It Works

The artwork is generated using a deterministic random number generator, seeded by timestamp + random noise. Every refresh:

1. **Setup**:
   - Chooses a background from 28 colors
   - Selects two random foreground colors for gradient
   - Determines number of control points (3-30)

2. **Point Generation**:
   - Points are placed randomly on a polar grid
   - Each point has a unique movement direction and speed
   - Each point moves within a defined range

3. **Animation**:
   - Points move continuously creating organic flow
   - The entire artwork rotates at a unique speed
   - Smooth gradient transitions between two colors
   - 30 FPS for smooth animation

4. **Rendering**:
   - Smooth closed bezier curve connects all points
   - Gradient color transition along the curve
   - Line width scales with canvas size

## 📁 File Structure

```
Bezier-2-Generative-Art/
├── index.html          # Main application (all-in-one)
├── Bezier-2.jpg        # T-shirt mockup image
├── fav.svg             # Favicon
├── demo-screenshot.jpg # Website demo screenshot
├── README.md           # This file
└── LICENSE             # MIT License
```

## 🛠️ Tech Stack

- **Vanilla HTML/CSS/JS** — No dependencies
- **Canvas API** — 2D rendering
- **CSS Grid & Flexbox** — Responsive layout
- **fxhash SDK** — Generative art platform integration
- **GitHub Pages** — Hosting

## 🎯 Interactive Controls

| Action | Keyboard | Button |
|--------|----------|--------|
| Regenerate | `R` | Click "regenerate" |
| Save Image | `S` | Click "regenerate" |
| Toggle Apparel | `T` | Click "apparel" |

## 🔧 Customization

You can tweak the generation parameters in `index.html`:

- **Point count range**: Modify `numberOfPoints` calculation (line ~310)
- **Background colors**: Edit `backgroundColours` array (line ~195-203)
- **Foreground colors**: Edit `foregroundColours` array (line ~205-212)
- **Movement speed**: Adjust `step` generation (line ~330)
- **Rotation speed**: Modify `Rot` calculation (line ~334)

### fxhash Parameters

The artwork supports fxhash parameters:

```javascript
{
  id: "number_id1",
  name: "Number of Control Points",
  type: "number",
  options: { min: 3, max: 30, step: 1 }
}
```

## 🎨 The Creative Process

### Point Movement
Each control point moves independently in a random direction. When a point reaches its boundary, it reverses direction, creating a flowing, organic motion.

### Gradient Colors
The curve transitions smoothly between two random colors, creating beautiful color harmonies that shift along the curve's path.

### Rotation
The entire artwork rotates at a unique speed, adding an extra dimension of motion and creating mesmerizing visual patterns.

## 📱 Responsive Design

The application automatically adapts to:
- Desktop screens
- Tablets
- Mobile phones
- Landscape orientation
- Various aspect ratios

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Fork the repository
- Create a feature branch
- Submit a pull request

### Ideas for Contributions:
- New movement algorithms
- Additional color palettes
- Enhanced animation effects
- GIF export functionality
- Performance optimizations

## 📄 License

MIT License — see [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Inspired by generative art and bezier curves
- Created with fxhash for the generative art platform
- Special thanks to the creative coding community

---

**Built with ❤️ and flowing motion**