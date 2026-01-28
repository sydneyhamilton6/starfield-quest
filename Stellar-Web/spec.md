# Stellar-Web Specification

## Overview
An interactive particle system visualization featuring connected nodes with customizable parameters, real-time network statistics, and mouse-based interaction.

## Features

### Particle System
- **Node Shapes**: Three distinct shapes rendered randomly per particle
  - Four-pointed sparkles (tall, asymmetric)
  - Circles
  - Five-pointed stars
- **Z-Depth Effect**: Particles vary in size and opacity based on simulated depth position
  - Closer particles (high z) appear larger and brighter
  - Distant particles (low z) appear smaller and faded
- **Edge Connections**: Lines drawn between particles within connectivity radius
  - Opacity fades with distance
  - Thickness and opacity scale with average depth of connected particles

### Controls Panel
| Control | Range | Default | Description |
|---------|-------|---------|-------------|
| Node Speed | 0.1 - 5 | 2 | Movement speed multiplier |
| Connectivity Radius | 50 - 300px | 150 | Max distance for edge connections |
| Node Count | 10 - 200 | 80 | Number of particles |
| Node Size | 1 - 10px | 3 | Base particle size |
| Edge Thickness | 0.5 - 4px | 1 | Connection line width |
| Mouse Mode | Attract/Repel | Attract | Cursor interaction behavior |

### Network Statistics Panel
- **Total Edges**: Current number of connections between particles
- **Avg Connections**: Mean edges per node (2 * edges / nodes)
- **Network Density**: Percentage of possible connections realized (edges / max possible edges)

### Mouse Interaction
- **Attract Mode**: Particles within 150px radius are pulled toward cursor
- **Repel Mode**: Particles within 150px radius are pushed away from cursor
- Velocity dampening prevents runaway speeds (max speed: 4)

## Technical Details

### Canvas Rendering
- Full-window responsive canvas
- Motion blur effect via semi-transparent background fill (alpha: 0.2)
- 60fps animation loop using requestAnimationFrame

### Particle Physics
- Random initial position and velocity
- Bounce off screen edges
- Z-position oscillates between 0 and 1
- Depth scaling: size and opacity range from 40-100% based on z

### UI Components
- Collapsible panels with smooth CSS transitions
- Stacked panel layout on left side of screen
- Dark theme with blue accent colors (#5a8cff, #8ab4ff)

## Browser Compatibility
- Modern browsers with ES6+ support
- Canvas 2D rendering context required

## File Structure
```
Stellar-Web/
└── index.html    # Single-file application (HTML + CSS + JS)
```
