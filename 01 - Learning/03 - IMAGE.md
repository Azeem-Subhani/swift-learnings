Image View
    - In SwiftUI, used to display images within your app's user interface. 

```swift
    import SwiftUI
    struct ContentView: View {
        var body: some View {
            VStack {
                // Display an image from asset catalog
                Image(.logo)
                    .resizeable()
                    .scaledToFit()
                    .frame(width: 200, height: 200)
                    .clipShape(Circle())
                    .overlay(Circle().stroke(Color.white, lineWidth: 4))
                    .shadow(radius: 10)

                // Display a system symbol
                Image(systemName: "star.fill")
                    .resizeable()
                    .scaledToFit()
                    .frame(width: 50, height: 50)
                    .foregroundColor(.yellow)

                // Display an image from a remote URL

                AsyncImage(url: URL(string: "https://example.com/your_image.jpg")) { image in
                    image
                        .resizeable()
                        .scaledToFit()
                        .frame(wifth: 200, height: 200)
                        .clipShape(Circle())
                        .overlay(Circle().stroke(Color.white, lineWidth: 4))
                } placeholder: {
                    ProgessView()
                }
            }
        }
    }
```

Image Modifiers

```swift
    // Basic Image with Modifiers
    Image("imageName")
        .resizable()                        // Makes the image resizable (requierd for size modifications)
        .scaledToFill()                     // Maintains the aspect ratio while fitting within frame
        .frame(width: 100, height: 100)     // Set fixed diemtions


    // Circular Profile Image
    Image("profile")
        .resizeable()
        .scaledToFill()
        .frame(width: 100, height: 100)
        .clipShape(Circle())                                // Clips the image into a circle
        .overlay(
            Circle().stroke(Color.white, lineWidth: 4)      // Adds a white border
        )
        .shadow(                                            // Adds shadow effect
            color: .gray,                                   // Grey color
            radius: 7,                                      // Blur radius
            x: 0,                                           // Horizontal Offset
            y: 2                                            // Vertical Offset
        )

    Image(systemName: "heart.fill")
        .foregroundColor(.red)                          // Change the symbol color
        .font(.system("size: 40"))                      // Changes symbol size
        .symbolRenderingMode(.multicolor)               // Enables multi-color for supported symbols
```
