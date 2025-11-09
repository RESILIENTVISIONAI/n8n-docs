# Hardcore Accountability Mode - Technical Implementation Guide
# App Blocking Feature for Peruchito

**Version:** 1.0
**Date:** October 31, 2025
**iOS Requirement:** iOS 16.0+
**Frameworks:** FamilyControls, ManagedSettings, DeviceActivity

---

## Overview

This guide explains how to implement the **Hardcore Accountability Mode** that blocks all non-essential apps when users don't complete their daily tasks by midnight.

### What It Does:
- ✅ Blocks distracting apps (social media, games, entertainment)
- ✅ Allows communication apps (Phone, Messages, WhatsApp)
- ✅ Triggers automatically at midnight if minimum tasks not completed
- ✅ Unlocks immediately when tasks are completed
- ✅ Provides emergency override with stat penalty

---

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Peruchito App                        │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  ┌──────────────────┐        ┌───────────────────┐    │
│  │  Task Manager    │───────▶│  Blocking Logic   │    │
│  └──────────────────┘        └───────────────────┘    │
│           │                            │               │
│           │                            ▼               │
│           │                  ┌───────────────────┐    │
│           │                  │ FamilyControls    │    │
│           │                  │ Authorization     │    │
│           │                  └───────────────────┘    │
│           │                            │               │
│           ▼                            ▼               │
│  ┌──────────────────┐        ┌───────────────────┐    │
│  │ Midnight Timer   │───────▶│ ManagedSettings   │    │
│  │ (DeviceActivity) │        │ Store             │    │
│  └──────────────────┘        └───────────────────┘    │
│                                        │               │
└────────────────────────────────────────┼───────────────┘
                                         │
                                         ▼
                              ┌─────────────────────┐
                              │   iOS System        │
                              │   (Blocks Apps)     │
                              └─────────────────────┘
```

---

## Step 1: Project Setup

### 1.1 Enable Capabilities in Xcode

1. Open your Xcode project
2. Select **Peruchito** target
3. Go to **Signing & Capabilities**
4. Click **+ Capability**
5. Add **Family Controls**

### 1.2 Update Info.plist

Add privacy description for Screen Time access:

```xml
<key>NSFamilyControlsUsageDescription</key>
<string>Peruchito needs access to Screen Time to help you stay accountable by blocking distracting apps when you don't complete your daily tasks.</string>
```

### 1.3 Required Frameworks

Add these imports to your Swift files:

```swift
import FamilyControls
import ManagedSettings
import DeviceActivity
```

---

## Step 2: Request Authorization

### 2.1 Create Authorization Manager

Create a new Swift file: `FamilyControlsManager.swift`

```swift
//
//  FamilyControlsManager.swift
//  Peruchito
//
//  Manages Screen Time / Family Controls authorization
//

import Foundation
import FamilyControls

class FamilyControlsManager: ObservableObject {
    static let shared = FamilyControlsManager()

    @Published var isAuthorized = false

    private let center = AuthorizationCenter.shared

    init() {
        checkAuthorizationStatus()
    }

    /// Check if already authorized
    func checkAuthorizationStatus() {
        switch center.authorizationStatus {
        case .approved:
            isAuthorized = true
        default:
            isAuthorized = false
        }
    }

    /// Request authorization from user
    func requestAuthorization() async throws {
        do {
            try await center.requestAuthorization(for: .individual)
            await MainActor.run {
                self.isAuthorized = true
            }
        } catch {
            await MainActor.run {
                self.isAuthorized = false
            }
            throw error
        }
    }
}
```

### 2.2 Create Authorization View

```swift
//
//  AccountabilitySetupView.swift
//  Peruchito
//
//  Onboarding screen for enabling Hardcore Accountability Mode
//

import SwiftUI
import FamilyControls

struct AccountabilitySetupView: View {
    @StateObject private var fcManager = FamilyControlsManager.shared
    @State private var showError = false
    @State private var errorMessage = ""

