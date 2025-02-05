# LOTR Currency Converter - SwiftUI Learning Guide

## Table of Contents
- [Complete Source Code](#complete-source-code)
- [Core Concepts](#core-concepts)
  - [SwiftUI Basics](#swiftui-basics)
  - [Structs in SwiftUI](#structs-in-swiftui)
  - [Property Wrappers](#property-wrappers)
- [UI Components Deep Dive](#ui-components-deep-dive)
  - [View Containers](#view-containers)
  - [Images](#images)
  - [Text](#text)
  - [Buttons](#buttons)
- [View Modifiers Encyclopedia](#view-modifiers-encyclopedia)
- [Best Practices](#best-practices)

## Complete Source Code

```swift
//  ContentView.swift
//  LOTRConverter
//  Created by Azeem Subhani

import SwiftUI

struct ContentView: View {
    @State var showExchangeInfo = false;
    
    var body: some View {
        ZStack {
            Image(.background)
                .resizable()
                .ignoresSafeArea()
            
            VStack {
                Image(.prancingpony)
                    .resizable()
                    .scaledToFit()
                    .frame(height: 200)
                
                Text("Currency Exchange")
                    .font(.largeTitle)
                    .foregroundStyle(.white)
                
                HStack {
                    VStack {
                        HStack {
                            Image(.silverpiece)
                                .resizable()
                                .scaledToFit()
                                .frame(height: 33)
                            
                            Text("Silver Piece")
                                .font(.headline)
                                .foregroundStyle(.white)
                        }
                        Text("Text Field!")
                    }
                    
                    Image(systemName: "equal")
                        .font(.largeTitle)
                        .foregroundStyle(.white)
                        .symbolEffect(.pulse)
                    
                    VStack {
                        HStack {
                            Text("Gold Piece")
                                .font(.headline)
                                .foregroundStyle(.white)
                            Image(.goldpiece)
                                .resizable()
                                .scaledToFit()
                                .frame(height: 33)
                        }
                        Text("Text Field")
                    }
                }
                
                Spacer()
                
                HStack {
                    Spacer()
                    Button {
                        showExchangeInfo.toggle()
                        print("Show Exchange Value: ", showExchangeInfo)
                    } label: {
                        Image(systemName: "info.circle.fill")
                            .font(.largeTitle)
                            .foregroundStyle(.white)
                    }.padding(.trailing)
                }
            }
            .border(.blue)
        }
    }
}

#Preview {
    ContentView()
}
```

## Core Concepts

### SwiftUI Basics

SwiftUI is Apple's modern framework for building user interfaces across all Apple platforms. It uses a declarative syntax, which means you describe WHAT you want to create rather than HOW to create it.

Key aspects of SwiftUI:
1. Declarative Syntax
2. Automatic UI Updates
3. Live Preview
4. Cross-platform Support
5. Built-in Animation Support

Example of declarative syntax:
```swift
// Declarative (SwiftUI)
Text("Hello")
    .font(.title)
    .foregroundStyle(.blue)

// Imperative (UIKit)
let label = UILabel()
label.text = "Hello"
label.font = UIFont.systemFont(ofSize: 24)
label.textColor = .blue
```

### Structs in SwiftUI

In SwiftUI, views are implemented as structs rather than classes. This is a fundamental design choice that offers several benefits:

1. **Performance**: Structs are value types, making them more efficient for SwiftUI's diffing engine
2. **Thread Safety**: Value types are inherently thread-safe
3. **Immutability**: Helps prevent unexpected state changes
4. **Memory Efficiency**: Stack allocation instead of heap allocation

Basic structure of a SwiftUI view:
```swift
struct MyView: View {
    var body: some View {
        // View content here
    }
}
```

### Property Wrappers

Property wrappers add behavior to properties. SwiftUI uses several property wrappers to manage state and data flow.

1. **@State**
   - Used for simple state management within a view
   - Automatically triggers view updates when value changes
   ```swift
   @State private var count = 0
   ```

2. **@Binding**
   - Creates a two-way connection between views
   - Allows child views to modify parent's state
   ```swift
   struct ChildView: View {
       @Binding var value: Bool
   }
   ```

3. **@StateObject**
   - Manages observable object instances
   - Persists through view updates
   ```swift
   @StateObject private var viewModel = ViewModel()
   ```

4. **@ObservedObject**
   - Similar to @StateObject but doesn't create the instance
   - Used for passing observable objects
   ```swift
   @ObservedObject var dataModel: DataModel
   ```

5. **@Environment**
   - Reads values from the environment
   - Useful for system-wide settings
   ```swift
   @Environment(\.colorScheme) var colorScheme
   ```

## UI Components Deep Dive

### View Containers

#### ZStack
Purpose: Overlays views back-to-front
Common Modifiers:
```swift
ZStack {
    // 1. Alignment
    .alignment(.topLeading)
    
    // 2. Z Index
    .zIndex(1)
    
    // 3. Background
    .background(.ultraThinMaterial)
    
    // 4. Clipped
    .clipped()
    
    // 5. Shadow
    .shadow(radius: 10)
}
```

#### VStack
Purpose: Arranges views vertically
Common Modifiers:
```swift
VStack {
    // 1. Spacing
    .spacing(20)
    
    // 2. Alignment
    .alignment(.leading)
    
    // 3. Padding
    .padding()
    
    // 4. Frame
    .frame(maxWidth: .infinity)
    
    // 5. Layout Priority
    .layoutPriority(1)
}
```

#### HStack
Purpose: Arranges views horizontally
Common Modifiers:
```swift
HStack {
    // 1. Spacing
    .spacing(8)
    
    // 2. Alignment
    .alignment(.center)
    
    // 3. Padding
    .padding(.horizontal)
    
    // 4. Frame
    .frame(height: 50)
    
    // 5. Border
    .border(.gray, width: 1)
}
```

### Images

SwiftUI provides two types of images:
1. Asset Catalog Images
2. SF Symbols (System Images)

Common Image Modifiers:
```swift
Image("myImage")
    // 1. Resize Options
    .resizable()
    .scaledToFit()
    
    // 2. Frame Control
    .frame(width: 200, height: 200)
    
    // 3. Clipping
    .clipShape(Circle())
    
    // 4. Styling
    .overlay(Circle().stroke(.white, lineWidth: 2))
    
    // 5. Effects
    .shadow(color: .black.opacity(0.3), radius: 10, x: 0, y: 5)
```

### Text

Text views are used for displaying strings. They are highly customizable:

```swift
Text("Hello, World!")
    // 1. Font Styling
    .font(.system(size: 24, weight: .bold, design: .rounded))
    
    // 2. Color
    .foregroundStyle(.primary)
    
    // 3. Multiple Lines
    .lineLimit(2)
    .multilineTextAlignment(.center)
    
    // 4. Text Decoration
    .underline(true, color: .blue)
    
    // 5. Dynamic Type
    .dynamicTypeSize(.large)
```

### Buttons

Buttons handle user interaction:

```swift
Button {
    // Action
} label: {
    Text("Click Me")
        // 1. Style
        .buttonStyle(.bordered)
        
        // 2. Size
        .controlSize(.large)
        
        // 3. Custom Colors
        .tint(.blue)
        
        // 4. Disabled State
        .disabled(false)
        
        // 5. Animation
        .animation(.easeIn, value: isPressed)
}
```

## View Modifiers Encyclopedia

View modifiers are methods that modify the appearance or behavior of a view. They return a new view with the modification applied.

### Layout Modifiers
```swift
.frame(width: 100, height: 100)
.padding(.horizontal, 20)
.offset(x: 10, y: 10)
.position(x: 100, y: 100)
.edgesIgnoringSafeArea(.all)
```

### Style Modifiers
```swift
.foregroundStyle(.blue)
.background(.red)
.border(.green, width: 2)
.cornerRadius(10)
.opacity(0.8)
```

### Effect Modifiers
```swift
.blur(radius: 3)
.shadow(radius: 10)
.brightness(0.2)
.contrast(1.2)
.grayscale(0.5)
```

### Animation Modifiers
```swift
.animation(.spring(), value: isAnimating)
.transition(.slide)
.rotationEffect(.degrees(45))
.scaleEffect(1.2)
.opacity(isVisible ? 1 : 0)
```

### Interaction Modifiers
```swift
.onTapGesture { }
.onLongPressGesture { }
.disabled(true)
.allowsHitTesting(false)
.contentShape(Rectangle())
```

## Best Practices

1. **View Organization**
   - Keep views small and focused
   - Extract reusable components
   - Use meaningful names

2. **State Management**
   - Use appropriate property wrappers
   - Keep state at appropriate level
   - Avoid unnecessary state

3. **Performance**
   - Minimize view updates
   - Use lazy loading when appropriate
   - Profile your app regularly

4. **Accessibility**
   - Add meaningful labels
   - Support Dynamic Type
   - Test with VoiceOver

5. **Code Style**
   - Follow Swift style guidelines
   - Group related modifiers
   - Comment complex logic

Remember that SwiftUI is highly composable - you can combine these components and modifiers in countless ways to create complex, beautiful interfaces. The key is understanding how each piece works and how they can work together.

For more advanced topics and detailed documentation, refer to:
- [Apple's SwiftUI Documentation](https://developer.apple.com/documentation/swiftui)
- [Swift Language Guide](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/)
- [Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines)