# Peruchito - Your Life RPG iOS App

<div align="center">
  <h3>🎮 Gamify Your Life with Peruchito</h3>
  <p>A stunning iOS app that turns your daily tasks into an epic RPG adventure</p>
</div>

## 📱 Features

### ✨ Premium Rank Badge System
- **9 Unique Ranks**: From Unranked to Legendary
- **Beautiful Gradients**: Each rank features custom 3-stop color gradients
- **Smooth Animations**: Floating icons, shine effects, and hover transitions
- **Responsive Grid Layout**: Organized display with current rank highlighting

### 💪 Clean Workout Library
- **No Images**: Streamlined, text-focused workout cards
- **Organized by Split**: Push, Pull, and Legs day exercises
- **Numbered Lists**: Easy-to-follow workout progression
- **Muscle Target Badges**: Quick identification of target muscles
- **Pro Tips**: Highlighted tips for proper form and execution

### 🎯 Core Features
- **Daily Tasks**: Track your daily habits and goals
- **Stat System**: Strength, Endurance, Intelligence, Discipline
- **Food Scanner**: Quick calorie logging with extensive food database
- **Weekly Weight Check-in**: Track your fitness progress
- **Mission System**: Daily, weekly, and epic challenges
- **Rewards & Streaks**: Stay motivated with visual progress

## 🚀 Getting Started

### Requirements
- **macOS**: Ventura 13.0 or later
- **Xcode**: 15.0 or later
- **iOS Deployment Target**: 15.0+
- **Swift**: 5.0+

### Installation

1. **Clone or download** this repository
2. **Open** `Peruchito.xcodeproj` in Xcode
3. **Select** your target device or simulator
4. **Press** `Cmd + R` to build and run

### First Launch
The app will load with default settings and an empty state. Start completing tasks to:
- Gain stats and level up
- Unlock new rank badges
- Build your daily streak
- Track your fitness journey

## 🏗️ Project Structure

```
Peruchito/
├── Peruchito.xcodeproj/          # Xcode project file
│   └── project.pbxproj
├── Peruchito/                     # Main app directory
│   ├── PeruchitoApp.swift        # App entry point
│   ├── ContentView.swift         # Main view with WKWebView
│   ├── index.html                # Full app UI (HTML/CSS/JS)
│   ├── Info.plist                # App configuration
│   └── Assets.xcassets/          # App icons and colors
│       ├── AppIcon.appiconset/   # App icon assets
│       ├── AccentColor.colorset/ # Purple theme color
│       └── LaunchScreenBackground.colorset/
```

## 🎨 Customization

### Colors
The app uses a premium purple theme defined in:
- `AccentColor`: #A78BFA (Purple)
- Modify in `Assets.xcassets/AccentColor.colorset/Contents.json`

### App Icon
Replace app icons in `Assets.xcassets/AppIcon.appiconset/`
Required sizes:
- 20x20 @2x, @3x
- 29x29 @2x, @3x
- 40x40 @2x, @3x
- 60x60 @2x, @3x
- 1024x1024 (App Store)

### Bundle Identifier
Change in Xcode project settings or `project.pbxproj`:
```
PRODUCT_BUNDLE_IDENTIFIER = com.peruchito.app;
```

## 🔧 Technical Details

### Architecture
- **SwiftUI**: Modern declarative UI framework
- **WKWebView**: High-performance web content rendering
- **Local Storage**: All data persists in browser localStorage

### iOS Integration
- ✅ Safe area support for notched devices
- ✅ Dark mode optimized
- ✅ Portrait and landscape orientation
- ✅ Smooth scrolling and gestures
- ✅ No tap highlights or text selection
- ✅ Optimized for iOS performance

### HTML Features
- Responsive design with Tailwind CSS
- Font Awesome icons
- Local storage for state persistence
- Real-time countdown timers
- Smooth animations and transitions

## 📦 Building for Production

### Debug Build
```bash
# From command line
xcodebuild -project Peruchito.xcodeproj -scheme Peruchito -configuration Debug
```

### Release Build
```bash
# From command line
xcodebuild -project Peruchito.xcodeproj -scheme Peruchito -configuration Release
```

### App Store Preparation
1. Add app icons (all required sizes)
2. Set up code signing in Xcode
3. Configure your bundle identifier
4. Update version and build numbers
5. Create archive: `Product → Archive`
6. Submit via Xcode Organizer

## 🔒 Privacy & Data

- **All data stored locally** on device
- **No server communication** for core features
- **No analytics or tracking**
- External resources loaded:
  - Tailwind CSS CDN
  - Font Awesome CDN
  - Google Fonts

## 🐛 Known Issues & Limitations

- App icons not included (needs custom icons for each size)
- No data sync between devices
- Requires internet for CDN resources (Tailwind, Font Awesome)

## 📝 License

This project is created for personal use and development purposes.

## 🤝 Contributing

This is a personal project, but feedback and suggestions are welcome!

---

<div align="center">
  <p>Built with ❤️ using SwiftUI and modern web technologies</p>
  <p>🤖 Enhanced with Claude Code</p>
</div>