    var body: some View {
        VStack(spacing: 30) {
            // Header
            Text("🔥 Hardcore Accountability Mode")
                .font(.system(size: 28, weight: .bold))
                .foregroundColor(.white)

            // Explanation
            VStack(alignment: .leading, spacing: 15) {
                ExplanationRow(
                    icon: "🚫",
                    title: "Block Distracting Apps",
                    description: "If you don't complete your daily tasks by midnight, all entertainment and social apps will be blocked."
                )

                ExplanationRow(
                    icon: "✅",
                    title: "Communication Allowed",
                    description: "Phone, Messages, and WhatsApp remain accessible for emergencies."
                )

                ExplanationRow(
                    icon: "⚡",
                    title: "Instant Unlock",
                    description: "Complete your tasks anytime to immediately unlock your apps."
                )

                ExplanationRow(
                    icon: "🆘",
                    title: "Emergency Override",
                    description: "In true emergencies, override the block (costs 50 Discipline stats)."
                )
            }
            .padding()
            .background(
                RoundedRectangle(cornerRadius: 16)
                    .fill(Color.white.opacity(0.05))
            )

            Spacer()

            // Enable Button
            if !fcManager.isAuthorized {
                Button(action: enableAccountability) {
                    Text("Enable Hardcore Mode 💪")
                        .font(.system(size: 18, weight: .bold))
                        .foregroundColor(.white)
                        .frame(maxWidth: .infinity)
                        .padding()
                        .background(
                            LinearGradient(
                                colors: [Color.purple, Color.purple.opacity(0.7)],
                                startPoint: .leading,
                                endPoint: .trailing
                            )
                        )
                        .cornerRadius(12)
                }
            } else {
                Text("✅ Hardcore Mode Enabled")
                    .font(.system(size: 18, weight: .bold))
                    .foregroundColor(.green)
            }

            // Skip Button
            Button(action: { /* Skip to main app */ }) {
                Text("Skip (Not Recommended)")
                    .font(.system(size: 14))
                    .foregroundColor(.gray)
            }
        }
        .padding()
        .background(Color.black.ignoresSafeArea())
        .alert("Authorization Error", isPresented: $showError) {
            Button("OK", role: .cancel) { }
        } message: {
            Text(errorMessage)
        }
    }

    private func enableAccountability() {
        Task {
            do {
                try await fcManager.requestAuthorization()
                // Authorization successful - proceed to main app
            } catch {
                errorMessage = "Failed to enable Hardcore Mode. Please try again."
                showError = true
            }
        }
    }
}

struct ExplanationRow: View {
    let icon: String
    let title: String
    let description: String

    var body: some View {
        HStack(alignment: .top, spacing: 12) {
            Text(icon)
                .font(.system(size: 24))

            VStack(alignment: .leading, spacing: 4) {
                Text(title)
                    .font(.system(size: 16, weight: .semibold))
                    .foregroundColor(.white)

                Text(description)
                    .font(.system(size: 14))
                    .foregroundColor(.gray)
                    .fixedSize(horizontal: false, vertical: true)
            }
        }
    }
}
```

---

## Step 3: Configure App Blocking

### 3.1 Create App Blocking Manager

```swift
//
//  AppBlockingManager.swift
//  Peruchito
//
//  Manages which apps to block/allow
//

import Foundation
import FamilyControls
import ManagedSettings

class AppBlockingManager {
    static let shared = AppBlockingManager()

    private let store = ManagedSettingsStore()

    /// Block all apps except communication and essential apps
    func blockNonEssentialApps() {
        // Get all installed apps
        let selection = FamilyActivitySelection()

        // Block categories (entertainment, social, games)
        var blockedCategories: Set<ActivityCategoryToken> = []

        // Add categories to block
        // Note: These are standard iOS Screen Time categories
        blockedCategories.insert(.socialNetworking)
        blockedCategories.insert(.games)
        blockedCategories.insert(.entertainment)

        // Configure blocking
        store.shield.applicationCategories = .specific(blockedCategories)

        // Allow specific apps (communication)
        var allowedApps: Set<ApplicationToken> = []
        // Note: You need to get tokens for specific apps
        // This is done through FamilyActivityPicker in the settings UI

        store.shield.applications = .specific(allowedApps, except: Set())

        // Customize blocking screen
        store.shield.applicationCategories?.policy = .specific(blockedCategories)
    }

    /// Unlock all apps
    func unlockAllApps() {
        store.shield.applicationCategories = nil
        store.shield.applications = nil
    }

    /// Check if blocking is currently active
    func isBlocking() -> Bool {
        return store.shield.applicationCategories != nil
    }
}
```

### 3.2 Create App Selection View (Settings)

```swift
//
//  AppSelectionView.swift
//  Peruchito
//
//  Allow users to customize which apps to block/allow
//

import SwiftUI
import FamilyControls

struct AppSelectionView: View {
    @State private var selection = FamilyActivitySelection()
    @State private var isPresented = false

