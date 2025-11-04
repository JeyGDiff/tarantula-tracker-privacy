# Privacy Policy for Tarantula Tracker

**Last Updated:** November 3, 2025

## Code-Verified Privacy Statement

This privacy policy is backed by verifiable technical implementation. We don't just claim to protect your privacy—our code proves it.

## Zero Data Collection - Verified

**Apple Privacy Manifest (PrivacyInfo.xcprivacy):**
```xml
<key>NSPrivacyTracking</key>
<false/>
<key>NSPrivacyCollectedDataTypes</key>
<array/>  <!-- Empty array = NO DATA COLLECTED -->
```

**Codebase Verification:**
- ❌ **No URLSession** - Zero network requests anywhere in the codebase
- ❌ **No URLRequest** - No HTTP/HTTPS calls of any kind
- ❌ **No Analytics SDKs** - No Firebase, Google Analytics, or any third-party tracking
- ❌ **No Cloud Services** - No iCloud, CloudKit, or external databases
- ❌ **No Advertising Networks** - No ad SDKs or tracking pixels
- ❌ **No Social Media SDKs** - No Facebook, Twitter, or social integrations
- ✅ **100% Local** - All data stored using SwiftData on your device only

## What the App Actually Does

### Local Data Storage Only

**Technology Used:** Apple's SwiftData framework (completely offline)

**Data Stored Locally (Item.swift):**
1. **Tarantula Records**
   - Name, scientific name, common name
   - Life stage, sex, classification, habitat type
   - Pre-molt state (boolean)
   
2. **Event Logs** (EventLog.swift)
   - Feeding dates and times
   - Molt dates and times
   - Custom event dates you create
   
3. **Photos** (Optional)
   - Stored in app's local container
   - Uses PHPickerViewController (read-only photo access)
   - Never uploaded anywhere

4. **User Preferences** (UserSettings.swift)
   - Theme selection
   - Feeding interval settings per life stage
   - Molt recovery delay settings
   - Notification preferences (on/off only)

**Code Reference:** See `tarantula_trackerApp.swift:10-12`
```swift
.modelContainer(for: [Tarantula.self, EventLog.self, Event.self])
```
This is SwiftData's local-only storage. No cloud configuration exists in the codebase.

## Permissions Requested

### Photo Library Access (Optional)
**Code:** `PHPickerViewController` used in TarantulaDetailView.swift
- **Purpose:** Select photos of your tarantulas
- **Scope:** Read-only access via PHPicker (no write access)
- **Storage:** Photos stored in app's local container
- **Network:** Photos never transmitted anywhere
- **Required:** No - app works fully without photos

**Permission String (project.pbxproj):**
```
"Access to your photo library is needed to add photos of your tarantulas 
for identification and record keeping."
```

### Notification Permissions (Optional)
**Code:** `UNUserNotificationCenter` in NotificationManager.swift
- **Purpose:** Local feeding reminders at 9:00 AM and molt predictions at 10:00 AM
- **Generated:** Locally on your device (no push notifications from servers)
- **Content:** Contains only your tarantula names and care information
- **Network:** Notifications never sent to or from external servers
- **Required:** No - app works fully without notifications

**Permission String (project.pbxproj):**
```
"Notifications are used to remind you about feeding schedules 
for your tarantulas."
```

### UserDefaults Access
**Reason Code:** CA92.1 (App preferences and settings)
- **Purpose:** Store app theme, feeding intervals, notification preferences
- **Scope:** Standard iOS UserDefaults (local only)
- **Network:** No synchronization with iCloud or external services

## What This App Does NOT Do

### Verified Absence of These Technologies:

**No Network Layer:**
```bash
# Codebase search results:
grep -r "URLSession" → No matches
grep -r "URLRequest" → No matches
grep -r "import Alamofire" → No matches
```

**No Analytics:**
```bash
grep -r "Firebase" → No matches
grep -r "Analytics" → No matches  
grep -r "Crashlytics" → No matches
grep -r "AppCenter" → No matches
```

