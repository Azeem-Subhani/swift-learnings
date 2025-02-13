
Text View
 - in SwiftUI, a Text view is used to display on or more lines of read-onnly text.

```swift
    import SwiftUI

    struct ContentView: View {
        var body: some View {
            Text("Hello, World")
                .font(.title)
                .foregroundColor(.blue)
                .padding()
        }
    }
```

Some examples for Text View
```swift
    // Basic Text
    Text("Hello, World")

    // Text with Multiple Modifiers
    Text("Styled Text")
        .font(.title)               // Set the font size to pre-defined title size
        .foregroundColor(.blue)     // Change the text color to blue
        .bold()                     // Makes the text bold
        .italic()                   // Applies italic style to the text

    // Text with Line Control
    Text("This is a long text that will wrap to multiple lines")
        .lineLimit(2)                       // Limits text to maximum 2 lines
        .multilineTextAlignment(.center)    // Centers the text when it spans multiple lines
        .lineSpace(10)                      // Add 10 points of space between lines

    // Custom Font Configurations
    Text("Custom Font")
        .font(.system(size: 24, weight: .semibold))     // Custom font size and weight
        .tracking(1.5)                                  // Adds space between character (letter spacing)

    // Text with Background and Border
    Text("Decorated Text")
        .padding()                      // Adds default padding arrond the text
        .background(Color.yellow)       // Adds yellow background
        .cornerRadius(10)               // Rounds the corners of the background
        .shadow(radius: 5)              // Adds a shadow effect with 5 points blur

    // Text with Line Decorations
    Text("Decorated Text")
        .underline(true, color: .red)           // Adds red underline
        .strikethrough(true, color: .blue)      // Adds blue strikethrough
```