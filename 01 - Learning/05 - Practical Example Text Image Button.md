Below is the practical example of button text and image in place in SwiftUI

```swift
    import SwiftUI

    struct ContentView: View {
        @State private var isPressed: Bool = false;

        var body: some View {

            VStack(spacing: 20) {

                VStack {

                    Image("profile")
                        .resizeable()
                        .scaledToFill()
                        .frame(width: 120, height: 120)
                        .clipShape(Circle())
                        .overlay(
                            Circle()
                                .stroke(Color.blue, lineWidth: 3)
                        )
                        .shadow(radius: 5)

                    
                    Text("Welcome to the App")
                        .font(.system(size: 24, weight: .bold))
                        .foregroundColor(.primary)
                        .padding(.top, 10)


                    Button(action: {
                        isPressed.toggle()
                    }) {
                        Text(isPressed ? "Pressed" : "Press Me")
                            .foregroundColor(isPressed ? .white : .blue)
                            .padding()
                            .frame(width: 200)
                            .background(isPressed ? Color.blue : Color.clear)
                            .cornerRadius(10)
                            .overlay(
                                RoundedRectangle(cornerRadius: 12)
                                    .stroke(Color.blue, lineWidth: 2)
                            )
                    } // Button
                    .animation(.spring(), value: isPressed)
                } // VStack
                .padding()
                .background(Color.gray.opacity(0.1))
                .cornerRadius(20)

            }

        }
    }
```