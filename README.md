# 🚀 Coin Catcher — Premium Arcade Survival Game

[![GitHub license](https://img.shields.io/github/license/jenanielangovan/coin-catcher?style=for-the-badge&color=blue)](LICENSE)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

A visually stunning, high-performance, **completely self-contained** HTML5 arcade survival experience built with raw HTML, CSS, JavaScript, and Canvas. Featuring a theatrical scroll-driven opening presentation, responsive glassmorphic HUDs, custom particle systems, and polished gameplay mechanics.

> 🌟 **Perfect for showcasing:** Vanilla JS expertise, advanced HTML5 Canvas animations, responsive browser event mapping, and high-quality UX design principles in portfolio/resumes.

---

## 🎮 Live Demo

*Coming soon / Host on GitHub Pages (e.g., `https://jenanielangovan.github.io/coin-catcher/Game%20Sample.html`)*

---

## 🎨 Design & Visual Features

- **Theatrical Scroll-Driven Intro**: A responsive, perspective-warped vertical scrolling layout presenting key game features (using CSS scroll-snapping, math-driven viewport interpolation, 3D CSS transforms, scaling, and dynamic filters).
- **Glassmorphic HUD Layer**: Modern visual UI overlay displaying real-time scores, high score (persisted in `localStorage`), and player health utilizing CSS backdrop-filter blur and vibrant neon glow drop-shadows.
- **Dynamic HTML5 Canvas Renderer**:
  - **Starfield Background**: Layered, parallex-scrolling background stars.
  - **Custom Geometry Drawing**: Custom math-drawn 5-pointed stars (Shield power-ups) and Bezier-curve hearts.
  - **Dynamic Particles**: High-fidelity decay particles emitting from collection and collision points.
  - **Interactive Screen Shake**: Impact feedback utilizing translation offset matrix manipulation.
  - **Glow Effects**: Radial canvas gradients and drop-shadow styling.

---

## 🕹️ Gameplay Mechanics

- **Interactive Elements**:
  - ⭐ **Gold Coins**: Standard items (+10 points) with golden rotating glow.
  - 🔮 **Rare Gems**: High-value items (+30 points) with pulsing magenta scale.
  - 🛡️ **Shield Matrix**: Multi-second invincibility power-up rendering a custom defensive color profile.
  - ❤️ **Hearts**: Replenishes HP back to the maximum of 3 integrity charges.
  - 🧱 **Red Debris**: Obstacles that drain health integrity unless protected by a shield.
- **Scaling Difficulty Matrix**: Choose between **Easy**, **Medium**, and **Hard** modes which scale spawning rate, gravity pull, and velocity acceleration dynamically.
- **Adaptive Input Handlers**: Play seamlessly using **Keyboard** (Arrow keys, A/D, ESC/P to Pause) or **Direct Pointer/Touch Dragging** (mapped precisely to scale regardless of device layout aspect ratio).

---

## 🛠️ Technology Stack & Architecture

- **Core**: Vanilla ECMAScript 6, CSS3 Custom Properties, Semantic HTML5.
- **Graphics & Animation Engine**: HTML5 2D Canvas Context (`requestAnimationFrame` game loop, collision detection system).
- **Persistence**: Web Storage API (`localStorage`) for high-score retention.
- **Typography**: Google Fonts (`Outfit`).

---

## 📁 Repository Structure

```bash
coin-catcher/
├── Game Sample.html    # The self-contained, fully styled game & engine
├── .gitignore          # System & local configuration ignore files
└── README.md           # This project overview and documentation
```

---

## 🚀 How to Run Locally

Since the game is built purely with vanilla web technology, it requires **zero installations or build servers**:

1. Clone this repository:
   ```bash
   git clone https://github.com/jenanielangovan/coin-catcher.git
   ```
2. Open the directory:
   ```bash
   cd coin-catcher
   ```
3. Open `Game Sample.html` directly in any modern web browser, or launch it with a local server (e.g., Live Server in VS Code).

---

## 🎓 Technical Highlights (Resume Worthy)

### 1. Unified Responsive Mouse & Touch Position Mapping
Translates mouse client coordinates accurately into canvas coordinate space, regardless of the browser's CSS scaling or high-DPI display resolutions.
```javascript
function handlePointerMove(clientX) {
    if (!isGameRunning || isGameOver || isPaused) return;
    const rect = canvas.getBoundingClientRect();
    const relativeX = clientX - rect.left;
    const scaleX = relativeX / rect.width;
    player.x = scaleX * canvas.width - player.width / 2;
    keepPlayerInBounds();
}
```

### 2. Math-Driven Intro Screen Transitions
Calculates real-time scrolling distance relative to viewport heights to apply smooth opacity, transform, and blur offsets to elements as the player scrolls.
```javascript
introPage.addEventListener("scroll", () => {
    const scrollTop = introPage.scrollTop;
    const viewportHeight = window.innerHeight;

    introSections.forEach((section, index) => {
        const sectionTop = index * viewportHeight;
        const ratio = (scrollTop - sectionTop) / viewportHeight;
        const absRatio = Math.abs(ratio);

        const content = section.querySelector(".section-content");
        content.style.opacity = Math.max(0, 1 - absRatio * 1.6);
        content.style.transform = `translateY(${ratio * -100}px) scale(${1 - absRatio * 0.18})`;
        content.style.filter = `blur(${absRatio * 12}px)`;
    });
});
```

---

## 💡 Future Enhancements Roadmap

- [ ] Add sound effects and ambient synthwave background music using the Web Audio API.
- [ ] Connect to a Firebase/Node.js backend to display a real-time global leaderboard.
- [ ] Implement local-coop or multiplayer features using WebRTC.

---

## ☕ Support This Project
If you found this vanilla JS physics template helpful for your portfolio, consider supporting my work!

[![Buy Me A Coffee](https://shields.io)](https://buymeacoffee.com)
[![GitHub Sponsors](https://shields.io)](https://github.com)

---

Designed and developed with ❤️ by [Jenani Elangovan](https://github.com/jenanielangovan).