    var body: some View {
        VStack(spacing: 20) {
            Text("Customize Blocked Apps")
                .font(.title2)
                .fontWeight(.bold)

            Text("Choose which apps to block when you don't complete your tasks")
                .font(.subheadline)
                .foregroundColor(.gray)
                .multilineTextAlignment(.center)

            Button("Select Apps to Block") {
                isPresented = true
            }
            .buttonStyle(.borderedProminent)
            .familyActivityPicker(
                isPresented: $isPresented,
                selection: $selection
            )

            if !selection.applicationTokens.isEmpty {
                Text("\(selection.applicationTokens.count) apps selected to block")
                    .font(.caption)
                    .foregroundColor(.green)
            }
        }
        .padding()
    }
}
```

---

## Step 4: Implement Midnight Trigger

### 4.1 Create Device Activity Monitor

Create a new target extension: **DeviceActivityMonitor**

1. In Xcode: File → New → Target
2. Select **Device Activity Monitor Extension**
3. Name it: `PeruchitoActivityMonitor`

### 4.2 Implement Monitor

```swift
//
//  DeviceActivityMonitorExtension.swift
//  PeruchitoActivityMonitor
//
//  Monitors device activity and triggers at midnight
//

import DeviceActivity
import ManagedSettings

class DeviceActivityMonitorExtension: DeviceActivityMonitor {

    let store = ManagedSettingsStore()

    /// Called when the threshold is reached (midnight)
    override func intervalDidEnd(for activity: DeviceActivityName) {
        super.intervalDidEnd(for: activity)

        // Check if minimum tasks completed
        let tasksCompleted = checkTasksCompleted()

        if tasksCompleted < getMinimumTaskThreshold() {
            // Block apps
            blockApps()
        }
    }

    /// Called when monitoring starts
    override func intervalDidStart(for activity: DeviceActivityName) {
        super.intervalDidStart(for: activity)
        // Optional: Send notification
    }

    // MARK: - Helper Methods

    private func blockApps() {
        // Block all non-essential apps
        var blockedCategories: Set<ActivityCategoryToken> = []
        blockedCategories.insert(.socialNetworking)
        blockedCategories.insert(.games)
        blockedCategories.insert(.entertainment)

        store.shield.applicationCategories = .specific(blockedCategories)

        // Send notification to user
        sendBlockingNotification()
    }

    private func checkTasksCompleted() -> Int {
        // Read from shared UserDefaults or App Group
        let shared = UserDefaults(suiteName: "group.com.peruchito.app")
        return shared?.integer(forKey: "tasksCompletedToday") ?? 0
    }

    private func getMinimumTaskThreshold() -> Int {
        let shared = UserDefaults(suiteName: "group.com.peruchito.app")
        return shared?.integer(forKey: "minimumTaskThreshold") ?? 1
    }

    private func sendBlockingNotification() {
        // TODO: Implement local notification
        // "⚠️ Apps Blocked! Complete your tasks in Peruchito to unlock."
    }
}
```

### 4.3 Schedule Midnight Monitor

```swift
//
//  DeviceActivityScheduler.swift
//  Peruchito
//
//  Schedules the midnight check
//

import DeviceActivity
import Foundation

class DeviceActivityScheduler {
    static let shared = DeviceActivityScheduler()

    private let center = DeviceActivityCenter()

    /// Schedule monitoring to check at midnight
    func scheduleMidnightCheck() {
        let schedule = DeviceActivitySchedule(
            intervalStart: DateComponents(hour: 0, minute: 0), // Midnight
            intervalEnd: DateComponents(hour: 23, minute: 59), // 11:59 PM
            repeats: true
        )

        let activityName = DeviceActivityName("dailyTaskCheck")

        do {
            try center.startMonitoring(activityName, during: schedule)
        } catch {
            print("Failed to schedule midnight check: \(error)")
        }
    }

    /// Stop monitoring (when user disables feature)
    func stopMidnightCheck() {
        let activityName = DeviceActivityName("dailyTaskCheck")
        center.stopMonitoring([activityName])
    }
}
```

---

## Step 5: Integrate with Task System

### 5.1 Update Task Completion Logic

Modify your existing task completion code to:
1. Save task count to App Group storage
2. Check if blocking should be removed

```swift
//
//  TaskManager.swift (Updated)
//  Peruchito
//

import Foundation

class TaskManager {
    static let shared = TaskManager()
    private let appBlockingManager = AppBlockingManager.shared

