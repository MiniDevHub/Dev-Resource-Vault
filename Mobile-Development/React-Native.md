<div align="center">

# 📱 React Native - Build Native Mobile Apps! 📱

![React Native](https://img.shields.io/badge/React_Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![iOS](https://img.shields.io/badge/iOS-000000?style=for-the-badge&logo=ios&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)

### _Write once, run on iOS and Android_ 🚀

**Build truly native mobile apps with JavaScript and React!** ✨

</div>

---

## 📚 Table of Contents

- [🎯 What is React Native](#-what-is-react-native)
- [🚀 Getting Started](#-getting-started)
- [🧱 Core Components](#-core-components)
- [🎨 Styling in React Native](#-styling-in-react-native)
- [🧭 Navigation](#-navigation)
- [💾 State Management](#-state-management)
- [📡 Networking & APIs](#-networking--apis)
- [📦 Essential Libraries](#-essential-libraries)
- [🔧 Native Modules](#-native-modules)
- [🎯 Platform-Specific Code](#-platform-specific-code)
- [🐛 Debugging](#-debugging)
- [⚡ Performance Optimization](#-performance-optimization)
- [📲 Building & Deployment](#-building--deployment)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 What is React Native

</div>

### Understanding React Native 🌟

```

# ═══════════════════════════════════════════

# REACT NATIVE EXPLAINED

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ WHAT IS REACT NATIVE? ║
╚════════════════════════════════════════════════════════════╝

React Native:
─────────────────────────────────────────────────────────────
A framework for building native mobile apps using JavaScript
and React.

Key Points:
─────────────────────────────────────────────────────────────
✅ Created by Facebook (Meta)
✅ Write in JavaScript
✅ Uses React syntax
✅ Renders native components
✅ One codebase → iOS + Android
✅ Hot reloading
✅ Large ecosystem

How It Works:
─────────────────────────────────────────────────────────────

Your Code (JavaScript/React)
↓
JavaScript Core (JS Engine)
↓
Bridge (Communication Layer)
↓
Native Modules (iOS/Android)
↓
Native UI Components
↓
📱 Native App

Not a Hybrid App:
─────────────────────────────────────────────────────────────
❌ Not like Cordova/PhoneGap (WebView)
✅ Truly native components
✅ Native performance
✅ Native look and feel

╔════════════════════════════════════════════════════════════╗
║ REACT NATIVE vs ALTERNATIVES ║
╚════════════════════════════════════════════════════════════╝

React Native vs Flutter:
─────────────────────────────────────────────────────────────

React Native:
✅ JavaScript (huge ecosystem)
✅ React skills transfer
✅ Mature (2015)
✅ More third-party libraries
❌ Bridge can be bottleneck
❌ Platform-specific bugs

Flutter:
✅ Faster (no bridge)
✅ Beautiful UI out of box
✅ Single rendering engine
❌ Dart language (learning curve)
❌ Smaller ecosystem
❌ Newer (2017)

React Native vs Native:
─────────────────────────────────────────────────────────────

React Native:
✅ Faster development
✅ Code sharing (iOS + Android)
✅ JavaScript developers can build mobile
✅ Hot reload
❌ Slightly lower performance
❌ Platform limitations

Native (Swift/Kotlin):
✅ Best performance
✅ Full platform access
✅ Latest features first
❌ Separate codebases
❌ Slower development
❌ Need iOS + Android developers

React Native vs Ionic/Cordova:
─────────────────────────────────────────────────────────────

React Native:
✅ Native components
✅ Better performance
✅ Native feel

Ionic/Cordova:
✅ Web technologies
❌ WebView (not native)
❌ Performance issues
❌ Not native feel

╔════════════════════════════════════════════════════════════╗
║ WHEN TO USE REACT NATIVE ║
╚════════════════════════════════════════════════════════════╝

Perfect For:
─────────────────────────────────────────────────────────────
✅ Cross-platform apps
✅ MVPs (fast to market)
✅ Content-heavy apps
✅ Social media apps
✅ E-commerce apps
✅ Have React developers
✅ Need rapid iteration

Consider Native If:
─────────────────────────────────────────────────────────────
❌ Heavy animations/graphics
❌ Need absolute best performance
❌ Complex native features
❌ AR/VR applications
❌ Heavy camera/sensor usage

Success Stories:
─────────────────────────────────────────────────────────────
• Instagram
• Facebook
• Discord
• Shopify
• Uber Eats
• Bloomberg
• Walmart

╔════════════════════════════════════════════════════════════╗
║ EXPO vs REACT NATIVE CLI ║
╚════════════════════════════════════════════════════════════╝

Two Ways to Start:
─────────────────────────────────────────────────────────────

1. Expo (Managed Workflow)
2. React Native CLI (Bare Workflow)

Expo:
─────────────────────────────────────────────────────────────
✅ Easier to start
✅ No Xcode/Android Studio needed
✅ OTA updates
✅ Many built-in features
✅ Expo Go app for testing
❌ Limited native modules
❌ Larger app size
❌ Less control

React Native CLI:
─────────────────────────────────────────────────────────────
✅ Full control
✅ Any native module
✅ Smaller app size
✅ Custom native code
❌ More complex setup
❌ Need Xcode/Android Studio
❌ Harder to configure

Recommendation:
─────────────────────────────────────────────────────────────
Beginners: Start with Expo
Can always eject later if needed!

Experienced: React Native CLI if you need custom native code

```

---

<div align="center">

## 🚀 Getting Started

</div>

### Setup Your Environment 🛠️

```

# ═══════════════════════════════════════════

# SETUP & INSTALLATION

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ EXPO SETUP (EASIEST) ║
╚════════════════════════════════════════════════════════════╝

Prerequisites:
─────────────────────────────────────────────────────────────
• Node.js (14+)
• npm or yarn
• Expo Go app on phone

Step-by-Step:
─────────────────────────────────────────────────────────────

```

Expo setup:

```bash
# Install Expo CLI
npm install -g expo-cli

# Create new project
npx create-expo-app my-app

# Navigate to project
cd my-app

# Start development server
npx expo start

# Or
npm start

# Scan QR code with Expo Go app to view on phone
# Press 'i' for iOS simulator (Mac only)
# Press 'a' for Android emulator
```

```
╔════════════════════════════════════════════════════════════╗
║                   REACT NATIVE CLI SETUP                   ║
╚════════════════════════════════════════════════════════════╝

Prerequisites:
─────────────────────────────────────────────────────────────
• Node.js (14+)
• Xcode (Mac, for iOS)
• Android Studio (for Android)
• Java JDK
• CocoaPods (Mac)

macOS Setup (iOS + Android):
─────────────────────────────────────────────────────────────
```

React Native CLI setup:

```bash
# Install Homebrew (if not installed)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Node and Watchman
brew install node
brew install watchman

# Install CocoaPods
sudo gem install cocoapods

# Install Xcode from App Store
# Open Xcode, install additional components

# Install Android Studio
# Download from: https://developer.android.com/studio

# Configure Android SDK
# Add to ~/.zshrc or ~/.bash_profile:
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/platform-tools

# Create new project
npx react-native@latest init MyApp

# Navigate to project
cd MyApp

# Install iOS dependencies (Mac only)
cd ios && pod install && cd ..

# Run on iOS (Mac only)
npx react-native run-ios

# Run on Android
npx react-native run-android
```

Windows Setup (Android only):

```bash
# Install Node.js from nodejs.org

# Install Android Studio
# Download from: https://developer.android.com/studio

# Configure Android SDK
# Add to Environment Variables:
ANDROID_HOME = C:\Users\YourName\AppData\Local\Android\Sdk

# Add to Path:
%ANDROID_HOME%\platform-tools
%ANDROID_HOME%\emulator

# Create new project
npx react-native@latest init MyApp

# Run on Android
npx react-native run-android
```

```
╔════════════════════════════════════════════════════════════╗
║                   PROJECT STRUCTURE                        ║
╚════════════════════════════════════════════════════════════╝

Typical Structure:
─────────────────────────────────────────────────────────────
```

```
MyApp/
├── android/              # Android native code
├── ios/                  # iOS native code
├── src/                  # Your app code
│   ├── components/       # Reusable components
│   ├── screens/          # Screen components
│   ├── navigation/       # Navigation setup
│   ├── services/         # API calls, utilities
│   ├── hooks/            # Custom hooks
│   ├── context/          # Context providers
│   ├── assets/           # Images, fonts
│   └── styles/           # Shared styles
├── App.js                # Main entry point
├── package.json
└── README.md
```

```
╔════════════════════════════════════════════════════════════╗
║                   FIRST APP                                ║
╚════════════════════════════════════════════════════════════╝
```

Hello World App:

```javascript
// App.js
import React, { useState } from "react";
import {
  SafeAreaView,
  StyleSheet,
  Text,
  View,
  TextInput,
  TouchableOpacity,
  ScrollView,
  StatusBar,
} from "react-native";

export default function App() {
  const [name, setName] = useState("");
  const [greetings, setGreetings] = useState([]);

  const addGreeting = () => {
    if (name.trim()) {
      setGreetings([...greetings, `Hello, ${name}!`]);
      setName("");
    }
  };

  return (
    <SafeAreaView style={styles.container}>
      <StatusBar barStyle="dark-content" />

      <View style={styles.header}>
        <Text style={styles.title}>React Native App</Text>
      </View>

      <View style={styles.inputContainer}>
        <TextInput
          style={styles.input}
          placeholder="Enter your name"
          value={name}
          onChangeText={setName}
        />
        <TouchableOpacity style={styles.button} onPress={addGreeting}>
          <Text style={styles.buttonText}>Say Hello</Text>
        </TouchableOpacity>
      </View>

      <ScrollView style={styles.greetingsList}>
        {greetings.map((greeting, index) => (
          <View key={index} style={styles.greetingItem}>
            <Text style={styles.greetingText}>{greeting}</Text>
          </View>
        ))}
      </ScrollView>
    </SafeAreaView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#f5f5f5",
  },
  header: {
    backgroundColor: "#2196F3",
    padding: 20,
    alignItems: "center",
  },
  title: {
    fontSize: 24,
    fontWeight: "bold",
    color: "white",
  },
  inputContainer: {
    padding: 20,
    backgroundColor: "white",
  },
  input: {
    borderWidth: 1,
    borderColor: "#ddd",
    padding: 12,
    borderRadius: 8,
    fontSize: 16,
    marginBottom: 12,
  },
  button: {
    backgroundColor: "#2196F3",
    padding: 15,
    borderRadius: 8,
    alignItems: "center",
  },
  buttonText: {
    color: "white",
    fontSize: 16,
    fontWeight: "bold",
  },
  greetingsList: {
    flex: 1,
    padding: 20,
  },
  greetingItem: {
    backgroundColor: "white",
    padding: 15,
    borderRadius: 8,
    marginBottom: 10,
    shadowColor: "#000",
    shadowOffset: { width: 0, height: 2 },
    shadowOpacity: 0.1,
    shadowRadius: 4,
    elevation: 3,
  },
  greetingText: {
    fontSize: 16,
    color: "#333",
  },
});
```

---

<div align="center">

## 🧱 Core Components

</div>

### Essential React Native Components 📦

```
# ═══════════════════════════════════════════
# CORE COMPONENTS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   VIEW & TEXT                              ║
╚════════════════════════════════════════════════════════════╝

View:
─────────────────────────────────────────────────────────────
The fundamental container component (like <div>)
```

View component:

```javascript
import { View, Text, StyleSheet } from "react-native";

function MyComponent() {
  return (
    <View style={styles.container}>
      <View style={styles.box}>
        <Text>Box 1</Text>
      </View>
      <View style={styles.box}>
        <Text>Box 2</Text>
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    flexDirection: "row",
    justifyContent: "space-around",
    alignItems: "center",
  },
  box: {
    width: 100,
    height: 100,
    backgroundColor: "#2196F3",
    justifyContent: "center",
    alignItems: "center",
  },
});
```

Text component:

```javascript
<Text style={styles.text}>
  Hello World
</Text>

<Text
  numberOfLines={2}
  ellipsizeMode="tail"
  style={styles.text}
>
  This is a long text that will be truncated after two lines
</Text>

<Text onPress={() => alert('Clicked!')}>
  Clickable text
</Text>

<Text>
  You can <Text style={{ fontWeight: 'bold' }}>nest</Text> text
</Text>
```

```
╔════════════════════════════════════════════════════════════╗
║                   BUTTONS & TOUCHABLES                     ║
╚════════════════════════════════════════════════════════════╝
```

Touchable components:

```javascript
import {
  TouchableOpacity,
  TouchableHighlight,
  TouchableWithoutFeedback,
  Pressable
} from 'react-native';

// TouchableOpacity (most common - reduces opacity on press)
<TouchableOpacity
  onPress={() => console.log('Pressed')}
  style={styles.button}
>
  <Text>Press Me</Text>
</TouchableOpacity>

// TouchableHighlight (shows underlay color)
<TouchableHighlight
  onPress={() => console.log('Pressed')}
  underlayColor="#DDDDDD"
  style={styles.button}
>
  <Text>Press Me</Text>
</TouchableHighlight>

// Pressable (new, more flexible)
<Pressable
  onPress={() => console.log('Pressed')}
  onLongPress={() => console.log('Long pressed')}
  style={({ pressed }) => [
    styles.button,
    pressed && styles.buttonPressed
  ]}
>
  {({ pressed }) => (
    <Text>{pressed ? 'Pressed!' : 'Press Me'}</Text>
  )}
</Pressable>

// Button (simple, platform-styled)
import { Button } from 'react-native';

<Button
  title="Press Me"
  onPress={() => console.log('Pressed')}
  color="#2196F3"
/>
```

```
╔════════════════════════════════════════════════════════════╗
║                   IMAGES                                   ║
╚════════════════════════════════════════════════════════════╝
```

Image component:

```javascript
import { Image } from 'react-native';

// Local image
<Image
  source={require('./assets/logo.png')}
  style={{ width: 200, height: 200 }}
/>

// Remote image
<Image
  source={{ uri: 'https://example.com/image.jpg' }}
  style={{ width: 200, height: 200 }}
/>

// With loading
<Image
  source={{ uri: 'https://example.com/image.jpg' }}
  style={styles.image}
  resizeMode="cover" // cover, contain, stretch, center
  onLoad={() => console.log('Loaded')}
  onError={() => console.log('Error')}
/>

// Background image
import { ImageBackground } from 'react-native';

<ImageBackground
  source={require('./assets/background.jpg')}
  style={styles.background}
>
  <Text>Content here</Text>
</ImageBackground>
```

```
╔════════════════════════════════════════════════════════════╗
║                   SCROLLVIEW & FLATLIST                    ║
╚════════════════════════════════════════════════════════════╝
```

ScrollView:

```javascript
import { ScrollView } from 'react-native';

// Basic ScrollView
<ScrollView>
  <Text>Item 1</Text>
  <Text>Item 2</Text>
  {/* More items */}
</ScrollView>

// Horizontal scroll
<ScrollView
  horizontal
  showsHorizontalScrollIndicator={false}
>
  <View style={styles.card} />
  <View style={styles.card} />
  <View style={styles.card} />
</ScrollView>

// With refresh
<ScrollView
  refreshControl={
    <RefreshControl
      refreshing={refreshing}
      onRefresh={onRefresh}
    />
  }
>
  {/* Content */}
</ScrollView>
```

FlatList (for large lists):

```javascript
import { FlatList } from 'react-native';

const DATA = [
  { id: '1', title: 'Item 1' },
  { id: '2', title: 'Item 2' },
  { id: '3', title: 'Item 3' },
];

// Basic FlatList
<FlatList
  data={DATA}
  renderItem={({ item }) => (
    <View style={styles.item}>
      <Text>{item.title}</Text>
    </View>
  )}
  keyExtractor={item => item.id}
/>

// With all features
<FlatList
  data={data}
  renderItem={({ item, index }) => (
    <TouchableOpacity onPress={() => onSelect(item)}>
      <View style={styles.item}>
        <Text>{item.title}</Text>
      </View>
    </TouchableOpacity>
  )}
  keyExtractor={item => item.id}

  // Separators
  ItemSeparatorComponent={() => <View style={styles.separator} />}

  // Empty state
  ListEmptyComponent={() => (
    <Text>No items found</Text>
  )}

  // Headers/Footers
  ListHeaderComponent={() => <Text>Header</Text>}
  ListFooterComponent={() => <Text>Footer</Text>}

  // Pull to refresh
  refreshing={refreshing}
  onRefresh={onRefresh}

  // Infinite scroll
  onEndReached={loadMore}
  onEndReachedThreshold={0.5}

  // Performance
  removeClippedSubviews={true}
  maxToRenderPerBatch={10}
  windowSize={5}
/>

// Horizontal FlatList
<FlatList
  data={data}
  horizontal
  renderItem={({ item }) => (
    <View style={styles.card}>
      <Text>{item.title}</Text>
    </View>
  )}
  keyExtractor={item => item.id}
  showsHorizontalScrollIndicator={false}
/>
```

```
╔════════════════════════════════════════════════════════════╗
║                   TEXTINPUT                                ║
╚════════════════════════════════════════════════════════════╝
```

TextInput component:

```javascript
import { TextInput } from 'react-native';

const [text, setText] = useState('');
const [password, setPassword] = useState('');

// Basic input
<TextInput
  style={styles.input}
  placeholder="Enter text"
  value={text}
  onChangeText={setText}
/>

// Password input
<TextInput
  style={styles.input}
  placeholder="Password"
  value={password}
  onChangeText={setPassword}
  secureTextEntry
/>

// Email input
<TextInput
  style={styles.input}
  placeholder="Email"
  keyboardType="email-address"
  autoCapitalize="none"
  autoCorrect={false}
/>

// Multiline
<TextInput
  style={styles.textArea}
  placeholder="Enter description"
  multiline
  numberOfLines={4}
  textAlignVertical="top"
/>

// With validation
<TextInput
  style={[
    styles.input,
    error && styles.inputError
  ]}
  placeholder="Username"
  value={username}
  onChangeText={setUsername}
  onBlur={validateUsername}
/>
```

```
╔════════════════════════════════════════════════════════════╗
║                   MODAL & ALERT                            ║
╚════════════════════════════════════════════════════════════╝
```

Modal:

```javascript
import { Modal } from "react-native";

const [visible, setVisible] = useState(false);

<Modal
  visible={visible}
  animationType="slide" // slide, fade, none
  transparent={true}
  onRequestClose={() => setVisible(false)}
>
  <View style={styles.modalOverlay}>
    <View style={styles.modalContent}>
      <Text>Modal Content</Text>
      <TouchableOpacity onPress={() => setVisible(false)}>
        <Text>Close</Text>
      </TouchableOpacity>
    </View>
  </View>
</Modal>;

const styles = StyleSheet.create({
  modalOverlay: {
    flex: 1,
    backgroundColor: "rgba(0,0,0,0.5)",
    justifyContent: "center",
    alignItems: "center",
  },
  modalContent: {
    backgroundColor: "white",
    padding: 20,
    borderRadius: 10,
    width: "80%",
  },
});
```

Alert:

```javascript
import { Alert } from "react-native";

// Simple alert
Alert.alert("Title", "Message");

// With buttons
Alert.alert("Delete Item", "Are you sure you want to delete this item?", [
  {
    text: "Cancel",
    style: "cancel",
  },
  {
    text: "Delete",
    onPress: () => console.log("Deleted"),
    style: "destructive",
  },
]);

// With input (iOS only)
Alert.prompt(
  "Enter Name",
  "Please enter your name",
  [
    {
      text: "Cancel",
      style: "cancel",
    },
    {
      text: "OK",
      onPress: (name) => console.log("Name:", name),
    },
  ],
  "plain-text",
  "",
  "default"
);
```

```
╔════════════════════════════════════════════════════════════╗
║                   ACTIVITYINDICATOR                        ║
╚════════════════════════════════════════════════════════════╝
```

Loading indicator:

```javascript
import { ActivityIndicator } from "react-native";

// Simple loading
<ActivityIndicator size="large" color="#2196F3" />;

// Full screen loading
{
  loading && (
    <View style={styles.loadingOverlay}>
      <ActivityIndicator size="large" color="#2196F3" />
      <Text style={styles.loadingText}>Loading...</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  loadingOverlay: {
    position: "absolute",
    top: 0,
    left: 0,
    right: 0,
    bottom: 0,
    backgroundColor: "rgba(0,0,0,0.5)",
    justifyContent: "center",
    alignItems: "center",
  },
  loadingText: {
    marginTop: 10,
    color: "white",
    fontSize: 16,
  },
});
```

---

<div align="center">

## 🎨 Styling in React Native

</div>

### Style Your Components 💅

```
# ═══════════════════════════════════════════
# STYLING IN REACT NATIVE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   STYLESHEET                               ║
╚════════════════════════════════════════════════════════════╝

No CSS - Use JavaScript Objects:
─────────────────────────────────────────────────────────────
```

Basic styling:

```javascript
import { StyleSheet } from 'react-native';

// Using StyleSheet (recommended - optimized)
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#f5f5f5',
    padding: 20,
  },
  text: {
    fontSize: 16,
    color: '#333',
    fontWeight: 'bold',
  },
  button: {
    backgroundColor: '#2196F3',
    padding: 15,
    borderRadius: 8,
    alignItems: 'center',
  },
});

// Usage
<View style={styles.container}>
  <Text style={styles.text}>Hello</Text>
</View>

// Inline styles (not recommended)
<View style={{ flex: 1, backgroundColor: 'red' }}>
  <Text style={{ fontSize: 20 }}>Text</Text>
</View>

// Multiple styles
<Text style={[styles.text, styles.bold, { color: 'red' }]}>
  Text
</Text>

// Conditional styles
<View style={[
  styles.button,
  disabled && styles.buttonDisabled
]}>
  <Text>Button</Text>
</View>
```

```
╔════════════════════════════════════════════════════════════╗
║                   FLEXBOX (MAIN LAYOUT SYSTEM)             ║
╚════════════════════════════════════════════════════════════╝

Flexbox in React Native:
─────────────────────────────────────────────────────────────
• Default: flexDirection: 'column' (unlike web's 'row')
• All containers are flex by default
```

Flexbox examples:

```javascript
// Column layout (default)
<View style={{ flex: 1, flexDirection: 'column' }}>
  <View style={{ flex: 1, backgroundColor: 'red' }} />
  <View style={{ flex: 2, backgroundColor: 'blue' }} />
  <View style={{ flex: 1, backgroundColor: 'green' }} />
</View>

// Row layout
<View style={{ flex: 1, flexDirection: 'row' }}>
  <View style={{ flex: 1, backgroundColor: 'red' }} />
  <View style={{ flex: 1, backgroundColor: 'blue' }} />
  <View style={{ flex: 1, backgroundColor: 'green' }} />
</View>

// Center content
<View style={{
  flex: 1,
  justifyContent: 'center', // vertical
  alignItems: 'center', // horizontal
}}>
  <Text>Centered</Text>
</View>

// Space between
<View style={{
  flex: 1,
  flexDirection: 'row',
  justifyContent: 'space-between',
  alignItems: 'center',
}}>
  <Text>Left</Text>
  <Text>Right</Text>
</View>

// Flex wrap
<View style={{
  flexDirection: 'row',
  flexWrap: 'wrap',
}}>
  <View style={{ width: 100, height: 100, backgroundColor: 'red' }} />
  <View style={{ width: 100, height: 100, backgroundColor: 'blue' }} />
  <View style={{ width: 100, height: 100, backgroundColor: 'green' }} />
</View>
```

```
╔════════════════════════════════════════════════════════════╗
║                   DIMENSIONS & RESPONSIVE                  ║
╚════════════════════════════════════════════════════════════╝
```

Responsive design:

```javascript
import { Dimensions, PixelRatio, Platform } from "react-native";

// Get screen dimensions
const { width, height } = Dimensions.get("window");
const screenWidth = Dimensions.get("screen").width;

// Responsive width
const responsiveWidth = (percent) => {
  const screenWidth = Dimensions.get("window").width;
  return (percent / 100) * screenWidth;
};

// Usage
<View style={{ width: responsiveWidth(80) }}>{/* 80% of screen width */}</View>;

// Responsive font size
const responsiveFontSize = (size) => {
  const scale = width / 375; // iPhone 8 width as base
  const newSize = size * scale;
  return Math.round(PixelRatio.roundToNearestPixel(newSize));
};

// Platform-specific styles
const styles = StyleSheet.create({
  container: {
    padding: Platform.OS === "ios" ? 20 : 16,
  },
  text: {
    fontSize: Platform.select({
      ios: 16,
      android: 14,
      default: 16,
    }),
  },
});

// Listen for orientation changes
useEffect(() => {
  const subscription = Dimensions.addEventListener("change", ({ window }) => {
    setDimensions(window);
  });

  return () => subscription?.remove();
}, []);
```

```
╔════════════════════════════════════════════════════════════╗
║                   SHADOWS & ELEVATION                      ║
╚════════════════════════════════════════════════════════════╝
```

Shadows (different on iOS/Android):

```javascript
const styles = StyleSheet.create({
  card: {
    backgroundColor: "white",
    borderRadius: 8,
    padding: 15,
    margin: 10,

    // iOS shadows
    ...Platform.select({
      ios: {
        shadowColor: "#000",
        shadowOffset: { width: 0, height: 2 },
        shadowOpacity: 0.25,
        shadowRadius: 3.84,
      },
      android: {
        elevation: 5,
      },
    }),
  },

  // Alternative: combine both
  cardWithShadow: {
    backgroundColor: "white",
    borderRadius: 8,
    padding: 15,

    // iOS
    shadowColor: "#000",
    shadowOffset: { width: 0, height: 2 },
    shadowOpacity: 0.25,
    shadowRadius: 3.84,

    // Android
    elevation: 5,
  },
});
```

```
╔════════════════════════════════════════════════════════════╗
║                   STYLED COMPONENTS (LIBRARY)              ║
╚════════════════════════════════════════════════════════════╝
```

Using styled-components:

```javascript
// Install: npm install styled-components
import styled from "styled-components/native";

const Container = styled.View`
  flex: 1;
  background-color: #f5f5f5;
  padding: 20px;
`;

const Title = styled.Text`
  font-size: 24px;
  font-weight: bold;
  color: #333;
  margin-bottom: 10px;
`;

const Button = styled.TouchableOpacity`
  background-color: #2196f3;
  padding: 15px;
  border-radius: 8px;
  align-items: center;
`;

const ButtonText = styled.Text`
  color: white;
  font-size: 16px;
  font-weight: bold;
`;

// Usage
function MyComponent() {
  return (
    <Container>
      <Title>Hello World</Title>
      <Button onPress={() => console.log("Pressed")}>
        <ButtonText>Press Me</ButtonText>
      </Button>
    </Container>
  );
}

// With props
const Box = styled.View`
  width: 100px;
  height: 100px;
  background-color: ${(props) => props.color || "blue"};
`;

<Box color="red" />;
```

---

<div align="center">

## 🧭 Navigation

</div>

### Navigate Between Screens 🗺️

```
# ═══════════════════════════════════════════
# REACT NAVIGATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   REACT NAVIGATION SETUP                   ║
╚════════════════════════════════════════════════════════════╝

Installation:
─────────────────────────────────────────────────────────────
```

Install React Navigation:

```bash
# Core
npm install @react-navigation/native

# Dependencies
npm install react-native-screens react-native-safe-area-context

# Stack Navigator
npm install @react-navigation/stack
npm install react-native-gesture-handler

# Bottom Tabs
npm install @react-navigation/bottom-tabs

# Drawer Navigator
npm install @react-navigation/drawer
npm install react-native-reanimated

# For iOS
cd ios && pod install && cd ..
```

```
╔════════════════════════════════════════════════════════════╗
║                   STACK NAVIGATOR                          ║
╚════════════════════════════════════════════════════════════╝
```

Stack Navigation:

```javascript
// App.js
import React from "react";
import { NavigationContainer } from "@react-navigation/native";
import { createStackNavigator } from "@react-navigation/stack";
import HomeScreen from "./screens/HomeScreen";
import DetailsScreen from "./screens/DetailsScreen";

const Stack = createStackNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator
        initialRouteName="Home"
        screenOptions={{
          headerStyle: { backgroundColor: "#2196F3" },
          headerTintColor: "#fff",
          headerTitleStyle: { fontWeight: "bold" },
        }}
      >
        <Stack.Screen
          name="Home"
          component={HomeScreen}
          options={{ title: "My Home" }}
        />
        <Stack.Screen
          name="Details"
          component={DetailsScreen}
          options={({ route }) => ({ title: route.params.name })}
        />
      </Stack.Navigator>
    </NavigationContainer>
  );
}

// HomeScreen.js
function HomeScreen({ navigation }) {
  return (
    <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
      <Text>Home Screen</Text>
      <Button
        title="Go to Details"
        onPress={() =>
          navigation.navigate("Details", {
            itemId: 86,
            name: "Detail Screen",
          })
        }
      />
    </View>
  );
}

// DetailsScreen.js
function DetailsScreen({ route, navigation }) {
  const { itemId, name } = route.params;

  return (
    <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
      <Text>Details Screen</Text>
      <Text>itemId: {itemId}</Text>
      <Button title="Go back" onPress={() => navigation.goBack()} />
      <Button title="Go to Home" onPress={() => navigation.navigate("Home")} />
    </View>
  );
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   BOTTOM TAB NAVIGATOR                     ║
╚════════════════════════════════════════════════════════════╝
```

Tab Navigation:

```javascript
import { createBottomTabNavigator } from "@react-navigation/bottom-tabs";
import { Ionicons } from "@expo/vector-icons";

const Tab = createBottomTabNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Tab.Navigator
        screenOptions={({ route }) => ({
          tabBarIcon: ({ focused, color, size }) => {
            let iconName;

            if (route.name === "Home") {
              iconName = focused ? "home" : "home-outline";
            } else if (route.name === "Settings") {
              iconName = focused ? "settings" : "settings-outline";
            }

            return <Ionicons name={iconName} size={size} color={color} />;
          },
          tabBarActiveTintColor: "#2196F3",
          tabBarInactiveTintColor: "gray",
        })}
      >
        <Tab.Screen name="Home" component={HomeScreen} />
        <Tab.Screen name="Settings" component={SettingsScreen} />
      </Tab.Navigator>
    </NavigationContainer>
  );
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   DRAWER NAVIGATOR                         ║
╚════════════════════════════════════════════════════════════╝
```

Drawer Navigation:

```javascript
import { createDrawerNavigator } from "@react-navigation/drawer";

const Drawer = createDrawerNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Drawer.Navigator
        initialRouteName="Home"
        screenOptions={{
          drawerActiveTintColor: "#2196F3",
          drawerItemStyle: { marginVertical: 5 },
        }}
      >
        <Drawer.Screen
          name="Home"
          component={HomeScreen}
          options={{
            drawerIcon: ({ color, size }) => (
              <Ionicons name="home-outline" size={size} color={color} />
            ),
          }}
        />
        <Drawer.Screen name="Profile" component={ProfileScreen} />
        <Drawer.Screen name="Settings" component={SettingsScreen} />
      </Drawer.Navigator>
    </NavigationContainer>
  );
}

// Open drawer
function HomeScreen({ navigation }) {
  return <Button onPress={() => navigation.openDrawer()} title="Open Drawer" />;
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   NESTED NAVIGATORS                        ║
╚════════════════════════════════════════════════════════════╝
```

Combining navigators:

```javascript
// Tab Navigator with Stack Navigators
function HomeStack() {
  return (
    <Stack.Navigator>
      <Stack.Screen name="Home" component={HomeScreen} />
      <Stack.Screen name="Details" component={DetailsScreen} />
    </Stack.Navigator>
  );
}

function SettingsStack() {
  return (
    <Stack.Navigator>
      <Stack.Screen name="Settings" component={SettingsScreen} />
      <Stack.Screen name="Profile" component={ProfileScreen} />
    </Stack.Navigator>
  );
}

export default function App() {
  return (
    <NavigationContainer>
      <Tab.Navigator>
        <Tab.Screen name="HomeTab" component={HomeStack} />
        <Tab.Screen name="SettingsTab" component={SettingsStack} />
      </Tab.Navigator>
    </NavigationContainer>
  );
}
```

---

<div align="center">

## 💾 State Management

</div>

### Manage App State 🗂️

```
# ═══════════════════════════════════════════
# STATE MANAGEMENT
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CONTEXT API                              ║
╚════════════════════════════════════════════════════════════╝

Built-in React Context:
─────────────────────────────────────────────────────────────
```

Context example:

```javascript
// UserContext.js
import React, { createContext, useState, useContext } from "react";

const UserContext = createContext();

export function UserProvider({ children }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(false);

  const login = async (email, password) => {
    setLoading(true);
    try {
      // API call
      const userData = await authAPI.login(email, password);
      setUser(userData);
    } catch (error) {
      console.error(error);
    } finally {
      setLoading(false);
    }
  };

  const logout = () => {
    setUser(null);
  };

  return (
    <UserContext.Provider value={{ user, loading, login, logout }}>
      {children}
    </UserContext.Provider>
  );
}

export function useUser() {
  return useContext(UserContext);
}

// App.js
export default function App() {
  return (
    <UserProvider>
      <NavigationContainer>{/* Your app */}</NavigationContainer>
    </UserProvider>
  );
}

// Usage in components
function HomeScreen() {
  const { user, logout } = useUser();

  return (
    <View>
      <Text>Welcome, {user.name}!</Text>
      <Button title="Logout" onPress={logout} />
    </View>
  );
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   REDUX TOOLKIT                            ║
╚════════════════════════════════════════════════════════════╝

Installation:
─────────────────────────────────────────────────────────────
```

Redux Toolkit:

```bash
npm install @reduxjs/toolkit react-redux
```

```javascript
// store/store.js
import { configureStore } from '@reduxjs/toolkit';
import userReducer from './userSlice';

export const store = configureStore({
  reducer: {
    user: userReducer,
  },
});

// store/userSlice.js
import { createSlice, createAsyncThunk } from '@reduxjs/toolkit';

export const fetchUser = createAsyncThunk(
  'user/fetchUser',
  async (userId) => {
    const response = await fetch(`/api/users/${userId}`);
    return response.json();
  }
);

const userSlice = createSlice({
  name: 'user',
  initialState: {
    data: null,
    loading: false,
    error: null,
  },
  reducers: {
    setUser: (state, action) => {
      state.data = action.payload;
    },
    logout: (state) => {
      state.data = null;
    },
  },
  extraReducers: (builder) => {
    builder
      .addCase(fetchUser.pending, (state) => {
        state.loading = true;
      })
      .addCase(fetchUser.fulfilled, (state, action) => {
        state.loading = false;
        state.data = action.payload;
      })
      .addCase(fetchUser.rejected, (state, action) => {
        state.loading = false;
        state.error = action.error.message;
      });
  },
});

export const { setUser, logout } = userSlice.actions;
export default userSlice.reducer;

// App.js
import { Provider } from 'react-redux';
import { store } from './store/store';

export default function App() {
  return (
    <Provider store={store}>
      <NavigationContainer>
        {/* Your app */}
      </NavigationContainer>
    </Provider>
  );
}

// Usage in components
import { useSelector, useDispatch } from 'react-redux';
import { fetchUser, logout } from './store/userSlice';

function HomeScreen() {
  const dispatch = useDispatch();
  const { data: user, loading } = useSelector((state) => state.user);

  useEffect(() => {
    dispatch(fetchUser(123));
  }, []);

  if (loading) return <ActivityIndicator />;

  return (
    <View>
      <Text>Welcome, {user?.name}!</Text>
      <Button title="Logout" onPress={() => dispatch(logout())} />
    </View>
  );
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   ZUSTAND (SIMPLE ALTERNATIVE)             ║
╚════════════════════════════════════════════════════════════╝
```

Zustand:

```bash
npm install zustand
```

```javascript
// store/useStore.js
import { create } from "zustand";

export const useStore = create((set) => ({
  user: null,
  loading: false,

  setUser: (user) => set({ user }),

  fetchUser: async (userId) => {
    set({ loading: true });
    try {
      const response = await fetch(`/api/users/${userId}`);
      const data = await response.json();
      set({ user: data, loading: false });
    } catch (error) {
      set({ loading: false });
    }
  },

  logout: () => set({ user: null }),
}));

// Usage
function HomeScreen() {
  const { user, loading, fetchUser, logout } = useStore();

  useEffect(() => {
    fetchUser(123);
  }, []);

  return (
    <View>
      <Text>Welcome, {user?.name}!</Text>
      <Button title="Logout" onPress={logout} />
    </View>
  );
}
```

---

<div align="center">

## 📡 Networking & APIs

</div>

### Fetch Data from APIs 🌐

```
# ═══════════════════════════════════════════
# NETWORKING & APIs
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   FETCH API                                ║
╚════════════════════════════════════════════════════════════╝
```

Basic fetch:

```javascript
// GET request
async function fetchData() {
  try {
    const response = await fetch("https://api.example.com/data");
    const data = await response.json();
    return data;
  } catch (error) {
    console.error("Error:", error);
  }
}

// POST request
async function postData(data) {
  try {
    const response = await fetch("https://api.example.com/data", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(data),
    });
    const result = await response.json();
    return result;
  } catch (error) {
    console.error("Error:", error);
  }
}

// With authentication
async function fetchWithAuth() {
  const token = await AsyncStorage.getItem("token");

  const response = await fetch("https://api.example.com/protected", {
    headers: {
      Authorization: `Bearer ${token}`,
    },
  });

  return response.json();
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   AXIOS                                    ║
╚════════════════════════════════════════════════════════════╝
```

Axios example:

```bash
npm install axios
```

```javascript
import axios from "axios";

// Create instance
const api = axios.create({
  baseURL: "https://api.example.com",
  timeout: 10000,
});

// Add interceptor for auth
api.interceptors.request.use(
  async (config) => {
    const token = await AsyncStorage.getItem("token");
    if (token) {
      config.headers.Authorization = `Bearer ${token}`;
    }
    return config;
  },
  (error) => Promise.reject(error)
);

// GET
const fetchData = async () => {
  try {
    const response = await api.get("/users");
    return response.data;
  } catch (error) {
    console.error(error);
  }
};

// POST
const createUser = async (userData) => {
  try {
    const response = await api.post("/users", userData);
    return response.data;
  } catch (error) {
    console.error(error);
  }
};

// PUT
const updateUser = async (id, userData) => {
  try {
    const response = await api.put(`/users/${id}`, userData);
    return response.data;
  } catch (error) {
    console.error(error);
  }
};

// DELETE
const deleteUser = async (id) => {
  try {
    await api.delete(`/users/${id}`);
  } catch (error) {
    console.error(error);
  }
};
```

```
╔════════════════════════════════════════════════════════════╗
║                   REACT QUERY                              ║
╚════════════════════════════════════════════════════════════╝
```

React Query (TanStack Query):

```bash
npm install @tanstack/react-query
```

```javascript
import {
  QueryClient,
  QueryClientProvider,
  useQuery,
  useMutation,
} from "@tanstack/react-query";

// Setup
const queryClient = new QueryClient();

export default function App() {
  return (
    <QueryClientProvider client={queryClient}>
      {/* Your app */}
    </QueryClientProvider>
  );
}

// Usage
function UsersScreen() {
  // Fetch data
  const { data, isLoading, error, refetch } = useQuery({
    queryKey: ["users"],
    queryFn: async () => {
      const response = await fetch("https://api.example.com/users");
      return response.json();
    },
  });

  // Mutation
  const mutation = useMutation({
    mutationFn: async (newUser) => {
      const response = await fetch("https://api.example.com/users", {
        method: "POST",
        body: JSON.stringify(newUser),
      });
      return response.json();
    },
    onSuccess: () => {
      // Refetch users after creating
      queryClient.invalidateQueries({ queryKey: ["users"] });
    },
  });

  if (isLoading) return <ActivityIndicator />;
  if (error) return <Text>Error: {error.message}</Text>;

  return (
    <FlatList
      data={data}
      renderItem={({ item }) => <Text>{item.name}</Text>}
      refreshing={isLoading}
      onRefresh={refetch}
    />
  );
}
```

---

<div align="center">

## 📦 Essential Libraries

</div>

### Must-Have React Native Libraries 🎁

```
# ═══════════════════════════════════════════
# ESSENTIAL LIBRARIES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   TOP LIBRARIES                            ║
╚════════════════════════════════════════════════════════════╝
```

| Library                          | Purpose         | Installation                                            |
| -------------------------------- | --------------- | ------------------------------------------------------- |
| **React Navigation**             | Navigation      | `npm install @react-navigation/native`                  |
| **Axios**                        | HTTP requests   | `npm install axios`                                     |
| **React Query**                  | Data fetching   | `npm install @tanstack/react-query`                     |
| **AsyncStorage**                 | Local storage   | `npm install @react-native-async-storage/async-storage` |
| **React Native Paper**           | UI components   | `npm install react-native-paper`                        |
| **NativeBase**                   | UI components   | `npm install native-base`                               |
| **React Native Vector Icons**    | Icons           | `npm install react-native-vector-icons`                 |
| **React Native Image Picker**    | Image selection | `npm install react-native-image-picker`                 |
| **React Native Camera**          | Camera access   | `npm install react-native-camera`                       |
| **React Native Maps**            | Maps            | `npm install react-native-maps`                         |
| **React Native Gesture Handler** | Gestures        | `npm install react-native-gesture-handler`              |
| **React Native Reanimated**      | Animations      | `npm install react-native-reanimated`                   |
| **Formik**                       | Forms           | `npm install formik`                                    |
| **Yup**                          | Validation      | `npm install yup`                                       |

```
╔════════════════════════════════════════════════════════════╗
║                   ASYNC STORAGE                            ║
╚════════════════════════════════════════════════════════════╝
```

AsyncStorage example:

```bash
npm install @react-native-async-storage/async-storage
```

```javascript
import AsyncStorage from "@react-native-async-storage/async-storage";

// Store data
const storeData = async (key, value) => {
  try {
    await AsyncStorage.setItem(key, value);
  } catch (error) {
    console.error(error);
  }
};

// Store object
const storeObject = async (key, value) => {
  try {
    const jsonValue = JSON.stringify(value);
    await AsyncStorage.setItem(key, jsonValue);
  } catch (error) {
    console.error(error);
  }
};

// Get data
const getData = async (key) => {
  try {
    const value = await AsyncStorage.getItem(key);
    return value;
  } catch (error) {
    console.error(error);
  }
};

// Get object
const getObject = async (key) => {
  try {
    const jsonValue = await AsyncStorage.getItem(key);
    return jsonValue != null ? JSON.parse(jsonValue) : null;
  } catch (error) {
    console.error(error);
  }
};

// Remove data
const removeData = async (key) => {
  try {
    await AsyncStorage.removeItem(key);
  } catch (error) {
    console.error(error);
  }
};

// Clear all
const clearAll = async () => {
  try {
    await AsyncStorage.clear();
  } catch (error) {
    console.error(error);
  }
};

// Usage
await storeData("username", "MrDib");
const username = await getData("username");

await storeObject("user", { name: "MrDib", age: 25 });
const user = await getObject("user");
```

```
╔════════════════════════════════════════════════════════════╗
║                   REACT NATIVE PAPER                       ║
╚════════════════════════════════════════════════════════════╝
```

Material Design components:

```bash
npm install react-native-paper
```

```javascript
import {
  Provider as PaperProvider,
  Button,
  Card,
  FAB,
} from "react-native-paper";

export default function App() {
  return (
    <PaperProvider>
      <View style={{ flex: 1, padding: 20 }}>
        <Card>
          <Card.Title title="Card Title" subtitle="Card Subtitle" />
          <Card.Content>
            <Text>Card content</Text>
          </Card.Content>
          <Card.Actions>
            <Button>Cancel</Button>
            <Button>OK</Button>
          </Card.Actions>
        </Card>

        <Button mode="contained" onPress={() => console.log("Pressed")}>
          Press me
        </Button>

        <FAB
          style={{ position: "absolute", right: 16, bottom: 16 }}
          icon="plus"
          onPress={() => console.log("Pressed")}
        />
      </View>
    </PaperProvider>
  );
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   FORMIK + YUP                             ║
╚════════════════════════════════════════════════════════════╝
```

Form handling:

```bash
npm install formik yup
```

```javascript
import { Formik } from "formik";
import * as Yup from "yup";

const validationSchema = Yup.object().shape({
  email: Yup.string().email("Invalid email").required("Email is required"),
  password: Yup.string()
    .min(6, "Password must be at least 6 characters")
    .required("Password is required"),
});

function LoginForm() {
  return (
    <Formik
      initialValues={{ email: "", password: "" }}
      validationSchema={validationSchema}
      onSubmit={(values) => {
        console.log(values);
      }}
    >
      {({
        handleChange,
        handleBlur,
        handleSubmit,
        values,
        errors,
        touched,
      }) => (
        <View>
          <TextInput
            placeholder="Email"
            onChangeText={handleChange("email")}
            onBlur={handleBlur("email")}
            value={values.email}
            style={styles.input}
          />
          {touched.email && errors.email && (
            <Text style={styles.error}>{errors.email}</Text>
          )}

          <TextInput
            placeholder="Password"
            onChangeText={handleChange("password")}
            onBlur={handleBlur("password")}
            value={values.password}
            secureTextEntry
            style={styles.input}
          />
          {touched.password && errors.password && (
            <Text style={styles.error}>{errors.password}</Text>
          )}

          <Button title="Submit" onPress={handleSubmit} />
        </View>
      )}
    </Formik>
  );
}
```

---

<div align="center">

## 🔧 Native Modules

</div>

### Access Native Features 📲

```
# ═══════════════════════════════════════════
# NATIVE MODULES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COMMON NATIVE FEATURES                   ║
╚════════════════════════════════════════════════════════════╝

Camera:
─────────────────────────────────────────────────────────────
```

```bash
npm install react-native-image-picker
```

```javascript
import { launchCamera, launchImageLibrary } from "react-native-image-picker";

// Take photo
const takePhoto = () => {
  const options = {
    mediaType: "photo",
    quality: 0.8,
  };

  launchCamera(options, (response) => {
    if (response.assets) {
      const photo = response.assets[0];
      console.log("Photo URI:", photo.uri);
    }
  });
};

// Pick from library
const pickImage = () => {
  launchImageLibrary({ mediaType: "photo" }, (response) => {
    if (response.assets) {
      const image = response.assets[0];
      console.log("Image URI:", image.uri);
    }
  });
};
```

```
Permissions:
─────────────────────────────────────────────────────────────
```

```bash
npm install react-native-permissions
```

```javascript
import { request, PERMISSIONS, RESULTS } from "react-native-permissions";

// Request camera permission
const requestCameraPermission = async () => {
  const result = await request(
    Platform.OS === "ios" ? PERMISSIONS.IOS.CAMERA : PERMISSIONS.ANDROID.CAMERA
  );

  if (result === RESULTS.GRANTED) {
    console.log("Permission granted");
  }
};
```

```
Location:
─────────────────────────────────────────────────────────────
```

```bash
npm install @react-native-community/geolocation
```

```javascript
import Geolocation from "@react-native-community/geolocation";

// Get current location
Geolocation.getCurrentPosition(
  (position) => {
    console.log(position.coords.latitude);
    console.log(position.coords.longitude);
  },
  (error) => console.error(error),
  { enableHighAccuracy: true, timeout: 20000, maximumAge: 1000 }
);

// Watch location
const watchId = Geolocation.watchPosition((position) => {
  console.log("Location updated:", position.coords);
});

// Stop watching
Geolocation.clearWatch(watchId);
```

---

<div align="center">

## 🎯 Platform-Specific Code

</div>

### Handle iOS and Android Differences 🔀

```
# ═══════════════════════════════════════════
# PLATFORM-SPECIFIC CODE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PLATFORM MODULE                          ║
╚════════════════════════════════════════════════════════════╝
```

Platform-specific code:

```javascript
import { Platform } from "react-native";

// Check platform
const isIOS = Platform.OS === "ios";
const isAndroid = Platform.OS === "android";

// Platform.select
const styles = StyleSheet.create({
  container: {
    padding: Platform.select({
      ios: 20,
      android: 16,
      default: 16,
    }),
  },
  text: {
    fontSize: Platform.select({
      ios: 16,
      android: 14,
    }),
  },
});

// Conditional rendering
{
  Platform.OS === "ios" && <IOSSpecificComponent />;
}
{
  Platform.OS === "android" && <AndroidSpecificComponent />;
}

// Platform version
if (Platform.Version >= 29) {
  // Android API 29+
}

// File extensions
// Component.ios.js - iOS only
// Component.android.js - Android only
// Component.js - Shared

// Auto-imports correct file
import Component from "./Component"; // Will use .ios.js on iOS, .android.js on Android
```

---

<div align="center">

## 🐛 Debugging

</div>

### Debug Your App 🔍

```
# ═══════════════════════════════════════════
# DEBUGGING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╝
║                   DEBUGGING TOOLS                          ║
╚════════════════════════════════════════════════════════════╝

Built-in Tools:
─────────────────────────────────────────────────────────────
• Shake device → Dev Menu
• Cmd/Ctrl + D → Dev Menu (simulator)
• Cmd/Ctrl + M → Dev Menu (Android)

Dev Menu Options:
• Reload
• Debug
• Enable/Disable Fast Refresh
• Toggle Inspector
• Show Perf Monitor

React DevTools:
─────────────────────────────────────────────────────────────
```

```bash
npm install -g react-devtools
react-devtools
```

```
Flipper (Recommended):
─────────────────────────────────────────────────────────────
• Download from: fbflipper.com
• Network inspector
• Layout inspector
• Logs viewer
• Redux DevTools
• Database inspector

Console Logging:
─────────────────────────────────────────────────────────────
```

```javascript
console.log("Simple log");
console.warn("Warning");
console.error("Error");
console.table([{ name: "John", age: 30 }]);
console.time("timer");
// code
console.timeEnd("timer");
```

```
Reactotron (Third-party):
─────────────────────────────────────────────────────────────
```

```bash
npm install --save-dev reactotron-react-native
```

```javascript
// Configure
import Reactotron from "reactotron-react-native";

Reactotron.configure().useReactNative().connect();

// Usage
Reactotron.log("Hello");
Reactotron.display({
  name: "User",
  value: { name: "John", age: 30 },
});
```

---

<div align="center">

## ⚡ Performance Optimization

</div>

### Make Your App Fast 🚀

```
# ═══════════════════════════════════════════
# PERFORMANCE OPTIMIZATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   OPTIMIZATION TIPS                        ║
╚════════════════════════════════════════════════════════════╝

1. Use FlatList, Not ScrollView:
─────────────────────────────────────────────────────────────
```

```javascript
// ❌ BAD - Renders all items
<ScrollView>
  {data.map(item => <Item key={item.id} />)}
</ScrollView>

// ✅ GOOD - Virtualizes items
<FlatList
  data={data}
  renderItem={({ item }) => <Item />}
  keyExtractor={item => item.id}
/>
```

```
2. Memoization:
─────────────────────────────────────────────────────────────
```

```javascript
import React, { memo, useMemo, useCallback } from "react";

// Memoize component
const ExpensiveComponent = memo(({ data }) => {
  return <View>{/* render */}</View>;
});

// Memoize computed values
const sortedData = useMemo(() => {
  return data.sort((a, b) => a.name.localeCompare(b.name));
}, [data]);

// Memoize callbacks
const handlePress = useCallback(() => {
  console.log("Pressed");
}, []);
```

```
3. Image Optimization:
─────────────────────────────────────────────────────────────
```

```javascript
// Use react-native-fast-image
import FastImage from "react-native-fast-image";

<FastImage
  source={{ uri: imageUrl, priority: FastImage.priority.normal }}
  resizeMode={FastImage.resizeMode.cover}
  style={{ width: 200, height: 200 }}
/>;
```

```
4. Remove Console Logs in Production:
─────────────────────────────────────────────────────────────
```

```bash
# Install
npm install babel-plugin-transform-remove-console --save-dev
```

```javascript
// babel.config.js
module.exports = {
  presets: ["module:metro-react-native-babel-preset"],
  env: {
    production: {
      plugins: ["transform-remove-console"],
    },
  },
};
```

```
5. Hermes Engine (Android):
─────────────────────────────────────────────────────────────
// android/app/build.gradle
project.ext.react = [
    enableHermes: true
]

Benefits:
✅ Faster app start
✅ Reduced memory
✅ Smaller bundle size
```

---

<div align="center">

## 📲 Building & Deployment

</div>

### Ship Your App 🚢

```
# ═══════════════════════════════════════════
# BUILDING & DEPLOYMENT
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   BUILDING FOR PRODUCTION                  ║
╚════════════════════════════════════════════════════════════╝

iOS Build:
─────────────────────────────────────────────────────────────
1. Open Xcode
2. Select "Any iOS Device"
3. Product → Archive
4. Upload to App Store Connect
5. Submit for review

Android Build:
─────────────────────────────────────────────────────────────
```

```bash
# Generate release APK
cd android
./gradlew assembleRelease

# Generate AAB (for Play Store)
./gradlew bundleRelease

# Output:
# android/app/build/outputs/apk/release/app-release.apk
# android/app/build/outputs/bundle/release/app-release.aab
```

```
EAS Build (Expo):
─────────────────────────────────────────────────────────────
```

```bash
# Install EAS CLI
npm install -g eas-cli

# Login
eas login

# Configure
eas build:configure

# Build for iOS
eas build --platform ios

# Build for Android
eas build --platform android

# Build both
eas build --platform all

# Submit to stores
eas submit --platform ios
eas submit --platform android
```

```
╔════════════════════════════════════════════════════════════╗
║                   APP ICONS & SPLASH SCREENS               ║
╚════════════════════════════════════════════════════════════╝

Expo:
─────────────────────────────────────────────────────────────
```

```json
// app.json
{
  "expo": {
    "name": "My App",
    "icon": "./assets/icon.png",
    "splash": {
      "image": "./assets/splash.png",
      "resizeMode": "contain",
      "backgroundColor": "#ffffff"
    }
  }
}
```

```
React Native CLI:
─────────────────────────────────────────────────────────────
Use: react-native-make or manual setup
```

```bash
npm install -g react-native-make

# Set app icon
react-native set-icon --path ./icon.png

# Set splash screen
react-native set-splash --path ./splash.png --resize contain
```

---

<div align="center">

## 💡 Best Practices

</div>

### Build Better Apps 🌟

```
# ═══════════════════════════════════════════
# BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CODE ORGANIZATION                        ║
╚════════════════════════════════════════════════════════════╝

Folder Structure:
─────────────────────────────────────────────────────────────
```

```
src/
├── components/         # Reusable components
│   ├── Button.js
│   ├── Card.js
│   └── Input.js
├── screens/           # Screen components
│   ├── HomeScreen.js
│   ├── ProfileScreen.js
│   └── SettingsScreen.js
├── navigation/        # Navigation config
│   └── AppNavigator.js
├── services/          # API calls
│   ├── api.js
│   └── auth.js
├── hooks/             # Custom hooks
│   ├── useAuth.js
│   └── useFetch.js
├── context/           # Context providers
│   └── AuthContext.js
├── utils/             # Utility functions
│   ├── helpers.js
│   └── constants.js
├── assets/            # Images, fonts
│   ├── images/
│   └── fonts/
└── styles/            # Shared styles
    └── theme.js
```

```
╔════════════════════════════════════════════════════════════╗
║                   CODING BEST PRACTICES                    ║
╚════════════════════════════════════════════════════════════╝

1. Use TypeScript:
─────────────────────────────────────────────────────────────
```

```bash
npx react-native init MyApp --template react-native-template-typescript
```

```
2. Use Absolute Imports:
─────────────────────────────────────────────────────────────
```

```javascript
// babel.config.js
module.exports = {
  plugins: [
    [
      "module-resolver",
      {
        root: ["./src"],
        alias: {
          "@components": "./src/components",
          "@screens": "./src/screens",
          "@utils": "./src/utils",
        },
      },
    ],
  ],
};

// Usage
import Button from "@components/Button";
import { API_URL } from "@utils/constants";
```

```
3. Extract Reusable Components:
─────────────────────────────────────────────────────────────
```

```javascript
// ❌ BAD
<TouchableOpacity style={styles.button} onPress={onPress}>
  <Text style={styles.buttonText}>Submit</Text>
</TouchableOpacity>

// ✅ GOOD
<Button onPress={onPress} title="Submit" />
```

```
4. Use Custom Hooks:
─────────────────────────────────────────────────────────────
```

```javascript
// hooks/useFetch.js
export function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch(url)
      .then((res) => res.json())
      .then(setData)
      .catch(setError)
      .finally(() => setLoading(false));
  }, [url]);

  return { data, loading, error };
}

// Usage
const { data, loading, error } = useFetch("/api/users");
```

```
5. Environment Variables:
─────────────────────────────────────────────────────────────
```

```bash
npm install react-native-config
```

```
# .env
API_URL=https://api.example.com
API_KEY=your_key_here
```

```javascript
import Config from "react-native-config";

const apiUrl = Config.API_URL;
const apiKey = Config.API_KEY;
```

```
6. Error Boundaries:
─────────────────────────────────────────────────────────────
```

```javascript
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    console.error(error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      return <Text>Something went wrong.</Text>;
    }

    return this.props.children;
  }
}

// Usage
<ErrorBoundary>
  <App />
</ErrorBoundary>;
```

---

<div align="center">

## 🎯 Summary

</div>

### Start Building with React Native! 📱

```
╔════════════════════════════════════════════════════════════╗
║                   QUICK START CHECKLIST                    ║
╚════════════════════════════════════════════════════════════╝

Beginner Path:
─────────────────────────────────────────────────────────────
☐ Install Node.js
☐ Install Expo CLI
☐ Create first app: npx create-expo-app
☐ Run on phone with Expo Go
☐ Learn core components
☐ Build simple app
☐ Deploy to app stores

Advanced Path:
─────────────────────────────────────────────────────────────
☐ Install React Native CLI
☐ Setup Xcode/Android Studio
☐ Learn navigation
☐ Implement state management
☐ Add native modules
☐ Optimize performance
☐ Build production app

Essential Libraries:
─────────────────────────────────────────────────────────────
✅ React Navigation
✅ AsyncStorage
✅ React Query
✅ React Native Paper/NativeBase
✅ Axios
✅ Formik + Yup

Remember:
─────────────────────────────────────────────────────────────
"Start with Expo.
Learn the basics.
Build real apps.
Optimize performance.
Ship to stores!"

Now go build amazing mobile apps! 🚀
```

---

<div align="center">

**Built with 📱 by MrDib, for mobile developers**

_Remember: "Learn once, write anywhere!"_ ✨

**Happy Coding!** 🎉

</div>

---

## 🔗 Related Guides

- [JavaScript Fundamentals](../Development/Languages/JavaScript.md)
- [React Basics](../Development/Frontend/React-Ecosystem.md)
- [Mobile Development Best Practices](./Mobile-Best-Practices.md)
- [API Integration](../APIs-Services/Public-APIs.md)

---

## 📊 Quick Reference Card

### **Essential Commands:**

```bash
# Expo
npx create-expo-app MyApp
npx expo start

# React Native CLI
npx react-native init MyApp
npx react-native run-ios
npx react-native run-android

# Build
eas build --platform all
```

### **Core Components:**

- `View` - Container (like div)
- `Text` - Text display
- `TouchableOpacity` - Touchable
- `Image` - Images
- `FlatList` - Lists
- `TextInput` - Input
- `ScrollView` - Scrollable

### **Quick Component:**

```javascript
import { View, Text, Button } from "react-native";

export default function App() {
  return (
    <View style={{ flex: 1, justifyContent: "center" }}>
      <Text>Hello React Native!</Text>
      <Button title="Press Me" onPress={() => alert("Hi!")} />
    </View>
  );
}
```

---
