# Product Requirements Document (PRD)
# Peruchito - Your Life RPG

**Version:** 1.0
**Date:** October 31, 2025
**Status:** Active Development
**Document Owner:** Product Team
**Platform:** iOS (iPhone & iPad)

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Product Overview](#2-product-overview)
3. [Goals and Objectives](#3-goals-and-objectives)
4. [Target Users](#4-target-users)
5. [User Stories](#5-user-stories)
6. [Functional Requirements](#6-functional-requirements)
7. [Non-Functional Requirements](#7-non-functional-requirements)
8. [Technical Requirements](#8-technical-requirements)
9. [Design Requirements](#9-design-requirements)
10. [Success Metrics](#10-success-metrics)
11. [Roadmap](#11-roadmap)
12. [Assumptions and Constraints](#12-assumptions-and-constraints)

---

## 1. Executive Summary

### 1.1 Product Vision
Peruchito transforms everyday life into an epic RPG adventure by gamifying personal development, fitness, nutrition, and daily habits. Users gain stats, level up through ranks, and unlock achievements as they complete real-world tasks.

### 1.2 Problem Statement
People struggle with:
- Maintaining consistent daily habits
- Staying motivated for fitness and health goals
- Tracking multiple aspects of personal development
- Visualizing progress in a meaningful way
- Making self-improvement engaging and fun

### 1.3 Solution
An iOS mobile app that:
- Converts daily tasks into RPG-style missions with stat rewards
- Provides a comprehensive rank progression system (9 ranks)
- Offers structured workout guidance and calorie tracking
- Gamifies all aspects of personal growth
- Makes progress visible through beautiful, engaging UI

### 1.4 Success Criteria
- 85%+ daily task completion rate among active users
- 70%+ user retention after 30 days
- 50%+ users reach Bronze rank (50+ total stats) within 2 weeks
- 4.5+ star rating on App Store

---

## 2. Product Overview

### 2.1 Product Description
Peruchito is an iOS life gamification app that combines:
- **Task Management**: Daily, weekly, and epic missions
- **RPG Progression**: 4 core stats and 9 rank tiers
- **Fitness Tracking**: Workout library with Push/Pull/Legs split
- **Nutrition Tracking**: Food scanner with 33+ popular foods
- **Progress Visualization**: Beautiful UI with gradients, animations, and real-time feedback

### 2.2 Key Differentiators
1. **Premium Aesthetic Design**: Glass morphism, gradients, smooth animations
2. **Comprehensive Gamification**: Not just tasks - includes fitness, nutrition, learning
3. **No Backend Required**: Full offline functionality with local storage
4. **Clean Workout UI**: Text-focused, no distracting images
5. **Instant Feedback**: Real-time stat updates and visual rewards

### 2.3 Platform
- **Primary**: iOS 15.0+ (iPhone)
- **Secondary**: iPad support (universal app)
- **Future**: Apple Watch companion, Android version, Web app

---

## 3. Goals and Objectives

### 3.1 Business Goals
1. **Launch MVP** on App Store by Q1 2026
2. **Acquire 10,000 users** in first 3 months
3. **Achieve 60% retention** at Day 30
4. **Monetization**: Freemium model with premium features (future)

### 3.2 User Goals
1. Build consistent daily habits
2. Track fitness progress effectively
3. Stay motivated through gamification
4. Visualize personal growth
5. Achieve "Legendary" rank status

### 3.3 Product Goals
1. **Engagement**: Users open app daily
2. **Completion**: 80%+ daily task completion
3. **Retention**: Users return for 30+ consecutive days
4. **Satisfaction**: 4.5+ star App Store rating

---

## 4. Target Users

### 4.1 Primary Personas

#### Persona 1: "Fitness Enthusiast Felix"
- **Age**: 22-35
- **Occupation**: Young professional, student, or entrepreneur
- **Goals**: Build muscle, track workouts, maintain consistency
- **Pain Points**: Loses motivation, struggles with nutrition tracking
- **Tech Savvy**: High - uses multiple fitness apps
- **Motivations**: Progress tracking, visual achievements, competition

#### Persona 2: "Productivity Pioneer Patricia"
- **Age**: 25-40
- **Occupation**: Remote worker, freelancer, content creator
- **Goals**: Daily habit formation, time management, self-improvement
- **Pain Points**: Procrastination, lacks structure, too many todo apps
- **Tech Savvy**: Medium - uses basic productivity tools
- **Motivations**: Gamification, visual progress, dopamine hits

#### Persona 3: "Transformation Seeker Sam"
- **Age**: 18-30
- **Occupation**: Student, early career professional
- **Goals**: Complete lifestyle change, weight loss, skill building
- **Pain Points**: Overwhelmed by goals, lacks accountability
- **Tech Savvy**: Medium-High - active on social media
- **Motivations**: Visible transformation, rank achievements, streaks

### 4.2 User Characteristics
- **Age Range**: 18-40 (primary), 40+ (secondary)
- **Gender**: All genders
- **Income**: $30k-$100k+ annually
- **Education**: High school to graduate degree
- **Interests**: Fitness, gaming, self-improvement, productivity
- **Device**: iPhone users with iOS 15+

---

## 5. User Stories

### 5.1 Core User Journeys

#### Journey 1: First-Time User Onboarding
```
AS A new user
I WANT TO understand how the app works quickly
SO THAT I can start gaining stats immediately

Acceptance Criteria:
- App launches with clear home screen showing current rank
- Daily tasks are immediately visible
- First task completion shows stat gain animation
- Rank progress bar updates in real-time
```

#### Journey 2: Daily Task Completion
```
AS A daily user
I WANT TO complete my tasks and see immediate progress
SO THAT I feel motivated to continue

Acceptance Criteria:
- Tasks display with clear descriptions and stat rewards
- One-tap completion with visual feedback
- Stats update immediately with animations
- Completion shows time until daily reset
```

#### Journey 3: Rank Progression
```
AS A motivated user
I WANT TO see my rank increase as I gain stats
SO THAT I feel a sense of achievement

Acceptance Criteria:
- Current rank displays with beautiful gradient badge
- Progress bar shows % to next rank
- Stats needed for next rank is clearly visible
- Rank up triggers celebration animation (future)
```

### 5.2 Feature-Specific Stories

#### Workout Library
```
AS A fitness user
I WANT TO browse workout exercises by muscle group
SO THAT I can plan my training sessions

Acceptance Criteria:
- Push/Pull/Legs tabs are clearly labeled
- Exercises display with muscle target, description, and tips
- No loading delays when switching tabs
- Clean, text-focused design without images
```

#### Food Scanner
```
AS A nutrition-conscious user
I WANT TO quickly log calories from popular foods
SO THAT I can track my daily intake

Acceptance Criteria:
- 33+ popular foods organized by category
- One-tap to add food with automatic calorie addition
- Food log shows recent entries
- Daily calorie total updates in real-time
- Delete option for logged foods
```

#### Streak Tracking
```
AS A consistency-focused user
I WANT TO maintain my daily streak
SO THAT I stay accountable to my goals

Acceptance Criteria:
- Streak counter displays prominently on home screen
- Fire emoji indicates active streak
- Streak resets at midnight if no tasks completed
- Visual indicator shows days until streak milestone
```

---

## 6. Functional Requirements

### 6.1 Core Features (MVP - Must Have)

#### 6.1.1 Rank Progression System
**Priority**: P0 (Critical)

**Requirements**:
- FR-1.1: System shall support 9 distinct ranks:
  - Unranked (0 stats)
  - Bronze (50+ stats)
  - Silver (150+ stats)
  - Gold (300+ stats)
  - Platinum (500+ stats)
  - Diamond (800+ stats)
  - Master (1200+ stats)
  - Grandmaster (1800+ stats)
  - Legendary (2500+ stats)

- FR-1.2: Each rank shall display:
  - Unique emoji icon
  - Custom 3-stop gradient background
  - Glow/shadow effect
  - Rank name in uppercase

- FR-1.3: Progress calculation:
  - Display current total stats
  - Show progress % to next rank
  - Calculate stats needed for next rank
  - Update in real-time when stats change

- FR-1.4: Rank display locations:
  - Home screen (current rank badge)
  - Stats screen (all ranks in responsive grid)
  - Profile screen (current rank with details)

**Acceptance Criteria**:
- ✅ All 9 ranks render with correct gradients
- ✅ Progress bar animates smoothly (0-100%)
- ✅ Stats calculation is accurate
- ✅ Grid layout is responsive on all iPhone sizes

---

#### 6.1.2 RPG Stats System
**Priority**: P0 (Critical)

**Requirements**:
- FR-2.1: Four core stats shall be tracked:
  - **Strength (STR)**: Gained from workouts, lifting
  - **Endurance (END)**: Gained from workouts, consistency
  - **Intelligence (INT)**: Gained from learning, Bible study, content
  - **Discipline (DIS)**: Gained from all completed tasks, streaks

- FR-2.2: Stat display:
  - Individual stat values (0-9999)
  - Total stats (sum of all 4)
  - Color-coded bars:
    - Strength: Red (#F6554D)
    - Endurance: Blue (#4A5F8C)
    - Intelligence: Yellow (#FABB5A)
    - Discipline: Cream (#F7F1EA)

- FR-2.3: Stat progression:
  - Stats increase when tasks are completed
  - Each task specifies stat rewards
  - Visual progress bar animation on gain
  - Confetti or celebration effect (future)

**Acceptance Criteria**:
- ✅ All 4 stats display correctly
- ✅ Total stats calculation is accurate
- ✅ Progress bars fill proportionally
- ✅ Stats persist across app sessions

---

#### 6.1.3 Daily Task System
**Priority**: P0 (Critical)

**Requirements**:
- FR-3.1: Minimum 12 daily tasks covering:
  - Fitness: Morning workout, second workout
  - Nutrition: Healthy eating, nutrition tracking
  - Personal Care: Skincare, grooming, supplements
  - Learning: Bible study, AI learning, content consumption
  - Productivity: Deep work sessions
  - Social: Family time

- FR-3.2: Task properties:
  - Unique ID
  - Task name
  - Description
  - Icon (Font Awesome)
  - Stat rewards (which stats + amount)
  - Completion state (boolean)

- FR-3.3: Task interaction:
  - Tap to complete
  - Visual state change (checkmark, glow effect)
  - Stats awarded immediately
  - Cannot un-complete once done

- FR-3.4: Daily reset:
  - All tasks reset at 12:00 AM ET
  - Countdown timer shows time until reset
  - Completion state stored in local storage
  - New day starts with all tasks incomplete

**Acceptance Criteria**:
- ✅ All tasks render with correct icons and descriptions
- ✅ Completion triggers stat gain
- ✅ Visual feedback is immediate
- ✅ Reset occurs at exact midnight
- ✅ Timer counts down accurately

---

#### 6.1.4 Workout Library
**Priority**: P0 (Critical)

**Requirements**:
- FR-4.1: Three workout categories:
  - **Push Day**: Chest, shoulders, triceps (5 exercises)
  - **Pull Day**: Back, biceps, rear delts (5 exercises)
  - **Legs Day**: Quads, hamstrings, calves (5 exercises)

- FR-4.2: Exercise information:
  - Exercise name
  - Target muscle group
  - Exercise description/form cues
  - Pro tips for execution
  - No images (text-only for clean design)

- FR-4.3: Display features:
  - Tab navigation (Push/Pull/Legs)
  - Numbered exercise list (1-5)
  - Muscle target badge with icon
  - Highlighted tips section
  - Hover/tap effects for cards

- FR-4.4: Exercises included:
  - **Push**: Bench Press, Overhead Press, Incline DB Press, Lateral Raises, Tricep Dips
  - **Pull**: Deadlifts, Pull-ups, Barbell Rows, Face Pulls, Bicep Curls
  - **Legs**: Squats, RDLs, Leg Press, Leg Curls, Calf Raises

**Acceptance Criteria**:
- ✅ All 15 exercises display correctly
- ✅ Tab switching is instant (no lag)
- ✅ Cards are clean and readable
- ✅ Tips section stands out visually
- ✅ No images, text-focused design

---

#### 6.1.5 Food Scanner & Calorie Tracking
**Priority**: P0 (Critical)

**Requirements**:
- FR-5.1: Food database with 33+ items:
  - Fast food (McDonald's, KFC, Pizza Hut, Subway, Taco Bell, etc.)
  - Snacks (chips, candy, cookies, etc.)
  - Drinks (Coke, Pepsi, Red Bull, Monster, Gatorade, etc.)
  - Breakfast (cereal, eggs, bacon, Pop-Tarts, etc.)
  - Healthy options (chicken, protein, Greek yogurt, fruits, etc.)
  - Restaurant meals (Chipotle, Panera, Olive Garden, etc.)

- FR-5.2: Food properties:
  - Food name
  - Category
  - Calories
  - Protein (g)
  - Carbs (g)
  - Fats (g)

- FR-5.3: Logging functionality:
  - Browse foods by category
  - One-tap quick add
  - Manual calorie input option
  - Food log history (shows recent entries)
  - Delete logged items
  - Daily total auto-calculation

- FR-5.4: Display:
  - Food cards with macros
  - Daily calorie total (large, prominent)
  - "Add to Daily Total" button
  - Food log with timestamps
  - Clear/reset option

**Acceptance Criteria**:
- ✅ All 33+ foods render correctly
- ✅ Quick add updates total immediately
- ✅ Food log persists across sessions
- ✅ Delete removes from total
- ✅ Daily total resets at midnight

---

#### 6.1.6 Streak System
**Priority**: P1 (High)

**Requirements**:
- FR-6.1: Streak tracking:
  - Counts consecutive days with ≥1 completed task
  - Displays fire emoji + number
  - Resets to 0 if no tasks completed by midnight
  - Persists across app sessions

- FR-6.2: Display locations:
  - Home screen (top badge)
  - Profile screen (detailed view)
  - Stats screen (as achievement)

- FR-6.3: Milestones:
  - 7 days: Weekly streak badge
  - 30 days: Monthly streak badge
  - 100 days: Century streak badge
  - 365 days: Yearly streak badge

**Acceptance Criteria**:
- ✅ Streak increments on first task completion each day
- ✅ Streak resets if no tasks by midnight
- ✅ Fire emoji displays correctly
- ✅ Milestones unlock at correct thresholds

---

#### 6.1.7 Weekly Weight Check-In
**Priority**: P1 (High)

**Requirements**:
- FR-7.1: Weight logging:
  - Input field accepts decimals (e.g., 185.5 lbs)
  - Log button enabled only after 7 days since last entry
  - Countdown timer shows days/hours until next check-in
  - Progress bar (0-7 days)

- FR-7.2: Weight history:
  - Stores all weight entries with timestamps
  - Displays last 4 entries
  - Calculates weight change (+/- lbs)
  - Shows trend (up/down/stable)

- FR-7.3: Restrictions:
  - Cannot log more than once per 7 days
  - Input validation (50-500 lbs range)
  - Button disabled if timer active

**Acceptance Criteria**:
- ✅ Weight logs successfully
- ✅ 7-day cooldown enforced
- ✅ Timer counts down accurately
- ✅ History displays correctly

---

#### 6.1.8 Hardcore Accountability Mode - App Blocking
**Priority**: P1 (High - Unique Differentiator)

**Requirements**:
- FR-8.1: Automatic app blocking when daily tasks not completed by midnight
  - Blocks all non-essential apps on device
  - Allows communication apps only:
    - Phone app (calls)
    - Messages (iMessage, SMS)
    - WhatsApp
    - Emergency apps (Settings, Health)
  - Peruchito app remains accessible to complete tasks

- FR-8.2: Blocking trigger conditions:
  - Timer reaches 00:00:00 (midnight ET)
  - Minimum task threshold not met (configurable: 1-12 tasks)
  - Default: At least 1 task must be completed

- FR-8.3: User authorization flow:
  - Requires explicit opt-in during onboarding
  - Uses iOS Screen Time/Family Controls API
  - User grants parental control permissions
  - Clear explanation of what will be blocked
  - Can be disabled in settings (with confirmation)

- FR-8.4: Blocking behavior:
  - Blocks apps immediately at midnight if criteria not met
  - Shows custom blocking screen: "Complete your daily tasks in Peruchito to unlock"
  - Provides "Open Peruchito" button
  - Remains blocked until minimum tasks completed

- FR-8.5: Unblocking mechanism:
  - Automatically unblocks when minimum tasks completed
  - Immediate unlock (no delay)
  - Success notification: "Apps unlocked! Great discipline 💪"
  - Resets for next day cycle

- FR-8.6: Emergency override:
  - "Emergency Override" button (requires 3 confirmations)
  - Disables blocking for 24 hours
  - Costs discipline stats (-50 DIS penalty)
  - Shows warning: "Using emergency override will decrease your Discipline stat"
  - Logs override in history

- FR-8.7: Customization options:
  - Set minimum task count (1-12 tasks)
  - Choose which apps to allow (whitelist)
  - Set grace period (0-60 minutes after midnight)
  - Weekend mode (disable blocking on Sat/Sun)
  - Hardcore mode (no override available)

- FR-8.8: Visual indicators:
  - Home screen shows blocking status
  - Timer shows warning colors:
    - Green: >6 hours remaining
    - Yellow: 3-6 hours remaining
    - Orange: 1-3 hours remaining
    - Red: <1 hour + minimum tasks not met
  - Pulsing "URGENT" indicator when < 30 min

**Technical Implementation**:
- Use iOS 16+ **Screen Time API** and **Family Controls** framework
- Requires `FamilyControls` entitlement from Apple
- `ManagedSettingsStore` for blocking configuration
- `DeviceActivityMonitor` for midnight trigger
- `AuthorizationCenter` for parental controls permission

**Privacy & Safety**:
- Clear privacy disclosure in App Store description
- Cannot be bypassed without user permission revocation
- Emergency override always available (with penalty)
- No data collection on blocked app usage
- User maintains full control via iOS Settings

**User Stories**:
```
AS A disciplined user
I WANT my phone to block distracting apps if I don't complete tasks
SO THAT I'm forced to prioritize my daily goals

AS A procrastinator
I WANT a consequence for missing my tasks
SO THAT I build consistent habits through accountability

AS A hardcore user
I WANT no escape from my commitments
SO THAT I achieve my transformation goals faster
```

**Acceptance Criteria**:
- ✅ User can enable/disable blocking mode in settings
- ✅ Blocking triggers exactly at midnight if minimum tasks not met
- ✅ Communication apps remain accessible
- ✅ Peruchito app remains accessible
- ✅ Apps unlock immediately when tasks completed
- ✅ Emergency override works with stat penalty
- ✅ Warning indicators display correctly
- ✅ All blocking configurations save properly

**UX Considerations**:
- **Onboarding**: Clear explanation with video/animation showing how it works
- **Warnings**: Multiple reminders as midnight approaches
- **Transparency**: Show list of apps that will be blocked
- **Escape Hatch**: Emergency override with clear consequences
- **Motivation**: Positive reinforcement when unlocked successfully

**App Store Compliance**:
- Clearly describe blocking functionality in App Store description
- Mark as "Parental Controls" or "Screen Time Management" category
- Include screenshots showing blocking feature
- Age rating: 4+ (requires parental permission for under 13)

---

### 6.2 Enhanced Features (Post-MVP - Should Have)

#### 6.2.1 Mission System
**Priority**: P2 (Medium)

**Requirements**:
- Weekly missions (complete X tasks in 7 days)
- Epic missions (long-term challenges)
- Mission rewards (bonus stats, badges)
- Mission progress tracking

---

#### 6.2.2 Rewards & Unlocks
**Priority**: P2 (Medium)

**Requirements**:
- Badge collection system
- Avatar customization
- Title unlocks ("The Disciplined", "The Strong")
- Special emojis/icons

---

#### 6.2.3 Data Visualization
**Priority**: P2 (Medium)

**Requirements**:
- Stats history graphs (7/30/90 day views)
- Task completion heatmap
- Weight progress chart
- Rank progression timeline

---

### 6.3 Future Features (Nice to Have)

#### 6.3.1 Social Features
**Priority**: P3 (Low)

**Requirements**:
- Friends list
- Leaderboards (global/friends)
- Compare ranks
- Share achievements

---

#### 6.3.2 Customization
**Priority**: P3 (Low)

**Requirements**:
- Custom task creation
- Adjustable stat rewards
- Theme selection (color schemes)
- Workout routine builder

---

#### 6.3.3 Advanced Tracking
**Priority**: P3 (Low)

**Requirements**:
- Apple Health integration
- Workout session tracking (sets/reps/weight)
- Macro calculator
- Meal planning

---

## 7. Non-Functional Requirements

### 7.1 Performance
- **NFR-1.1**: App shall launch in <2 seconds on iPhone 12 or newer
- **NFR-1.2**: All animations shall run at 60fps minimum
- **NFR-1.3**: Task completion shall trigger visual feedback in <100ms
- **NFR-1.4**: Data persistence shall occur <50ms after state change
- **NFR-1.5**: Memory usage shall not exceed 150MB during normal operation

### 7.2 Reliability
- **NFR-2.1**: App shall not crash during normal user operation (99.9% stability)
- **NFR-2.2**: Local storage shall persist data across app closures with 100% accuracy
- **NFR-2.3**: Daily reset timer shall execute within ±5 seconds of midnight
- **NFR-2.4**: Data shall not corrupt if app is force-closed

### 7.3 Usability
- **NFR-3.1**: New users shall complete first task within 30 seconds of app launch
- **NFR-3.2**: All primary actions shall be reachable with one thumb
- **NFR-3.3**: Font sizes shall be readable without zooming (minimum 14px)
- **NFR-3.4**: Color contrast shall meet WCAG AA standards (4.5:1 minimum)
- **NFR-3.5**: No feature shall require more than 3 taps to access

### 7.4 Compatibility
- **NFR-4.1**: App shall support iOS 15.0 through latest iOS version
- **NFR-4.2**: App shall be universal (iPhone + iPad)
- **NFR-4.3**: App shall support all iPhone screen sizes (iPhone SE to Pro Max)
- **NFR-4.4**: App shall support portrait and landscape orientations
- **NFR-4.5**: App shall work on devices with/without notch (safe area support)

### 7.5 Security & Privacy
- **NFR-5.1**: All data shall be stored locally (no server transmission)
- **NFR-5.2**: No user authentication required for MVP
- **NFR-5.3**: No analytics tracking without user consent
- **NFR-5.4**: No third-party data sharing
- **NFR-5.5**: App shall comply with Apple App Store privacy guidelines

### 7.6 Accessibility
- **NFR-6.1**: App shall support VoiceOver screen reader
- **NFR-6.2**: All interactive elements shall have accessible labels
- **NFR-6.3**: Color shall not be the only means of conveying information
- **NFR-6.4**: Text shall support Dynamic Type sizing
- **NFR-6.5**: All animations shall respect "Reduce Motion" setting

### 7.7 Offline Functionality
- **NFR-7.1**: Core features shall work without internet connection
- **NFR-7.2**: Only CDN resources (Tailwind, Font Awesome) require internet
- **NFR-7.3**: App shall gracefully handle offline state
- **NFR-7.4**: No degradation of functionality when offline (except initial load)

---

## 8. Technical Requirements

### 8.1 Platform & Framework
- **TR-1.1**: iOS 15.0+ deployment target
- **TR-1.2**: Swift 5.0+ programming language
- **TR-1.3**: SwiftUI framework for native UI
- **TR-1.4**: WKWebView for HTML/CSS/JS rendering
- **TR-1.5**: Xcode 15.0+ for development

### 8.2 Architecture
- **TR-2.1**: Hybrid app architecture (SwiftUI wrapper + HTML content)
- **TR-2.2**: Local storage using browser localStorage API
- **TR-2.3**: State management via JavaScript
- **TR-2.4**: No backend/server infrastructure
- **TR-2.5**: No database (localStorage only)

### 8.3 Frontend Technologies
- **TR-3.1**: HTML5 for content structure
- **TR-3.2**: CSS3 for styling and animations
- **TR-3.3**: Vanilla JavaScript (no frameworks)
- **TR-3.4**: Tailwind CSS (CDN) for utility styling
- **TR-3.5**: Font Awesome (CDN) for icons

### 8.4 Data Storage
- **TR-4.1**: localStorage for user data persistence
- **TR-4.2**: JSON format for structured data
- **TR-4.3**: Maximum 10MB storage usage
- **TR-4.4**: Data schema versioning for future migrations

### 8.5 External Dependencies
- **TR-5.1**: Tailwind CSS CDN (https://cdn.tailwindcss.com)
- **TR-5.2**: Font Awesome CDN (v6.5.1+)
- **TR-5.3**: Google Fonts (Inter font family)
- **TR-5.4**: No other third-party libraries

### 8.6 Build & Deployment
- **TR-6.1**: Xcode project format (.xcodeproj)
- **TR-6.2**: Code signing with Apple Developer account
- **TR-6.3**: App Store distribution
- **TR-6.4**: TestFlight for beta testing
- **TR-6.5**: Automated builds via Xcode Cloud (future)

---

## 9. Design Requirements

### 9.1 Visual Design

#### 9.1.1 Color Palette
**Primary Colors:**
- **Black**: #000000 (background)
- **Purple**: #A78BFA (accent, primary actions)
- **Purple Dark**: #7C3AED (gradients, hover states)
- **White**: #FFFFFF (text, icons)

**Secondary Colors:**
- **Red**: #F6554D (Strength stat)
- **Blue**: #4A5F8C (Endurance stat)
- **Yellow**: #FABB5A (Intelligence stat)
- **Cream**: #F7F1EA (Discipline stat)

**Gradients:**
- All rank badges use custom 3-stop gradients
- Progress bars use purple gradient (A78BFA → 7C3AED)
- Glass panels use rgba transparency

#### 9.1.2 Typography
- **Primary Font**: Inter (Google Fonts)
- **Weights**: 300 (light), 400 (regular), 500 (medium), 600 (semibold), 700 (bold), 800 (extra bold)
- **Fallback**: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif

**Font Sizes:**
- Headings: 24-32px
- Subheadings: 18-20px
- Body: 14-16px
- Small/meta: 12-13px
- Rank badges: 16px (names), 28px (icons)

#### 9.1.3 Design System
**Glass Morphism:**
- Background: rgba(15, 15, 15, 0.9)
- Border: 1px solid rgba(167, 139, 250, 0.3)
- Border radius: 16px (cards), 12px (buttons)
- Backdrop filter: blur(10px)

**Shadows & Glows:**
- Rank badges: Custom shadow per rank (0 0 20-40px rgba)
- Buttons: 0 4px 15px rgba(167, 139, 250, 0.4)
- Cards on hover: 0 8px 24px rgba(139, 92, 246, 0.3)

**Spacing:**
- Section padding: 24px (p-6)
- Card padding: 16-20px
- Element gaps: 8-16px
- Safe area insets: env(safe-area-inset-*)

### 9.2 Animations & Interactions

#### 9.2.1 Animation Principles
- **Duration**: 200-400ms for most interactions
- **Easing**: cubic-bezier(0.4, 0, 0.2, 1) for smoothness
- **Frame Rate**: 60fps minimum
- **Reduce Motion**: Respect iOS accessibility setting

#### 9.2.2 Specific Animations
**Rank Icons:**
- Float animation (3s infinite ease-in-out)
- Vertical translation: -4px to 0px

**Rank Badges:**
- Hover: scale(1.08) + translateY(-2px)
- Shine sweep effect on hover

**Progress Bars:**
- Width transition: 0.5s cubic-bezier
- Glow effect: 0 0 10px rgba(purple)

**Task Completion:**
- Checkmark appear with scale
- Card glow effect
- Stat counter increment (number animation)

**Tab Switching:**
- Instant (no transition)
- Active state color change

#### 9.2.3 Touch Interactions
- **Tap Targets**: Minimum 44x44px
- **Tap Feedback**: Color change within 100ms
- **Long Press**: Disabled (not needed)
- **Swipe**: Not implemented in MVP
- **Haptics**: Native iOS tap feedback

### 9.3 Layouts

#### 9.3.1 Screen Layouts

**Home Screen:**
- Top: Rank badge + total stats
- Timer: Countdown to midnight
- Daily tasks: Scrollable list
- Bottom: Tab navigation (5 tabs)

**Stats Screen:**
- Top: 4 stat bars with values
- Middle: Rank grid (responsive, 1-3 columns)
- Bottom: Tab navigation

**Track Screen (Fitness):**
- Top: Food scanner section
- Middle: Workout library (tabbed)
- Bottom: Weight check-in
- Bottom: Tab navigation

**Missions Screen:**
- Daily missions
- Weekly missions
- Epic missions
- Tab navigation

**Profile Screen:**
- Current rank showcase
- Total stats breakdown
- Streak information
- Settings (future)

#### 9.3.2 Responsive Behavior
- **iPhone SE (375px)**: Single column, smaller font sizes
- **iPhone Standard (390px)**: Standard layout
- **iPhone Pro Max (428px)**: Larger spacing, 2-column grids
- **iPad**: Multi-column layouts, larger cards

### 9.4 Iconography
- **Icon Library**: Font Awesome 6.5.1
- **Icon Style**: Solid (fa-solid)
- **Common Icons**:
  - Home: fa-house
  - Trophy: fa-trophy
  - Gift: fa-gift
  - Chart: fa-chart-simple
  - Dumbbell: fa-dumbbell
  - User: fa-user
  - Fire: fa-fire
  - Star: fa-star
  - Info: fa-info-circle
  - Bullseye: fa-bullseye

---

## 10. Success Metrics

### 10.1 Key Performance Indicators (KPIs)

#### 10.1.1 Engagement Metrics
| Metric | Target | Measurement Period |
|--------|--------|-------------------|
| Daily Active Users (DAU) | 60% of MAU | Daily |
| Average Session Length | 5-10 minutes | Daily |
| Sessions Per Day | 2-3 sessions | Daily |
| Task Completion Rate | 85%+ | Daily |
| Feature Usage (Workout Library) | 40%+ users | Weekly |
| Food Logger Usage | 50%+ users | Weekly |

#### 10.1.2 Retention Metrics
| Metric | Target | Measurement Period |
|--------|--------|-------------------|
| Day 1 Retention | 80% | Daily |
| Day 7 Retention | 65% | Weekly |
| Day 30 Retention | 50% | Monthly |
| Day 90 Retention | 35% | Quarterly |

#### 10.1.3 Progression Metrics
| Metric | Target | Measurement Period |
|--------|--------|-------------------|
| Users Reaching Bronze | 70% | Within 2 weeks |
| Users Reaching Silver | 40% | Within 1 month |
| Users Reaching Gold | 20% | Within 3 months |
| Users Reaching Legendary | 1% | Within 6 months |
| Average Stats Per Active User | 500+ | Monthly |

#### 10.1.4 Quality Metrics
| Metric | Target | Measurement Period |
|--------|--------|-------------------|
| App Store Rating | 4.5+ stars | Ongoing |
| Crash-Free Rate | 99.9% | Daily |
| App Launch Time | <2 seconds | Per version |
| User-Reported Bugs | <5 per 1000 users | Monthly |

### 10.2 Analytics Events to Track

#### 10.2.1 User Actions
- `app_opened` - App launch
- `task_completed` - Task marked as complete
- `rank_achieved` - New rank unlocked
- `workout_viewed` - Workout library accessed
- `food_logged` - Food added to tracker
- `weight_logged` - Weight check-in completed
- `streak_milestone` - 7/30/100/365 day streak reached
- `tab_switched` - Navigation between screens

#### 10.2.2 System Events
- `daily_reset` - Midnight reset triggered
- `data_persisted` - localStorage save
- `error_occurred` - App error/crash
- `performance_slow` - Lag detected

### 10.3 A/B Testing Opportunities
1. **Onboarding Flow**: Tutorial vs. no tutorial
2. **Task Rewards**: Higher stat rewards vs. lower
3. **Rank Names**: Current names vs. alternatives
4. **Color Scheme**: Purple theme vs. blue/green
5. **Notification Timing**: Morning vs. evening reminders (future)

---

## 11. Roadmap

### 11.1 Phase 1: MVP Launch (Q1 2026)

**Timeline**: 12 weeks

**Week 1-2: Foundation**
- ✅ Xcode project setup
- ✅ SwiftUI + WKWebView integration
- ✅ Basic HTML/CSS structure
- ✅ localStorage implementation

**Week 3-4: Core Features**
- ✅ Rank system (all 9 ranks)
- ✅ Stats system (4 stats)
- ✅ Daily task system
- ✅ Task completion logic
- ✅ Daily reset timer

**Week 5-6: Fitness & Nutrition**
- ✅ Workout library (15 exercises)
- ✅ Push/Pull/Legs tabs
- ✅ Food scanner (33+ foods)
- ✅ Calorie tracking
- ✅ Weight check-in

**Week 7-8: UI/UX Polish**
- ✅ Premium gradient designs
- ✅ Animations and transitions
- ✅ Glass morphism effects
- ✅ Responsive layouts

**Week 9-10: Testing**
- QA testing on all devices
- Performance optimization
- Bug fixes
- Accessibility testing

**Week 11-12: Launch Prep**
- App Store assets (screenshots, icon, description)
- Privacy policy
- App Store submission
- TestFlight beta testing

**MVP Features Included:**
- ✅ 9-rank progression system
- ✅ 4 RPG stats
- ✅ 12+ daily tasks
- ✅ Workout library (15 exercises)
- ✅ Food scanner (33+ foods)
- ✅ Weight tracking
- ✅ Streak system
- ✅ Local storage persistence

---

### 11.2 Phase 2: Enhancements (Q2 2026)

**Timeline**: 8 weeks

**Features:**
- Mission system (weekly + epic)
- Badge/achievement collection
- Stats history graphs
- Custom task creation
- Export data functionality
- Dark/light theme toggle
- Haptic feedback
- Sound effects (optional)

**Goals:**
- Increase retention to 60% (Day 30)
- Add premium features for monetization
- Improve onboarding experience

---

### 11.3 Phase 3: Expansion (Q3 2026)

**Timeline**: 12 weeks

**Features:**
- Apple Watch app
- Apple Health integration
- Siri Shortcuts
- Widgets (Home Screen + Lock Screen)
- iCloud sync across devices
- Family sharing / multiplayer
- Leaderboards

**Goals:**
- Expand to iPad-optimized UI
- Launch Android version (separate development)
- Reach 50k active users

---

### 11.4 Phase 4: Monetization (Q4 2026)

**Timeline**: Ongoing

**Premium Features (Subscription):**
- Unlimited custom tasks
- Advanced analytics
- Cloud backup
- Custom themes
- Ad-free experience
- Priority support

**Pricing Model:**
- Free tier: Core features
- Premium: $4.99/month or $39.99/year
- Lifetime: $99.99 one-time

**Goals:**
- 10% conversion to premium
- $5k MRR (Monthly Recurring Revenue)

---

## 12. Assumptions and Constraints

### 12.1 Assumptions

**User Assumptions:**
1. Users have iPhone with iOS 15.0 or later
2. Users understand basic gamification concepts
3. Users are self-motivated to improve
4. Users check app daily for best experience
5. Users have internet for CDN resources (Tailwind, Font Awesome)

**Technical Assumptions:**
1. localStorage is sufficient for data storage
2. WKWebView performs well for HTML content
3. No backend is needed for MVP
4. CDN resources are reliably available
5. iOS WebView supports all required CSS/JS features

**Business Assumptions:**
1. App Store approval will be granted
2. No copyright issues with design/content
3. Free app with future premium model
4. Self-funded development (no external funding needed initially)

### 12.2 Constraints

**Technical Constraints:**
1. **Platform**: iOS only (no Android for MVP)
2. **Storage**: Limited to localStorage capacity (~10MB)
3. **Offline**: Requires internet for initial CDN load
4. **Data**: No cloud backup in MVP
5. **Sync**: No multi-device sync in MVP

**Resource Constraints:**
1. **Development**: Solo developer or small team
2. **Timeline**: 12-week MVP development
3. **Budget**: Minimal ($99/year Apple Developer + hosting)
4. **Marketing**: Organic/word-of-mouth initially

**Design Constraints:**
1. **Brand**: "Peruchito" name and purple theme established
2. **Icons**: Limited to Font Awesome free tier
3. **Images**: No custom exercise photos (text-only by design)
4. **Accessibility**: Must meet WCAG AA standards minimum

**Legal Constraints:**
1. **Privacy**: Must comply with Apple App Store guidelines
2. **Age**: 4+ rating (no mature content)
3. **COPPA**: If targeting users under 13, additional compliance needed
4. **Terms**: Need Terms of Service and Privacy Policy

### 12.3 Risks and Mitigations

| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|------------|
| App Store rejection | High | Low | Follow Apple guidelines strictly, test thoroughly |
| Poor user retention | High | Medium | Implement engaging onboarding, push notifications |
| Performance issues on older devices | Medium | Medium | Test on iPhone 8/SE, optimize animations |
| localStorage data loss | High | Low | Implement export/backup feature, educate users |
| CDN unavailability | Medium | Low | Consider bundling Tailwind/FA in future version |
| Low user adoption | High | Medium | Pre-launch marketing, TestFlight beta, influencer outreach |
| Competitor launches similar app | Medium | Medium | Focus on unique features (rank system, aesthetic design) |
| Feature creep delays launch | Medium | High | Strict scope control, prioritize MVP features only |

### 12.4 Dependencies

**External Dependencies:**
1. Apple Developer Program membership ($99/year)
2. Tailwind CSS CDN uptime
3. Font Awesome CDN uptime
4. Google Fonts CDN uptime
5. Xcode updates (must support latest iOS)

**Internal Dependencies:**
1. Design assets completion before implementation
2. Content writing (task descriptions, workout tips)
3. Testing devices available (multiple iPhone models)
4. Code signing certificates and provisioning profiles

---

## 13. Open Questions

### 13.1 Product Questions
1. Should we add push notifications for daily reminders?
2. What happens if user misses midnight reset (traveling, timezone change)?
3. Should stats have a maximum cap, or unlimited growth?
4. Should there be a tutorial/onboarding flow, or jump straight in?
5. How should we handle users who complete all tasks before noon?

### 13.2 Technical Questions
1. Should we bundle CSS/JS instead of CDN for true offline support?
2. Do we need data export/import for backup?
3. Should we implement data migration strategy for future versions?
4. How do we handle localStorage quota exceeded errors?
5. Should we add analytics (privacy-compliant)?

### 13.3 Design Questions
1. Should completed tasks show checkmark or disappear entirely?
2. Do we need a settings screen in MVP?
3. Should rank-up trigger full-screen celebration animation?
4. How many food categories should we support?
5. Should we add profile customization (avatar, username)?

### 13.4 Business Questions
1. When should we introduce premium features?
2. What's our user acquisition strategy?
3. Should we build a landing page / website?
4. Do we need a Discord/community for users?
5. When should we expand to Android?

---

## 14. Appendix

### 14.1 Glossary

| Term | Definition |
|------|------------|
| **Rank** | User's current level based on total stats (Unranked to Legendary) |
| **Stats** | Numerical values representing user progress (STR, END, INT, DIS) |
| **Task** | Daily action that rewards stats when completed |
| **Mission** | Long-term challenge with milestone rewards |
| **Streak** | Consecutive days with at least one completed task |
| **MVP** | Minimum Viable Product - initial version with core features |
| **CDN** | Content Delivery Network - external resource hosting |
| **localStorage** | Browser API for client-side data persistence |
| **WKWebView** | iOS framework for displaying web content in native apps |
| **Glass Morphism** | Design style with translucent, blurred backgrounds |

### 14.2 References

**Design Inspiration:**
- Habitica (gamification)
- Duolingo (streaks, progression)
- MyFitnessPal (nutrition tracking)
- StrongLifts (workout tracking)
- Forest (minimalist, engaging UI)

**Technical Documentation:**
- Apple Human Interface Guidelines
- WKWebView Documentation
- SwiftUI Documentation
- Web Storage API (localStorage)

### 14.3 Document History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | Oct 31, 2025 | Product Team | Initial PRD creation |

---

## 15. Approval

**Document Status**: Draft
**Review Date**: Pending
**Approval Date**: Pending

**Stakeholders:**
- [ ] Product Owner
- [ ] Engineering Lead
- [ ] Design Lead
- [ ] QA Lead
- [ ] Business Owner

---

**End of Document**

*For questions or feedback, contact: [Product Team]*

---

## Quick Reference Card

**Product:** Peruchito - Your Life RPG
**Platform:** iOS 15.0+
**Type:** Life gamification / habit tracking
**Architecture:** SwiftUI + WKWebView (hybrid)
**Storage:** localStorage (local only)
**Launch Target:** Q1 2026
**MVP Timeline:** 12 weeks

**Core Features:**
1. ✅ 9-rank progression system
2. ✅ 4 RPG stats (STR, END, INT, DIS)
3. ✅ 12+ daily tasks
4. ✅ Workout library (15 exercises, 3 splits)
5. ✅ Food scanner (33+ foods)
6. ✅ Weight tracking (weekly)
7. ✅ Streak system

**Success Metrics:**
- 85% task completion rate
- 50% Day 30 retention
- 4.5+ App Store rating
- 70% users reach Bronze rank in 2 weeks