    /// Mark task as completed
    func completeTask(_ taskId: String) {
        // Existing logic...

        // Update shared storage for Device Activity Monitor
        let tasksCompleted = getCompletedTasksCount()
        saveToAppGroup(key: "tasksCompletedToday", value: tasksCompleted)

        // Check if we should unlock apps
        checkAndUnlockIfNeeded(tasksCompleted: tasksCompleted)
    }

    private func checkAndUnlockIfNeeded(tasksCompleted: Int) {
        let minimumRequired = UserDefaults.standard.integer(forKey: "minimumTaskThreshold")

        if tasksCompleted >= minimumRequired && appBlockingManager.isBlocking() {
            // Unlock apps!
            appBlockingManager.unlockAllApps()

            // Show success message
            showUnlockSuccessNotification()
        }
    }

    private func saveToAppGroup(key: String, value: Int) {
        let shared = UserDefaults(suiteName: "group.com.peruchito.app")
        shared?.set(value, forKey: key)
    }

    private func showUnlockSuccessNotification() {
        // TODO: Show celebration UI
        // "🎉 Apps Unlocked! Great discipline 💪"
    }

    private func getCompletedTasksCount() -> Int {
        // Your existing logic to count completed tasks
        return 0 // Placeholder
    }
}
```

---

## Step 6: Add App Group (For Shared Data)

### 6.1 Enable App Groups

1. In Xcode, select **Peruchito** target
2. Go to **Signing & Capabilities**
3. Click **+ Capability** → **App Groups**
4. Create new app group: `group.com.peruchito.app`

5. Repeat for **PeruchitoActivityMonitor** extension target

### 6.2 Update Both Targets

Make sure both the main app and the Device Activity Monitor extension have the same App Group enabled.

---

## Step 7: UI/UX Implementation

### 7.1 Add Blocking Status to Home Screen

```swift
//
//  BlockingStatusBanner.swift
//  Peruchito
//

import SwiftUI

struct BlockingStatusBanner: View {
    @State private var tasksCompleted: Int = 0
    @State private var minimumRequired: Int = 1
    @State private var timeRemaining: TimeInterval = 0

    var urgencyLevel: UrgencyLevel {
        if timeRemaining < 1800 { return .critical } // < 30 min
        if timeRemaining < 3600 { return .high } // < 1 hour
        if timeRemaining < 10800 { return .medium } // < 3 hours
        return .low
    }

    var body: some View {
        VStack(spacing: 12) {
            // Timer
            HStack {
                Text("⏰ Time Until Midnight:")
                    .font(.system(size: 14, weight: .medium))

                Spacer()

                Text(formattedTime)
                    .font(.system(size: 18, weight: .bold))
                    .foregroundColor(urgencyColor)
            }

            // Progress
            HStack {
                Text("Tasks Completed:")
                    .font(.system(size: 14))

                Spacer()

                Text("\(tasksCompleted) / \(minimumRequired)")
                    .font(.system(size: 16, weight: .semibold))
                    .foregroundColor(tasksCompleted >= minimumRequired ? .green : .red)
            }

            // Warning if needed
            if tasksCompleted < minimumRequired && urgencyLevel != .low {
                HStack {
                    Image(systemName: "exclamationmark.triangle.fill")
                        .foregroundColor(.orange)

                    Text("Complete \(minimumRequired - tasksCompleted) more task(s) to avoid app blocking!")
                        .font(.system(size: 13, weight: .semibold))
                        .foregroundColor(.orange)
                }
                .padding(8)
                .background(Color.orange.opacity(0.1))
                .cornerRadius(8)
            }
        }
        .padding()
        .background(bannerBackground)
        .cornerRadius(16)
    }

    private var urgencyColor: Color {
        switch urgencyLevel {
        case .critical: return .red
        case .high: return .orange
        case .medium: return .yellow
        case .low: return .green
        }
    }

    private var bannerBackground: some View {
        RoundedRectangle(cornerRadius: 16)
            .fill(urgencyColor.opacity(0.1))
            .overlay(
                RoundedRectangle(cornerRadius: 16)
                    .stroke(urgencyColor.opacity(0.3), lineWidth: 2)
            )
    }

    private var formattedTime: String {
        let hours = Int(timeRemaining) / 3600
        let minutes = (Int(timeRemaining) % 3600) / 60
        return String(format: "%02d:%02d", hours, minutes)
    }
}

enum UrgencyLevel {
    case low, medium, high, critical
}
```

### 7.2 Emergency Override View

```swift
//
//  EmergencyOverrideView.swift
//  Peruchito
//

