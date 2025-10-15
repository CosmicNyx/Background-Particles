# Background Particles Library

A lightweight, easy-to-use JavaScript library for creating beautiful animated particle backgrounds on your website. Perfect for adding visual flair to landing pages, portfolios, or any web project.

## Table of Contents

- [Features](#features)
- [Quick Start](#quick-start)
  - [1. Include the Library](#1-include-the-library)
  - [2. Create the HTML Structure](#2-create-the-html-structure)
  - [3. CSS is Already Included!](#3-css-is-already-included)
- [Configuration Options](#configuration-options)
  - [Data Attributes](#data-attributes)
  - [Color Examples](#color-examples)
- [Usage Examples](#usage-examples)
  - [Full Page Background](#full-page-background)
  - [Section Background](#section-background)
- [How It Works: JavaScript Code Explained](#how-it-works-javascript-code-explained)
  - [Class Structure](#class-structure)
  - [Key Methods Breakdown](#key-methods-breakdown)
- [Advanced Usage](#advanced-usage)
  - [Multiple Particle Backgrounds](#multiple-particle-backgrounds)
  - [Programmatic Initialization](#programmatic-initialization)
- [Browser Support](#browser-support)
- [Tips & Best Practices](#tips--best-practices)
- [License](#license)
- [Contributing](#contributing)

## Features

- **Customizable Colors** - Set up to 5 different particle colors
- **Lightweight** - Minimal code footprint with no dependencies
- **Configurable** - Adjust particle count and animation speed
- **Responsive** - Automatically adapts to container size
- **Easy Setup** - Just add HTML attributes and CSS

## Quick Start

### 1. Include the Library

Add both the `particles.js` and `particles.css` files to your project and include them in your HTML:

```html
<link rel="stylesheet" href="particles.css">
<script src="particles.js"></script>
```

**⚠️ IMPORTANT: The CSS file is REQUIRED!** Without it, the particles won't display correctly.

### 2. Create the HTML Structure

Add a container div with the `particle-background` class and configure it with data attributes:

```html
<div class="particle-background" data-color-1="#00d76c" data-color-2="#a8e2ff" data-color-3="#0f1627" data-count="60" data-speed="1"></div>
```

**Format Comparison:**
```html
<!-- One-liner (recommended) -->
<div class="particle-background" data-color-1="#00d76c" data-color-2="#a8e2ff" data-color-3="#0f1627" data-count="60" data-speed="1"></div>

<!-- Multi-line (also works) -->
<div class="particle-background" 
     data-color-1="#00d76c" 
     data-color-2="#a8e2ff" 
     data-color-3="#0f1627"
     data-count="60" 
     data-speed="1">
</div>
```

*Personal preference: I like the one-liner format because it looks more attached to the main container and takes up less space in the code.*

### 3. CSS is Already Included!

The required CSS is already included in the `particles.css` file you linked in step 1. However, if you prefer to copy-paste the CSS into your own stylesheet, here's what the CSS contains:

```css
.particle-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;  /* ⚠️ CRITICAL: Keeps particles behind content */
  pointer-events: none;
  overflow: hidden;
}

.particle-background canvas {
  display: block;
  width: 100%;
  height: 100%;
}

/* ⚠️ IMPORTANT: Your content MUST have higher z-index than particles */
.your-content {
  position: relative;
  z-index: 1;  /* Higher than -1, so content appears above particles */
}
```

**⚠️ Z-Index Warning**: The z-index is crucial! Without proper z-index values:
- Particles will appear on top of your content
- Text and buttons will be unclickable
- Your website will be unusable

That's it! Your particle background will automatically initialize when the page loads.

## Configuration Options

### Data Attributes

| Attribute | Description | Default | Example |
|-----------|-------------|---------|---------|
| `data-color-1` | First particle color | `#00d76c` | `#ff0000` |
| `data-color-2` | Second particle color | `#a8e2ff` | `#00ff00` |
| `data-color-3` | Third particle color | `#ffffff` | `#0000ff` |
| `data-color-4` | Fourth particle color | - | `#ffff00` |
| `data-color-5` | Fifth particle color | - | `#ff00ff` |
| `data-count` | Number of particles | `60` | `100` |
| `data-speed` | Animation speed multiplier | `1` | `2.5` |

### Color Examples

```html
<!-- Ocean theme -->
<div class="particle-background" data-color-1="#006994" data-color-2="#00a8cc" data-color-3="#87ceeb" data-count="80" data-speed="0.8"></div>

<!-- Sunset theme -->
<div class="particle-background" data-color-1="#ff6b35" data-color-2="#f7931e" data-color-3="#ffd23f" data-count="50" data-speed="1.2"></div>

<!-- Minimal theme -->
<div class="particle-background" data-color-1="#ffffff" data-color-2="#f0f0f0" data-count="30" data-speed="0.5"></div>
```

## Usage Examples

### Full Page Background

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
        }
        
        .particle-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
            overflow: hidden;
        }
        
        .content {
            position: relative;
            z-index: 1;
            padding: 50px;
            text-align: center;
            color: white;
        }
    </style>
</head>
<body>
    <div class="particle-background" data-color-1="#667eea" data-color-2="#764ba2" data-color-3="#f093fb" data-count="75" data-speed="1"></div>
    
    <div class="content">
        <h1>Welcome to My Website</h1>
        <p>Beautiful particles dancing in the background!</p>
    </div>
    
    <script src="particles.js"></script>
</body>
</html>
```

### Section Background

```html
<section class="hero-section">
    <div class="particle-background" data-color-1="#ff9a9e" data-color-2="#fecfef" data-color-3="#fecfef" data-count="40" data-speed="0.7"></div>
    
    <div class="hero-content">
        <h2>Hero Section</h2>
        <p>Content with particle background</p>
    </div>
</section>

<style>
.hero-section {
    position: relative;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
}

.particle-background {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    pointer-events: none;
    overflow: hidden;
}

.hero-content {
    position: relative;
    z-index: 1;
    text-align: center;
    color: white;
}
</style>
```


## How It Works: JavaScript Code Explained

The library uses a simple but effective approach to create smooth particle animations. Here's how the code works:

### Class Structure

The `ParticleBackground` class handles everything:

```javascript
export class ParticleBackground {
    constructor(element) {
        this.container = element;
        this.colors = this.getColorsFromAttributes();
        this.particleCount = parseInt(element.dataset.count) || 60;
        this.animationSpeed = parseFloat(element.dataset.speed) || 1;
        this.init();
    }
}
```

### Key Methods Breakdown

#### 1. **Color Configuration** (`getColorsFromAttributes`)
```javascript
getColorsFromAttributes() {
    const colors = [];
    // Checks for data-color-1, data-color-2, etc.
    for (let i = 1; i <= 5; i++) {
        const color = this.container.dataset[`color${i}`] || 
                     this.container.dataset[`color-${i}`];
        if (color) colors.push(color);
    }
    // Fallback to default colors
    return colors.length > 0 ? colors : ['#00d76c', '#a8e2ff', '#ffffff'];
}
```
- Reads up to 5 color attributes from your HTML
- Supports both `data-color-1` and `data-color1` formats
- Falls back to default colors if none specified

#### 2. **Canvas Setup** (`init`)
```javascript
init() {
    this.canvas = document.createElement('canvas');
    this.container.appendChild(this.canvas);
    this.ctx = this.canvas.getContext('2d');
    
    this.resize();
    window.addEventListener('resize', this.resize.bind(this));
    
    // Create particle array
    this.particles = [];
    for (let i = 0; i < this.particleCount; i++) {
        this.particles.push(this.createParticle());
    }
    
    this.animate();
}
```
- Creates a canvas element and adds it to your container
- Sets up responsive resizing
- Creates the initial particle array
- Starts the animation loop

#### 3. **Particle Creation** (`createParticle`)
```javascript
createParticle() {
    return {
        x: Math.random() * this.width,           // Random X position
        y: Math.random() * this.height,          // Random Y position
        size: Math.random() * 3 + 1,             // Size between 1-4px
        color: this.colors[Math.floor(Math.random() * this.colors.length)],
        speed: Math.random() * this.animationSpeed + 0.2,  // Speed variation
        direction: Math.random() * Math.PI * 2   // Random direction (0-360°)
    };
}
```
Each particle has:
- **Position**: Random starting coordinates
- **Size**: Random size between 1-4 pixels
- **Color**: Randomly selected from your color array
- **Speed**: Base speed + random variation
- **Direction**: Random angle in radians

#### 4. **Animation Loop** (`animate`)
```javascript
animate() {
    this.ctx.clearRect(0, 0, this.width, this.height);
    
    this.particles.forEach(particle => {
        // Move particle based on direction and speed
        particle.x += Math.cos(particle.direction) * particle.speed;
        particle.y += Math.sin(particle.direction) * particle.speed;
        
        // Bounce off edges
        if (particle.x < 0 || particle.x > this.width) {
            particle.direction = Math.PI - particle.direction;
        }
        if (particle.y < 0 || particle.y > this.height) {
            particle.direction = -particle.direction;
        }
        
        // Draw the particle
        this.ctx.fillStyle = particle.color;
        this.ctx.beginPath();
        this.ctx.arc(particle.x, particle.y, particle.size, 0, Math.PI * 2);
        this.ctx.fill();
    });
    
    requestAnimationFrame(this.animate.bind(this));
}
```

**Animation Process:**
1. **Clear canvas** - Wipes the previous frame
2. **Update positions** - Moves each particle using trigonometry
3. **Edge collision** - Bounces particles off container edges
4. **Draw particles** - Renders each particle as a colored circle
5. **Repeat** - Uses `requestAnimationFrame` for smooth 60fps animation

#### 5. **Responsive Resizing** (`resize`)
```javascript
resize() {
    this.width = this.canvas.width = this.container.offsetWidth;
    this.height = this.canvas.height = this.container.offsetHeight;
}
```
- Automatically adjusts canvas size when window resizes
- Ensures particles stay within container bounds

### Auto-Initialization

```javascript
document.addEventListener('DOMContentLoaded', () => {
    document.querySelectorAll('.particle-background').forEach(el => {
        new ParticleBackground(el);
    });
});
```
- Automatically finds all elements with `.particle-background` class
- Creates a new `ParticleBackground` instance for each one
- Runs when the DOM is fully loaded

### Performance Features

- **Canvas-based rendering** - Much faster than DOM manipulation
- **Efficient collision detection** - Simple edge bouncing
- **RequestAnimationFrame** - Smooth, browser-optimized animation
- **Minimal memory usage** - Only stores essential particle data

## Advanced Usage

### Multiple Particle Backgrounds

You can have multiple particle backgrounds on the same page:

```html
<div class="particle-background" data-color-1="#ff6b6b" data-color-2="#4ecdc4" data-count="30" data-speed="1"></div>

<div class="particle-background" data-color-1="#45b7d1" data-color-2="#96ceb4" data-color-3="#feca57" data-count="45" data-speed="0.5"></div>
```

### Programmatic Initialization

If you need more control, you can initialize particles programmatically:

```javascript
// Wait for DOM to be ready
document.addEventListener('DOMContentLoaded', () => {
    const container = document.getElementById('my-particles');
    const particles = new ParticleBackground(container);
});
```

## Browser Support

- Chrome 60+
- Firefox 55+
- Safari 12+
- Edge 79+

## Tips & Best Practices

1. **⚠️ Z-Index is Critical**: 
   - Particles: `z-index: -1` (behind everything)
   - Content: `z-index: 1` or higher (above particles)
   - Without this, particles will cover your content and make it unusable!

2. **Performance**: Use fewer particles (20-50) on mobile devices
3. **Colors**: Choose colors that complement your design
4. **Speed**: Lower speeds (0.5-1) work better for subtle effects
5. **Container**: Make sure the particle container has a defined size
6. **Pointer Events**: Always use `pointer-events: none` on particle containers

## License

This project is open source and available under the [MIT License](LICENSE).

## Contributing

Feel free to submit issues and enhancement requests!
