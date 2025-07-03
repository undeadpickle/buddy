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
- Local folders simulate external CDN structure
- Asset loader handles dynamic PNG loading at runtime
- Standard resolution only (no @2x, @3x loading)

## Development Commands

### Local Development
```bash
# Start local server
python3 -m http.server 8000

# Access at http://localhost:8000/public/
```

### Testing
- Test character switching via dropdown
- Verify wave animation loops for each character
- Check console for asset loading errors

## Important Notes
- Keep implementation minimal and simple
- All characters use same bone rig and animations
- Referenced assets enable dynamic character switching
- Canvas size: 500x500px
- Local asset folders act as CDN simulation

## File Structure
```
buddy/
├── public/           # Web assets
│   ├── assets/
│   │   ├── rive/     # Rive animation files
│   │   └── characters/ # Character PNG assets
│   └── index.html    # Main application
├── src/              # Source code (for future development)
├── docs/             # Documentation and screenshots
└── README.md         # Project documentation
```