Below are the examples of basic shapes in the SwiftUI.

```swift
    // Rectangle
    Rectangle()
        .fill(Color.blue)                   // Fills shape with color
        .frame(width: 200, height: 200)     // Sets dimensions
        .cornerRadius(15)                   // Rounds corners

    // Rounded Rectangle
    RoundedRectangle(cornerRadius: 20)
        .fill(
            LinearGradient(
                gradient: Gradient(colors: [.blue, .purple]),
                startPoint: .leading,
                endPoint: .trailing
            )
        )
        .frame(width: 200, height: 100)

    // Circle
    Circle()
        .stroke(Color.red, lineWidth: 2)    // Creates outline instead of fill
        .frame(width: 100, height: 100)    

    // Capsule
    Capsule()
        .fill(Color.green)
        .frame(width: 200, height: 80)

    // Ellipse
    Ellipse()
        .fill(Color.orange)
        .frame(width: 200, height: 100)

    
    // Advance Space with Multiple Modifiers
    Rectangle()
        .fill(Color.blue)
        .frame(width: 200, height: 100)
        .overlay(                           // Adds content over shape
            Text("Overlay Text")
                .foregroundColor(.white)
        )
        .border(Color.black, width: 2)
        .shadow(radius: 10)


    Circle()
        .strokeBorder(
            LinearGradient(
                gradient: Gradient(colors: [.red, .blue]),
                startPoint: .topLeading,
                endPoint: .bottomLeading
            ),
            lineWidth: 5
        )
        .frame(width: 100, height: 100)
        .background(Circle().fill(Color.white))
```