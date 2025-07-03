# Buddy Characters

A simple web application for testing animated buddy characters using Rive animations with dynamic character switching.

## Features

- **Interactive Character Selection**: Switch between three unique buddy characters using a dropdown menu
- **Rive Animation**: Continuous wave gesture animation that works across all characters
- **CDN Asset Loading**: PNG character parts loaded dynamically from GitHub Pages CDN with local fallback
- **Responsive Design**: Clean, centered layout with hover effects

## Characters

1. **Cat Dog Orange** - Orange cat-dog hybrid character
2. **Kitten Ninja** - Gray ninja kitten with red accents
3. **Master Hamster** - Brown hamster with monocle

## Technical Implementation

### Rive Integration
- Uses Rive Web Runtime for animation playback
- Single artboard (`BuddyBase`) shared across all characters
- Referenced PNG assets loaded via custom asset loader
- Wave gesture animation loops continuously

### Character System
- Each character shares the same skeletal rig system
- PNG parts (head, torso, arms, etc.) swap dynamically
- Consistent naming convention across all character assets
- **CDN-First Loading**: Assets served from GitHub Pages CDN with automatic fallback to local assets
- **Performance Monitoring**: Console logs show load times and CDN vs fallback usage

## Getting Started

### Prerequisites
- Modern web browser with JavaScript enabled
- Local web server (Python, Node.js, etc.)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/undeadpickle/buddy.git
cd buddy
```

2. Start a local web server:
```bash
# Serve from public directory
python3 -m http.server 8000 -d public

# Alternative port if 8000 is in use
python3 -m http.server 8001 -d public
```

3. Open your browser and navigate to:
```
http://localhost:8000/
# or http://localhost:8001/ if using alternative port
```

## Project Structure

```
buddy/
├── public/                 # Web application files
│   ├── assets/
│   │   ├── rive/          # Rive animation files
│   │   │   └── humanoid-buddies.riv
│   │   └── characters/    # Character PNG assets (local fallback)
│   │       ├── cat-dog-orange/
│   │       ├── kitten-ninja/
│   │       └── master-hamster/
│   └── index.html         # Main application with CDN integration
├── buddy-assets-cdn/      # CDN repository (GitHub Pages)
│   ├── cat-dog-orange/    # Character assets hosted on CDN
│   ├── kitten-ninja/
│   ├── master-hamster/
│   └── index.html         # CDN directory listing
├── src/                   # Source code (for future development)
├── docs/                  # Documentation and screenshots
├── CLAUDE.md             # AI assistant context
└── README.md             # This file
```

## CDN Configuration

### Asset Hosting
- **CDN URL**: `https://undeadpickle.github.io/buddy-assets-cdn/`
- **Repository**: `https://github.com/undeadpickle/buddy-assets-cdn`
- **Hosting**: GitHub Pages (free, reliable CDN)
- **Fallback**: Automatic fallback to local assets if CDN fails

### Testing CDN Functionality
1. Open browser developer tools (F12)
2. Go to Console tab to monitor asset loading
3. Look for logs showing CDN vs fallback usage:
   - `usedFallback: false` = Assets loaded from CDN
   - `usedFallback: true` = Assets loaded from local fallback
4. Check Network tab to verify assets loading from GitHub Pages

### Performance Monitoring
- Console logs show load times for each asset
- File sizes logged for performance analysis
- CDN vs fallback usage clearly indicated
- Character switch timing tracked

## Development

### Character Assets
- Each character folder contains identical PNG part names
- Standard resolution only (no @2x, @3x variants used)
- Parts include: head, torso, arms, legs, eyes, tail, etc.
- Assets maintained in both CDN and local folders

### Adding New Characters
1. Create a new character folder in `public/assets/characters/` (local fallback)
2. Create matching folder in `buddy-assets-cdn/` repository (CDN)
3. Add PNG files with matching names to existing characters in both locations
4. Update the `characters` and `localCharacters` objects in `index.html`
5. Add new option to the dropdown select
6. Commit and push CDN changes to GitHub

## Browser Support
- Modern browsers that support ES6+ features
- Requires WebGL support for Rive animations

## License
This project is for educational and testing purposes.

## Contributing
This is a simple MVP project. Feel free to fork and experiment with additional features.