**No Tracking:**
```bash
NSPrivacyTracking = false (PrivacyInfo.xcprivacy:6)
NSPrivacyTrackingDomains = [] (empty array)
```

**No Cloud Storage:**
```bash
grep -r "iCloud\|CloudKit\|NSUbiquitousKeyValueStore" → No matches
```

## Data Sharing & Transmission

**NONE.** The codebase contains:
- Zero server endpoints
- Zero API keys
- Zero cloud service configurations
- Zero third-party SDK integrations

The only data that leaves the app is when **you explicitly** choose to:
1. Export CSV files using the "Export CSV" button (SettingsView.swift:383-439)
2. Share via iOS Share Sheet (your choice of destination)

## Your Complete Control

### Data Location
- Stored in: `/var/mobile/Containers/Data/Application/[UUID]/Library/Application Support/default.store`
- Encrypted: Automatically by iOS when device is locked
- Backed up: Via iOS device backups (encrypted backups recommended)

### Data Deletion
- **Delete App:** Removes all data permanently (iOS deletes app container)
- **Delete Individual Records:** Delete tarantulas individually in-app
- **Clear All:** No bulk clear (intentional - prevents accidental data loss)

### Data Export
- **Format:** CSV (human-readable text)
- **Location:** Your choice via iOS Share Sheet
- **Content:** Only what you choose to export
- **Method:** File-based export (SettingsView.swift:383-439)

## Children's Privacy

This app:
- Collects NO personal information from anyone
- Stores ALL data locally (no collection = no COPPA concerns)
- Requires NO account creation
- Performs NO age verification (not needed - no data collected)

Safe for users of all ages.

## Technical Compliance

### GDPR Compliance
- **No Data Processing:** Data never leaves device = no processing
- **No Data Controller:** You are the sole controller of your data
- **No Data Transfers:** No cross-border transfers
- **Right to Deletion:** Delete app = complete data erasure
- **Right to Access:** Data visible in app at all times
- **Right to Portability:** CSV export functionality

### CCPA Compliance
- **No Sale of Data:** No data collected = nothing to sell
- **No Sharing:** Data stored locally only
- **No Third Parties:** Zero third-party integrations

### Apple Privacy Requirements
- **Privacy Manifest:** Included (PrivacyInfo.xcprivacy)
- **Privacy Nutrition Labels:** Accurate (no data collection)
- **Required Reason API:** UserDefaults (CA92.1), FileTimestamp (C617.1), SystemBootTime (35F9.1)

## Intellectual Property

Tarantula Tracker is **proprietary, closed-source software**. The source code is not publicly available. This privacy policy is verifiable through:
- Apple's App Review process
- Privacy manifest in the app bundle
- Network traffic analysis (shows zero network activity)

## Changes to This Policy

Updates will:
1. Increment "Last Updated" date
2. Be included in app updates (visible in version release notes)
3. Require continued use to constitute acceptance

We will never:
- Add data collection without explicit disclosure
- Change from local-only storage without your consent
- Introduce third-party services without notification

## Contact

**Privacy Questions:**
- Email: jeygbiz@gmail.com
- Subject: Tarantula Tracker Privacy Policy

**Response Time:** Within 48 hours

## Verification

Want to verify these claims?
1. **Monitor Network Traffic:** Use a network proxy - you'll see zero app traffic
2. **Check Privacy Manifest:** Open the .app bundle and read PrivacyInfo.xcprivacy
3. **Review App Permissions:** iOS Settings → Tarantula Tracker → see limited permissions
4. **Inspect Local Storage:** iOS File Manager shows only local database files

## Summary

**What We Collect:** NOTHING
**Where Data Goes:** NOWHERE (stays on your device)
**Who Sees Your Data:** ONLY YOU
**Network Requests:** ZERO
**Third Parties:** ZERO
**Your Control:** COMPLETE

This privacy policy is effective as of November 3, 2025 and applies to Tarantula Tracker version 1.1 and later.
