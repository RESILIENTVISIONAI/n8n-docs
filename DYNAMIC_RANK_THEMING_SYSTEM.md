# Dynamic Rank-Based Theming System
# Peruchito App - Progressive Color Evolution

**Version:** 1.0
**Date:** October 31, 2025
**Feature Type:** Visual Progression System

---

## Overview

The app's color scheme **dynamically changes** based on your current rank. As you level up from Unranked to Legendary, your entire interface transforms with your rank's signature colors, creating a powerful sense of progression and achievement.

---

## Color Schemes by Rank

### 🎨 Rank Color Palettes

```
┌──────────────┬─────────────────┬──────────────────┬─────────────────┐
│    Rank      │  Primary (BG)   │  Secondary (UI)  │   Accent        │
├──────────────┼─────────────────┼──────────────────┼─────────────────┤
│  Unranked    │  #000000 Black  │  #6B7280 Gray    │  #9CA3AF       │
│  Bronze      │  #000000 Black  │  #92400E Brown   │  #F59E0B       │
│  Silver      │  #000000 Black  │  #6B7280 Gray    │  #E5E7EB       │
│  Gold        │  #000000 Black  │  #CA8A04 DkGold  │  #FACC15       │
│  Platinum    │  #000000 Black  │  #0891B2 Cyan    │  #06B6D4       │
│  Diamond     │  #000000 Black  │  #1E40AF DkBlue  │  #3B82F6       │
│  Master      │  #000000 Black  │  #7C3AED Purple  │  #A78BFA       │
│  Grandmaster │  #000000 Black  │  #EA580C Orange  │  #FB923C       │
│  Legendary   │  #000000 Black  │  #DC2626 Red     │  #EF4444       │
└──────────────┴─────────────────┴──────────────────┴─────────────────┘
```

---

## What Changes Color

### UI Elements That Transform:

1. **✅ Progress Bars**
   - All stat bars (STR, END, INT, DIS)
   - Rank progress bar
   - Task completion indicators
   - Timer bars

2. **✅ Buttons**
   - Primary action buttons
   - Task completion buttons
   - Tab navigation active states
   - Food scanner add buttons

3. **✅ Accents & Highlights**
   - Border colors on glass panels
   - Glow effects
   - Active tab indicators
   - Streak badge backgrounds

4. **✅ Icons & Badges**
   - Mission badge colors
   - Current rank badge glow
   - Completed task checkmarks
   - Urgency indicators

5. **✅ Gradients**
   - Button gradients
   - Progress bar fills
   - Card hover effects
   - Loading screens