import SwiftUI

struct EmergencyOverrideView: View {
    @State private var confirmationStep = 0
    @Binding var isPresented: Bool

    var body: some View {
        VStack(spacing: 30) {
            Text("⚠️ Emergency Override")
                .font(.title)
                .fontWeight(.bold)

            if confirmationStep < 3 {
                Text("Are you sure? This will:")
                    .font(.headline)

                VStack(alignment: .leading, spacing: 12) {
                    WarningRow(text: "Disable blocking for 24 hours")
                    WarningRow(text: "Reduce Discipline stat by 50 points")
                    WarningRow(text: "Log this override in your history")
                }

                Text("Confirmation \(confirmationStep + 1) of 3")
                    .font(.caption)
                    .foregroundColor(.gray)

                Button(action: proceedConfirmation) {
                    Text("Yes, I understand")
                        .fontWeight(.semibold)
                        .foregroundColor(.white)
                        .frame(maxWidth: .infinity)
                        .padding()
                        .background(Color.orange)
                        .cornerRadius(12)
                }
            } else {
                // Final confirmation
                Text("Last chance to reconsider...")
                    .font(.headline)

                Button(action: executeOverride) {
                    Text("Activate Emergency Override")
                        .fontWeight(.bold)
                        .foregroundColor(.white)
                        .frame(maxWidth: .infinity)
                        .padding()
                        .background(Color.red)
                        .cornerRadius(12)
                }
            }

            Button("Cancel") {
                isPresented = false
            }
            .foregroundColor(.gray)
        }
        .padding()
    }

    private func proceedConfirmation() {
        confirmationStep += 1
    }

    private func executeOverride() {
        // Unlock apps
        AppBlockingManager.shared.unlockAllApps()

        // Apply discipline penalty
        // StatsManager.shared.addDiscipline(-50)

        // Log override
        // OverrideHistory.shared.log()

        isPresented = false
    }
}

struct WarningRow: View {
    let text: String

    var body: some View {
        HStack {
            Image(systemName: "exclamationmark.circle.fill")
                .foregroundColor(.orange)
            Text(text)
                .font(.system(size: 14))
        }
    }
}
```

---

## Step 8: Settings & Configuration

### 8.1 Accountability Settings View

```swift
//
//  AccountabilitySettingsView.swift
//  Peruchito
//

import SwiftUI

struct AccountabilitySettingsView: View {
    @AppStorage("accountabilityModeEnabled") private var isEnabled = false
    @AppStorage("minimumTaskThreshold") private var minimumTasks = 1
    @AppStorage("gracePeriodMinutes") private var gracePeriod = 0
    @AppStorage("weekendModeEnabled") private var weekendMode = false
    @AppStorage("hardcoreModeEnabled") private var hardcoreMode = false

