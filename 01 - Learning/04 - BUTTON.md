Button View
 - In SwiftUI, a button view is used  to create interactive elements that perform an action when tapped or clicked


 Here's a basic example of how to create a button in SwiftUI

```swift
    import SwiftUI
    struct ContentView: View {
        var body: some View {

            Button(action: {
                print("Button is Pressed")
            }) {
                Text("Tap Me")
                    .padding()
                    .background(Color.blue)
                    .foreground(Color.white)
                    .cornerRadius(8)
            }

        }
    }
```

Button Common Modifiers
```swift

    // Basic Styled Button

    Button(action: {
        // Action Here
    }) {
        Text("Custom Button")
            .foregroundColor(.white)            // Set Text Color
            .padding(.horizontal, 20)           // Add Horizontal Padding
            .padding(.vertical, 10)             // Add Vertical Padding
            .background(Color.blue)             // Add Background Color
            .cornerRadius(8)                    // Rounds The Corner
    }


    // Advance Button with Multiple Modifiers
    Button(action: {
        // Action Here
    }) {
        HStack {
            Image(systemName: "star.fill")
            Text("Rate Now")
        }
        .padding()
        .foregroundColor(.white)
        .background(
            LinearGradient(
                gradient: Gradient( colors: [.blue, .purple]),
                startPoint: .leading,
                endPoint: .trailing
            )
        )
        .cornerRadius(10)
        .shadow(
            color: .gray.opacity(0.4),
            radius: 5,
            x: 0,
            y: 2
        )
    }
    .buttonStyle(.plain)                // Use plain button styles (removes the default one)


    Button("Interactive Button" {
        // Action Here
    }).disabled(true)                           // Disables Button Interation
        .opacity(0.5)                           // Makes Button appear faded when disabled
        .scaleEffect(0.98)                      // Slightly reduce button size
        .animation(.easeInOut, value: true)     // Animate state change
    
```