### What Stays Black:
- ❌ Background (always #000000)
- ❌ Main text (always white/cream)
- ❌ Glass panel bases
- ❌ Other rank badges (they keep their own colors)

---

## Visual Examples

### Unranked (Gray Theme)
```
┌─────────────────────────────────────────────────┐
│  🏠 Peruchito                                   │
│                                                 │
│  ⚪ Unranked  |  0 Stats                       │
│  ├────────────────────────────────────────┤    │
│  │▓▓▓░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░│ 5% │ ← Gray
│                                                 │
│  ⏰ Time Until Midnight: 12:45:30               │
│                                                 │
│  📋 Daily Tasks                                 │
│  ┌────────────────────────────────────┐        │
│  │ ✓ Morning Workout    [COMPLETE] ──────Gray  │
│  └────────────────────────────────────┘        │
└─────────────────────────────────────────────────┘
```

### Bronze (Brown/Amber Theme)
```
┌─────────────────────────────────────────────────┐
│  🏠 Peruchito                                   │
│                                                 │
│  🥉 Bronze  |  75 Stats                        │
│  ├────────────────────────────────────────┤    │
│  │▓▓▓▓▓▓▓▓▓▓░░░░░░░░░░░░░░░░░░░░░░░░░░░░│ 25% │ ← Bronze
│                                                 │
│  ⏰ Time Until Midnight: 08:23:15               │
│                                                 │
│  📋 Daily Tasks                                 │
│  ┌────────────────────────────────────┐        │
│  │ ✓ Morning Workout    [COMPLETE] ──────Bronze│
│  └────────────────────────────────────┘        │
└─────────────────────────────────────────────────┘
```

### Diamond (Blue Theme)
```
┌─────────────────────────────────────────────────┐
│  🏠 Peruchito                                   │
│                                                 │
│  💠 Diamond  |  975 Stats                      │
│  ├────────────────────────────────────────┤    │
│  │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓░░░░░░░░░░░░░░░│ 58% │ ← Blue
│                                                 │
│  ⏰ Time Until Midnight: 04:12:08               │
│                                                 │
│  📋 Daily Tasks                                 │
│  ┌────────────────────────────────────┐        │
│  │ ✓ Morning Workout    [COMPLETE] ───────Blue │
│  └────────────────────────────────────┘        │
└─────────────────────────────────────────────────┘
```

### Legendary (Red Theme) 🔥
```
┌─────────────────────────────────────────────────┐
│  🏠 Peruchito                                   │
│                                                 │
│  🔥 LEGENDARY  |  3847 Stats                   │
│  ├────────────────────────────────────────┤    │
│  │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│ MAX │ ← Red
│                                                 │
│  ⏰ Time Until Midnight: 16:42:55               │
│                                                 │
│  📋 Daily Tasks                                 │
│  ┌────────────────────────────────────┐        │
│  │ ✓ Morning Workout    [COMPLETE] ────────Red │
│  └────────────────────────────────────┘        │
└─────────────────────────────────────────────────┘
```

---

## Implementation Architecture

```
┌─────────────────────────────────────────────────┐
│           Swift App (Native Layer)              │
│  ┌───────────────────────────────────────────┐ │
│  │  RankThemeManager                         │ │
│  │  - Monitors current rank                  │ │
│  │  - Calculates theme colors                │ │
│  │  - Injects CSS variables to WebView      │ │
│  └───────────────┬───────────────────────────┘ │
│                  │                               │
│                  ▼                               │
│  ┌───────────────────────────────────────────┐ │
│  │  WKWebView                                │ │
│  │  ┌─────────────────────────────────────┐ │ │
│  │  │  HTML/CSS/JS Layer                  │ │ │
│  │  │  - Receives theme via JavaScript    │ │ │
│  │  │  - Updates CSS variables            │ │ │
│  │  │  - Re-renders UI with new colors   │ │ │
│  │  └─────────────────────────────────────┘ │ │
│  └───────────────────────────────────────────┘ │
└─────────────────────────────────────────────────┘
```

---

## Swift Implementation

### 1. Rank Theme Manager

```swift
//
//  RankThemeManager.swift
//  Peruchito
//
//  Manages dynamic theming based on current rank
//

import Foundation
import UIKit

struct RankTheme {
    let name: String
    let secondary: String      // Secondary UI color (darker)
    let accent: String          // Accent color (brighter)
    let gradient: [String]      // Gradient stops
}

class RankThemeManager: ObservableObject {
    static let shared = RankThemeManager()

    @Published var currentTheme: RankTheme

    // All rank themes
    private let themes: [String: RankTheme] = [
        "Unranked": RankTheme(
            name: "Unranked",
            secondary: "#6B7280",
            accent: "#9CA3AF",
            gradient: ["#6B7280", "#9CA3AF", "#D1D5DB"]
        ),
        "Bronze": RankTheme(
            name: "Bronze",
            secondary: "#92400E",
            accent: "#F59E0B",
            gradient: ["#92400E", "#F59E0B", "#FCD34D"]
        ),
        "Silver": RankTheme(
            name: "Silver",
            secondary: "#6B7280",
            accent: "#E5E7EB",
            gradient: ["#9CA3AF", "#D1D5DB", "#F3F4F6"]
        ),
        "Gold": RankTheme(
            name: "Gold",
            secondary: "#CA8A04",
            accent: "#FACC15",
            gradient: ["#CA8A04", "#FACC15", "#FEF08A"]
        ),
        "Platinum": RankTheme(
            name: "Platinum",
            secondary: "#0891B2",
            accent: "#06B6D4",
            gradient: ["#0891B2", "#06B6D4", "#A5F3FC"]
        ),
        "Diamond": RankTheme(
            name: "Diamond",
            secondary: "#1E40AF",
            accent: "#3B82F6",
            gradient: ["#1E40AF", "#3B82F6", "#93C5FD"]
        ),
        "Master": RankTheme(
            name: "Master",
            secondary: "#7C3AED",
            accent: "#A78BFA",
            gradient: ["#7C3AED", "#A78BFA", "#DDD6FE"]
        ),
        "Grandmaster": RankTheme(
            name: "Grandmaster",
            secondary: "#EA580C",
            accent: "#FB923C",
            gradient: ["#EA580C", "#FB923C", "#FED7AA"]
        ),
        "Legendary": RankTheme(
            name: "Legendary",
            secondary: "#DC2626",
            accent: "#EF4444",
            gradient: ["#DC2626", "#EF4444", "#F87171", "#FCA5A5", "#FECACA"]
        )
    ]

    init() {
        // Start with default (Master/Purple)
        self.currentTheme = themes["Master"]!
    }

    /// Update theme based on rank name
    func updateTheme(forRank rankName: String) {
        if let theme = themes[rankName] {
            self.currentTheme = theme
        }
    }

    /// Get JavaScript code to inject into WebView
    func getThemeInjectionScript() -> String {
        return """
        (function() {
            const theme = {
                secondary: '\(currentTheme.secondary)',
                accent: '\(currentTheme.accent)',
                gradient: [\(currentTheme.gradient.map { "'\($0)'" }.joined(separator: ", "))]
            };

            // Update CSS variables
            document.documentElement.style.setProperty('--color-secondary', theme.secondary);
            document.documentElement.style.setProperty('--color-accent', theme.accent);
            document.documentElement.style.setProperty('--gradient-start', theme.gradient[0]);
            document.documentElement.style.setProperty('--gradient-mid', theme.gradient[1]);
            document.documentElement.style.setProperty('--gradient-end', theme.gradient[2]);

            // Trigger re-render
            if (window.updateTheme) {
                window.updateTheme(theme);
            }
        })();
        """
    }
}
```

### 2. Update ContentView to Monitor Rank Changes

```swift
//
//  ContentView.swift (Updated)
//  Peruchito
//

import SwiftUI
import WebKit

struct ContentView: View {
    @State private var isLoading = true
    @StateObject private var themeManager = RankThemeManager.shared
    @State private var webView: WKWebView?

    var body: some View {
        ZStack {
            Color.black
                .ignoresSafeArea()

            WebView(
                isLoading: $isLoading,
                webView: $webView,
                onRankChange: { newRank in
                    // When rank changes in WebView, update theme
                    themeManager.updateTheme(forRank: newRank)
                    injectTheme()
                }
            )
            .ignoresSafeArea()

            if isLoading {
                VStack(spacing: 20) {
                    ProgressView()
                        .scaleEffect(1.5)
                        .tint(Color(hex: themeManager.currentTheme.accent))

                    Text("Loading Peruchito...")
                        .font(.system(size: 16, weight: .semibold))
                        .foregroundColor(.white)
                }
            }
        }
        .onChange(of: themeManager.currentTheme) { _ in
            injectTheme()
        }
    }

    private func injectTheme() {
        guard let webView = webView else { return }

        let script = themeManager.getThemeInjectionScript()
        webView.evaluateJavaScript(script) { result, error in
            if let error = error {
                print("Theme injection error: \(error)")
            }
        }
    }
}

// Helper for hex colors
extension Color {
    init(hex: String) {
        let hex = hex.trimmingCharacters(in: CharacterSet.alphanumerics.inverted)
        var int: UInt64 = 0
        Scanner(string: hex).scanHexInt64(&int)
        let a, r, g, b: UInt64
        switch hex.count {
        case 6: // RGB
            (a, r, g, b) = (255, int >> 16, int >> 8 & 0xFF, int & 0xFF)
        default:
            (a, r, g, b) = (255, 0, 0, 0)
        }

        self.init(
            .sRGB,
            red: Double(r) / 255,
            green: Double(g) / 255,
            blue:  Double(b) / 255,
            opacity: Double(a) / 255
        )
    }
}
```

### 3. Enhanced WebView with Message Handling

```swift
//
//  EnhancedWebView.swift
//  Peruchito
//

import SwiftUI
import WebKit

struct WebView: UIViewRepresentable {
    @Binding var isLoading: Bool
    @Binding var webView: WKWebView?
    var onRankChange: (String) -> Void

    func makeCoordinator() -> Coordinator {
        Coordinator(self)
    }

    func makeUIView(context: Context) -> WKWebView {
        let configuration = WKWebViewConfiguration()
        configuration.preferences.javaScriptEnabled = true

        // Add message handler for rank changes
        let contentController = WKUserContentController()
        contentController.add(context.coordinator, name: "rankChanged")
        configuration.userContentController = contentController

        let preferences = WKWebpagePreferences()
        preferences.allowsContentJavaScript = true
        configuration.defaultWebpagePreferences = preferences

        let webView = WKWebView(frame: .zero, configuration: configuration)
        webView.navigationDelegate = context.coordinator
        webView.scrollView.contentInsetAdjustmentBehavior = .never
        webView.isOpaque = false
        webView.backgroundColor = .black
        webView.scrollView.backgroundColor = .black

        // Load HTML
        if let htmlPath = Bundle.main.path(forResource: "index", ofType: "html") {
            let url = URL(fileURLWithPath: htmlPath)
            webView.loadFileURL(url, allowingReadAccessTo: url.deletingLastPathComponent())
        }

        DispatchQueue.main.async {
            self.webView = webView
        }

        return webView
    }

    func updateUIView(_ uiView: WKWebView, context: Context) {}

    class Coordinator: NSObject, WKNavigationDelegate, WKScriptMessageHandler {
        var parent: WebView

        init(_ parent: WebView) {
            self.parent = parent
        }

        func webView(_ webView: WKWebView, didFinish navigation: WKNavigation!) {
            DispatchQueue.main.asyncAfter(deadline: .now() + 0.5) {
                self.parent.isLoading = false
            }
        }

        func webView(_ webView: WKWebView, didFail navigation: WKNavigation!, withError error: Error) {
            self.parent.isLoading = false
        }

        // Handle messages from JavaScript
        func userContentController(_ userContentController: WKUserContentController, didReceive message: WKScriptMessage) {
            if message.name == "rankChanged", let rankName = message.body as? String {
                parent.onRankChange(rankName)
            }
        }
    }
}
```

---

## HTML/CSS Implementation

### 1. Update CSS Variables

Add these CSS variables at the top of your `<style>` section:

```css
:root {
  /* Dynamic theme colors - updated by Swift */
  --color-secondary: #7C3AED;  /* Default: Purple */
  --color-accent: #A78BFA;
  --gradient-start: #7C3AED;
  --gradient-mid: #A78BFA;
  --gradient-end: #DDD6FE;

  /* Static colors */
  --black: #000000;
  --white: #FFFFFF;
  --cream: #F7F1EA;
}
```

### 2. Update UI Components to Use Variables

Replace hardcoded purple colors with CSS variables:

```css
/* Progress bars */
.progress-bar {
  background: linear-gradient(90deg, var(--color-secondary) 0%, var(--color-accent) 100%);
  height: 8px;
  border-radius: 4px;
  transition: width 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 0 10px var(--color-accent);
}

.progress-container {
  background: rgba(167, 139, 250, 0.1);
  border-radius: 4px;
  overflow: hidden;
  border: 1px solid var(--color-secondary);
}

/* Buttons */
.btn-primary {
  background: linear-gradient(135deg, var(--color-accent) 0%, var(--color-secondary) 100%);
  color: #FFFFFF;
  font-weight: 600;
  border: none;
  border-radius: 8px;
  padding: 12px 24px;
  cursor: pointer;
  transition: all 0.2s ease;
  box-shadow: 0 4px 15px var(--color-accent);
}

.btn-primary:hover {
  background: linear-gradient(135deg, var(--gradient-mid) 0%, var(--color-secondary) 100%);
  transform: translateY(-2px);
  box-shadow: 0 6px 20px var(--color-accent);
}

/* Glass panels */
.glass {
  background: rgba(15, 15, 15, 0.9);
  border: 1px solid var(--color-secondary);
  border-radius: 16px;
}

/* Active tab */
.tab.active {
  background: rgba(139, 92, 246, 0.15);
  color: var(--color-accent);
  border: 1px solid var(--color-secondary);
}

/* Task cards - completed */
.task-card.completed {
  background: rgba(139, 92, 246, 0.1);
  border-color: var(--color-accent);
  box-shadow: 0 0 15px var(--color-accent);
}

/* Mission badges */
.mission-badge {
  background: linear-gradient(135deg, var(--color-secondary) 0%, var(--color-accent) 100%);
  color: #FFFFFF;
  padding: 4px 12px;
  border-radius: 12px;
  font-size: 10px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  box-shadow: 0 0 10px var(--color-accent);
}

/* Streak badge */
.streak-badge {
  background: linear-gradient(135deg, var(--color-secondary) 0%, var(--color-accent) 100%);
  color: #FFFFFF;
  padding: 6px 14px;
  border-radius: 20px;
  font-weight: 700;
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-size: 14px;
  box-shadow: 0 0 15px var(--color-accent);
}
```

### 3. Add JavaScript Theme Update Function

Add this to your JavaScript section:

```javascript
// Theme update function (called from Swift)
window.updateTheme = function(theme) {
  console.log('Theme updated:', theme);

  // Update CSS variables
  document.documentElement.style.setProperty('--color-secondary', theme.secondary);
  document.documentElement.style.setProperty('--color-accent', theme.accent);
  document.documentElement.style.setProperty('--gradient-start', theme.gradient[0]);
  document.documentElement.style.setProperty('--gradient-mid', theme.gradient[1]);
  document.documentElement.style.setProperty('--gradient-end', theme.gradient[2]);

  // Optional: Add transition animation
  document.body.style.transition = 'all 0.5s ease';

  // Force re-render
  renderStatic();
};

// Notify Swift when rank changes
function notifyRankChange(rankName) {
  if (window.webkit && window.webkit.messageHandlers && window.webkit.messageHandlers.rankChanged) {
    window.webkit.messageHandlers.rankChanged.postMessage(rankName);
  }
}

// Update getCurrentRank function
function getCurrentRank() {
  const totalStats = Object.values(state.stats).reduce((sum, val) => sum + val, 0);
  let currentRank = RANKS[0];

  for (const rank of RANKS) {
    if (totalStats >= rank.minStats) {
      currentRank = rank;
    } else {
      break;
    }
  }

  // Notify Swift of rank change
  notifyRankChange(currentRank.name);

  return { rank: currentRank, totalStats };
}
```

---

## Rank-Up Animation

### Add Special Effect When Ranking Up

```javascript
// Detect rank up and trigger animation
let previousRank = null;

function checkForRankUp() {
  const { rank } = getCurrentRank();

  if (previousRank && rank.name !== previousRank.name) {
    // RANK UP!
    showRankUpCelebration(previousRank.name, rank.name);
  }

  previousRank = rank;
}

function showRankUpCelebration(oldRank, newRank) {
  // Create celebration overlay
  const overlay = document.createElement('div');
  overlay.style.cssText = `
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: radial-gradient(circle, var(--color-accent) 0%, transparent 70%);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 9999;
    animation: fadeIn 0.5s ease;
  `;

  overlay.innerHTML = `
    <div style="text-align: center; animation: scaleIn 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);">
      <div style="font-size: 72px; margin-bottom: 20px;">${getRankIcon(newRank)}</div>
      <div style="font-size: 48px; font-weight: 800; color: var(--color-accent); text-shadow: 0 0 30px var(--color-accent);">
        RANK UP!
      </div>
      <div style="font-size: 32px; font-weight: 700; color: white; margin-top: 10px;">
        ${newRank}
      </div>
      <div style="font-size: 16px; color: rgba(255,255,255,0.7); margin-top: 20px;">
        Tap to continue
      </div>
    </div>
  `;

  // Add animations
  const style = document.createElement('style');
  style.textContent = `
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    @keyframes scaleIn {
      from { transform: scale(0.5); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }
  `;
  document.head.appendChild(style);

  // Add to page
  document.body.appendChild(overlay);

  // Remove on tap
  overlay.addEventListener('click', () => {
    overlay.style.animation = 'fadeIn 0.3s ease reverse';
    setTimeout(() => overlay.remove(), 300);
  });

  // Auto-remove after 5 seconds
  setTimeout(() => {
    if (overlay.parentElement) {
      overlay.style.animation = 'fadeIn 0.3s ease reverse';
      setTimeout(() => overlay.remove(), 300);
    }
  }, 5000);
}

function getRankIcon(rankName) {
  const icons = {
    'Unranked': '⚪',
    'Bronze': '🥉',
    'Silver': '🥈',
    'Gold': '🥇',
    'Platinum': '💎',
    'Diamond': '💠',
    'Master': '👑',
    'Grandmaster': '⚡',
    'Legendary': '🔥'
  };
  return icons[rankName] || '⭐';
}
```

---

## Testing Guide

### Test Each Rank Theme:

```javascript
// Add to browser console or create debug buttons

// Test Unranked (Gray)
state.stats = { str: 0, end: 0, int: 0, dis: 0 };
saveState();
renderStatic();

// Test Bronze (Brown/Amber)
state.stats = { str: 15, end: 15, int: 10, dis: 10 };
saveState();
renderStatic();

// Test Silver (Silver/White)
state.stats = { str: 40, end: 40, int: 35, dis: 35 };
saveState();
renderStatic();

// Test Gold (Yellow/Gold)
state.stats = { str: 80, end: 75, int: 75, dis: 70 };
saveState();
renderStatic();

// Test Platinum (Cyan/Turquoise)
state.stats = { str: 130, end: 125, int: 125, dis: 120 };
saveState();
renderStatic();

// Test Diamond (Blue)
state.stats = { str: 210, end: 200, int: 195, dis: 195 };
saveState();
renderStatic();

// Test Master (Purple) - Current default
state.stats = { str: 310, end: 300, int: 295, dis: 295 };
saveState();
renderStatic();

// Test Grandmaster (Orange)
state.stats = { str: 460, end: 450, int: 445, dis: 445 };
saveState();
renderStatic();

// Test Legendary (Red)
state.stats = { str: 640, end: 625, int: 625, dis: 610 };
saveState();
renderStatic();
```

---

## User Experience

### Progression Feel:

**🎮 Unranked → Bronze (First Rank Up)**
```
"Wow! The entire app turned bronze! I actually ranked up!"
```

**🥇 Silver → Gold (Mid-Game)**
```
"Everything is gold now... I'm getting somewhere"
```

**💎 Platinum → Diamond (Late Game)**
```
"Blue theme looks sick. This feels premium."
```

**👑 Diamond → Master (Elite)**
```
"Purple! Finally! This is where the pros are."
```

**🔥 Grandmaster → Legendary (Endgame)**
```
"RED. FIRE. I AM LEGENDARY. 🔥🔥🔥"
```

---

## Benefits

### 1. **Constant Visual Feedback**
- Every rank up = entire UI transformation
- Makes progression tangible and rewarding

### 2. **Status Symbol**
- Others see your rank by your app's color
- "Show me your phone... wait, you're GOLD?!"

### 3. **Motivation to Rank Up**
- "I want that red theme"
- "When do I get purple?"
- Goal beyond just numbers

### 4. **Personalization**
- Your app evolves with you
- Feels custom to your journey

### 5. **Screenshots/Social Proof**
- Different colored screenshots show rank
- "Look at my Legendary app! 🔥"

---

## Marketing Copy

### Feature Description:
> **Your App Evolves With You**
>
> Start in grayscale. Unlock bronze. Climb through silver, gold, platinum, diamond. Achieve purple as a Master. Blaze orange as a Grandmaster. Reach red fire as Legendary.
>
> Every rank transforms your entire interface. Your progress isn't just numbers—it's the color of your journey.

### App Store Screenshots:
- Show same screen in 3-4 different rank colors
- Caption: "Unranked → Bronze → Gold → Legendary"
- "Watch Your App Transform As You Level Up"

---

## Implementation Checklist

### Swift (Native):
- [ ] Create `RankThemeManager.swift`
- [ ] Update `ContentView.swift` with theme monitoring
- [ ] Add message handler for rank changes
- [ ] Inject theme on app launch
- [ ] Inject theme on rank change
- [ ] Test theme switching

### HTML/CSS:
- [ ] Add CSS variables to `:root`
- [ ] Replace hardcoded colors with `var(--color-*)`
- [ ] Update all UI components
- [ ] Add `window.updateTheme()` function
- [ ] Add `notifyRankChange()` function
- [ ] Add rank-up celebration animation

### Testing:
- [ ] Test all 9 rank themes
- [ ] Test theme injection from Swift
- [ ] Test rank-up animation
- [ ] Test persistence (theme stays on app restart)
- [ ] Test on different iPhone sizes
- [ ] Test dark mode (should look good in all themes)

---

## Performance Considerations

- ✅ CSS variables update instantly (no re-render)
- ✅ Transition animations smooth (0.5s ease)
- ✅ No performance impact (just CSS changes)
- ✅ Theme state stored in localStorage
- ✅ Injected once per rank change (not per task)

---

**This feature will make ranking up feel AMAZING!** 🎨🔥

Every time users level up, they'll literally see their entire app transform. It's like getting a new phone with every rank!