    var body: some View {
        Form {
            Section(header: Text("Hardcore Accountability Mode")) {
                Toggle("Enable App Blocking", isOn: $isEnabled)
                    .onChange(of: isEnabled) { newValue in
                        if newValue {
                            DeviceActivityScheduler.shared.scheduleMidnightCheck()
                        } else {
                            DeviceActivityScheduler.shared.stopMidnightCheck()
                        }
                    }

                if isEnabled {
                    Stepper("Minimum Tasks: \(minimumTasks)", value: $minimumTasks, in: 1...12)

                    Stepper("Grace Period: \(gracePeriod) min", value: $gracePeriod, in: 0...60, step: 5)

                    Toggle("Weekend Mode (No blocking Sat/Sun)", isOn: $weekendMode)

                    Toggle("Hardcore Mode (No override)", isOn: $hardcoreMode)
                        .foregroundColor(hardcoreMode ? .red : .primary)
                }
            }

            Section(header: Text("Allowed Apps")) {
                NavigationLink("Customize Blocked Apps") {
                    AppSelectionView()
                }

                Text("Communication apps (Phone, Messages, WhatsApp) are always allowed")
                    .font(.caption)
                    .foregroundColor(.gray)
            }

            Section(header: Text("Status")) {
                if AppBlockingManager.shared.isBlocking() {
                    Label("Apps Currently Blocked", systemImage: "lock.fill")
                        .foregroundColor(.red)

                    Button("Complete Tasks to Unlock") {
                        // Navigate to tasks screen
                    }
                } else {
                    Label("Apps Unlocked", systemImage: "lock.open.fill")
                        .foregroundColor(.green)
                }
            }
        }
        .navigationTitle("Accountability Settings")
    }
}
```

---

## Step 9: Testing

### 9.1 Test Checklist

- [ ] Authorization flow works correctly
- [ ] Apps block at midnight when tasks incomplete
- [ ] Communication apps remain accessible
- [ ] Peruchito app remains accessible
- [ ] Apps unlock immediately when minimum tasks completed
- [ ] Emergency override works with confirmations
- [ ] Discipline stat penalty applies correctly
- [ ] Weekend mode disables blocking
- [ ] Grace period delays blocking
- [ ] Settings persist across app restarts
- [ ] Device Activity Monitor triggers correctly
- [ ] App Group data sharing works
- [ ] Notifications display properly

### 9.2 Testing Tips

1. **Change device time** to test midnight trigger
2. **Test on physical device** (not simulator - Family Controls requires real device)
3. **Test with different task counts** (0, 1, 5, 12)
4. **Test emergency override** multiple times
5. **Verify blocked apps** actually get blocked
6. **Test unlocking** by completing tasks

---

## Step 10: App Store Submission

### 10.1 Required Information

**App Privacy**:
- Data Collection: None
- Screen Time Data: Used only for blocking, not collected/transmitted

**App Description** (include):
> **Hardcore Accountability Mode**: Miss your daily tasks? Your phone blocks all distracting apps until you complete them. Communication apps remain accessible. Take control of your discipline!

**Screenshots**:
- Show blocking configuration screen
- Show warning timer
- Show blocked app screen
- Show unlock success

### 10.2 App Review Notes

```
This app uses Family Controls API to help users stay accountable to their daily goals by blocking non-essential apps when they fail to complete minimum tasks by midnight. This is an opt-in feature that requires explicit user authorization. Emergency override is always available. All data is stored locally.

Test Account: Not required (feature is opt-in)
Test Instructions: Enable "Hardcore Mode" in onboarding, skip tasks until midnight (or change device time), observe app blocking.
```

---

## Troubleshooting

### Common Issues

**1. Authorization Fails**
- Ensure `NSFamilyControlsUsageDescription` is in Info.plist
- Check that Family Controls capability is enabled
- Test on real device (not simulator)

**2. Apps Don't Block**
- Verify Device Activity Monitor extension is included in build
- Check App Group is enabled on both targets
- Ensure monitoring was started with `startMonitoring()`

**3. Unlock Doesn't Work**
- Check shared UserDefaults key is correct
- Verify App Group suite name matches
- Ensure `unlockAllApps()` sets shield to nil

**4. Midnight Trigger Doesn't Fire**
- Check DeviceActivitySchedule times are correct
- Verify monitoring is active (check in Settings → Screen Time)
- Test with device time change

---

## Security & Privacy

### Privacy Considerations

✅ **No Data Collection**: App doesn't collect which apps user has or uses
✅ **Local Only**: All blocking logic happens on-device
✅ **User Control**: User can disable feature anytime via Settings → Screen Time
✅ **Transparent**: Clear explanation of what will be blocked
✅ **Escape Hatch**: Emergency override always available

### User Safety

✅ **Communication**: Phone/Messages always accessible
✅ **Emergency**: Settings app accessible to disable feature
✅ **Health**: Health app remains accessible
✅ **Override**: Can always override with stat penalty
✅ **Grace Period**: Optional delay before blocking

---

## Performance Considerations

- Device Activity Monitor runs in separate extension (minimal battery impact)
- Monitoring uses iOS system features (efficient)
- No continuous polling (event-driven)
- Shared data via App Groups (fast)

---

## Future Enhancements

- [ ] Custom blocking schedules (block during work hours, etc.)
- [ ] App usage analytics (time spent in each app)
- [ ] Website blocking (Safari content filter)
- [ ] Focus modes integration
- [ ] Streak-based unlocks (7-day streak = no blocking for a day)
- [ ] Progressive difficulty (more tasks required over time)

---

## Resources

**Apple Documentation**:
- [Family Controls Framework](https://developer.apple.com/documentation/familycontrols)
- [Managed Settings](https://developer.apple.com/documentation/managedsettings)
- [Device Activity](https://developer.apple.com/documentation/deviceactivity)
- [Screen Time API](https://developer.apple.com/documentation/screentime)

**WWDC Sessions**:
- WWDC 2021: "Meet the Screen Time API"
- WWDC 2022: "What's new in Screen Time"

---

**End of Implementation Guide**

For questions or issues, refer to Apple's documentation or community forums.
