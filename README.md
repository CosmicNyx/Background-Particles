# Background Particles Library

A lightweight, easy-to-use JavaScript library for creating beautiful animated particle backgrounds on your website. Perfect for adding visual flair to landing pages, portfolios, or any web project.

## Features

- **Customizable Colors** - Set up to 5 different particle colors
- **Lightweight** - Minimal code footprint with no dependencies
- **Configurable** - Adjust particle count and animation speed
- **Responsive** - Automatically adapts to container size
- **Easy Setup** - Just add HTML attributes and CSS

## Quick Start

### 1. Include the Library

Add the `particles.js` file to your project and include it in your HTML:

```html
<script src="particles.js"></script>
```

### 2. Create the HTML Structure

Add a container div with the `particle-background` class and configure it with data attributes:

```html
<div class="particle-background" 
     data-color-1="#00d76c" 
     data-color-2="#a8e2ff" 
     data-color-3="#0f1627"
     data-count="60" 
     data-speed="1">
</div>
```

### 3. Add the Required CSS

Style your particle background container:

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
<div class="particle-background" 
     data-color-1="#006994" 
     data-color-2="#00a8cc" 
     data-color-3="#87ceeb"
     data-count="80" 
     data-speed="0.8">
</div>

<!-- Sunset theme -->
<div class="particle-background" 
     data-color-1="#ff6b35" 
     data-color-2="#f7931e" 
     data-color-3="#ffd23f"
     data-count="50" 
     data-speed="1.2">
</div>

<!-- Minimal theme -->
<div class="particle-background" 
     data-color-1="#ffffff" 
     data-color-2="#f0f0f0"
     data-count="30" 
     data-speed="0.5">
</div>
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
    <div class="particle-background" 
         data-color-1="#667eea" 
         data-color-2="#764ba2" 
         data-color-3="#f093fb"
         data-count="75" 
         data-speed="1">
    </div>
    
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
    <div class="particle-background" 
         data-color-1="#ff9a9e" 
         data-color-2="#fecfef" 
         data-color-3="#fecfef"
         data-count="40" 
         data-speed="0.7">
    </div>
    
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

## Advanced Usage

### Multiple Particle Backgrounds

You can have multiple particle backgrounds on the same page:

```html
<div class="particle-background" 
     data-color-1="#ff6b6b" 
     data-color-2="#4ecdc4"
     data-count="30" 
     data-speed="1">
</div>

<div class="particle-background" 
     data-color-1="#45b7d1" 
     data-color-2="#96ceb4" 
     data-color-3="#feca57"
     data-count="45" 
     data-speed="0.5">
</div>
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
