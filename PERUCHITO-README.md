# Level Up Idea - Peruchito Life RPG 🎮

<div align="center">
  <h3>🚀 Transform Your Life Into An Epic RPG Adventure</h3>
  <p>Complete iOS app for gamifying your daily tasks, workouts, and habits</p>
</div>

---

## 🎯 What is Peruchito?

**Peruchito** (formerly SENSE) is a life gamification app that turns your daily habits into an RPG experience. Track tasks, gain stats, level up through ranks, and become the legendary version of yourself!

## ✨ Key Features

### 🏆 Premium Rank System
- **9 Unique Ranks**: Unranked → Bronze → Silver → Gold → Platinum → Diamond → Master → Grandmaster → Legendary
- **Beautiful Gradient Badges**: Each rank features custom 3-stop color gradients
- **Smooth Animations**: Floating icons, shine effects, and responsive grid layout
- **Progress Tracking**: Visual progress bars showing your journey to the next rank

### 💪 Workout Library
- **Clean, Text-Focused Design**: No distracting images
- **3-Day Split**: Push, Pull, and Legs workouts
- **Numbered Exercise Lists**: Easy-to-follow progression
- **Muscle Target Badges**: Quick identification of target muscles
- **Pro Tips**: Highlighted tips for proper form and execution

### 📊 RPG Stats System
- **Strength**: Gain through workouts and lifting
- **Endurance**: Build through consistency
- **Intelligence**: Grow via learning and content consumption
- **Discipline**: Increase with all completed tasks

### 🍔 Food Scanner
- **33+ Popular Foods**: Fast food, snacks, healthy options
- **Quick Calorie Logging**: One-tap to add meals
- **Daily Tracking**: Automatic calorie total updates
- **Food History**: Review your eating patterns

### 📅 Daily Missions
- Morning workout
- Healthy eating
- Learning sessions
- Bible study
- Skin care routine
- And more!

### 🎁 Rewards & Streaks
- **Daily Streak Tracking**: Build momentum
- **Mission Rewards**: Unlock achievements
- **Weekly Weight Check-in**: Track fitness progress
- **Visual Progress**: See your stats grow

---

## 📱 iOS App - Production Ready

### Quick Start

1. **Requirements:**
   - macOS Ventura 13.0+
   - Xcode 15.0+
   - iOS 15.0+ device or simulator

2. **Open & Run:**
   ```bash
   open Peruchito.xcodeproj
   ```
   - Select your target device
   - Press `Cmd + R` to build and run

3. **Start Using:**
   - Complete daily tasks to gain stats
   - Track workouts in the library
   - Scan/log food for calorie tracking
   - Watch your rank increase!

### Project Structure

```
level-up-idea/
├── README.md                      # This file
├── SENSE-ULTIMATE.html           # Original HTML (standalone version)
├── Peruchito.xcodeproj/          # Xcode project - OPEN THIS
│   └── project.pbxproj
└── Peruchito/                     # App source files
    ├── PeruchitoApp.swift        # SwiftUI app entry
    ├── ContentView.swift         # WKWebView integration
    ├── index.html                # Optimized HTML for iOS
    ├── Info.plist                # App configuration
    ├── README.md                 # Detailed iOS setup guide
    └── Assets.xcassets/          # App icons & colors
        ├── AppIcon.appiconset/
        ├── AccentColor.colorset/
        └── LaunchScreenBackground.colorset/
```

---

## 🎨 Design Philosophy

### Premium Aesthetics
- **Dark Theme**: Black background with purple accents (#A78BFA)
- **Glass Morphism**: Translucent cards with blur effects
- **Smooth Animations**: Cubic-bezier transitions throughout
- **Gradient Effects**: Every rank badge and progress bar

### iOS Native Feel
- **Safe Area Support**: Perfect on all iPhone models (notch included)
- **No User Scaling**: Locked for native app consistency
- **Tap Optimization**: Disabled text selection and highlights
- **Dark Mode**: Optimized for OLED displays

---

## 🚀 Use Cases

### For Individuals
- **Fitness Tracking**: Log workouts, track weight, count calories
- **Habit Building**: Daily task completion with streak tracking
- **Personal Growth**: Gain "Intelligence" through learning
- **Discipline**: Build consistency across all areas of life

### Gamification Benefits
- **Motivation**: See tangible progress through ranks and stats
- **Competition**: Compare ranks with friends (future feature)
- **Achievement**: Unlock badges and reach legendary status
- **Visual Feedback**: Immediate satisfaction from completed tasks

---

## 🔧 Technical Stack

### iOS App
- **Language**: Swift 5.0
- **Framework**: SwiftUI
- **Web Engine**: WKWebView
- **Storage**: Local Storage (browser-based persistence)
- **Deployment**: iOS 15.0+

### Web Technologies
- **HTML5**: Semantic markup
- **CSS3**: Custom animations, gradients, glass effects
- **JavaScript**: Vanilla JS for state management
- **Tailwind CSS**: Utility-first styling (CDN)
- **Font Awesome**: Icon library (CDN)

---

## 📖 Detailed Documentation

See **[Peruchito/README.md](Peruchito/README.md)** for:
- Complete iOS setup instructions
- Customization guide (colors, bundle ID, icons)
- App Store submission checklist
- Technical architecture details
- Build configurations

---

## 🎯 Roadmap

### Planned Features
- [ ] App icons for all sizes
- [ ] iCloud sync across devices
- [ ] Widget support (iOS 16+)
- [ ] Apple Watch companion app
- [ ] Social features (compare ranks)
- [ ] Custom task creation
- [ ] Advanced analytics
- [ ] Dark/light theme toggle
- [ ] Offline mode improvements

### Future Enhancements
- [ ] Android version
- [ ] Web app (PWA)
- [ ] Desktop app (Electron)
- [ ] Backend API for cloud sync
- [ ] Team/family accounts
- [ ] AI-powered suggestions

---

## 🤝 Contributing

This is a personal project, but feedback and suggestions are welcome!

**Ideas?** Open an issue or submit a pull request.

---

## 📄 License

This project is for personal use and development purposes.

---

## 🙏 Acknowledgments

- Design inspired by modern fitness and habit tracking apps
- Gamification concepts from RPG game mechanics
- Built with passion for personal growth and self-improvement

---

<div align="center">
  <h3>🌟 Start Your Journey Today</h3>
  <p>From Unranked to Legendary - Your transformation begins now!</p>
  <br>
  <p>Built with ❤️ using SwiftUI and modern web technologies</p>
  <p>🤖 Enhanced with <a href="https://claude.com/claude-code">Claude Code</a></p>
</div>
