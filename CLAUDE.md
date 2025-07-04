# Claude AI Assistant Context

## Project Overview
This is a simple MVP web application for testing buddy characters using Rive animations. The project demonstrates dynamic character switching with referenced PNG assets.

## Key Technical Details

### Rive Integration
- **File**: `public/assets/rive/humanoid-buddies.riv`
- **Artboard**: BuddyBase (default artboard)
- **Animation**: gesture_wave (loops continuously)
- **Asset Loading**: Referenced PNG files loaded dynamically via asset loader API

### Character System
- **Characters**: Cat Dog Orange, Kitten Ninja, Master Hamster
- **Asset Structure**: Each character has identical PNG part names (head.png, torso.png, etc.)
- **Switching**: Reinitializes Rive instance with new character asset paths
- **Bone Rig**: Single skeletal system shared across all characters

### Asset Loading Strategy
- PNG files marked as "Referenced" in Rive editor
- **CDN Hosting**: Assets served from GitHub Pages CDN at `https://undeadpickle.github.io/buddy/public/assets/characters/`
- **Smart Fallback**: Automatically falls back to local assets if CDN fails
- Asset loader handles dynamic PNG loading at runtime with performance tracking
- Standard resolution only (no @2x, @3x loading currently used)

## Development Commands

### Local Development
```bash
# Start local server
python3 -m http.server 8000 -d public

# Access at http://localhost:8000/
# Alternative port if 8000 is in use
python3 -m http.server 8001 -d public
```

### Testing
- Test character switching via dropdown
- Verify wave animation loops for each character
- Check console for asset loading errors and CDN performance
- Monitor fallback behavior if CDN is unavailable
- Verify assets load from CDN (check browser Network tab)

## Important Notes
- Keep implementation minimal and simple
- All characters use same bone rig and animations
- Referenced assets enable dynamic character switching
- Canvas size: 500x500px
- **CDN-First Architecture**: Assets load from external CDN with local fallback
- **Performance Monitoring**: Console logs show load times and CDN vs fallback usage

## File Structure
```
buddy/
├── public/           # Web assets (served via GitHub Pages CDN)
│   ├── assets/
│   │   ├── rive/     # Rive animation files
│   │   └── characters/ # Character PNG assets
│   └── index.html    # Main application with CDN integration
├── src/              # Source code (for future development)
├── docs/             # Documentation and screenshots
└── README.md         # Project documentation
```

## CDN Configuration
- **CDN URL**: `https://undeadpickle.github.io/buddy/public/assets/characters/`
- **Repository**: `https://github.com/undeadpickle/buddy` (main repository)
- **Hosting**: GitHub Pages enabled on main branch
- **Fallback Strategy**: Automatic fallback to local assets if CDN fails
- **Performance Tracking**: Console logs show CDN vs fallback usage and load times