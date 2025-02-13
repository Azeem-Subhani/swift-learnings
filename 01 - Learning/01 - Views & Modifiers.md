What is Structs?
 - Structs are data types in swift that can store multiple  values.
 - Think of a LEGO blocks, each block is like a struct. A struct is a special box which holds things together.

 ```swift
 struct MyCoolScreen: View {
    var body: some View {
        Text("Hello, World")
            .font(.largeTitle)
            .foregroundColor(.blue)
    }
 }
```


What is View?
 - A view is the building blocks of a swift ui user interface.
 - A view represent a piece of ui, such as button, text, image or even a container like vstack/hstack.
 - Views are lightweight and value types (structs).


What is a View Modifiers?
 - View Modifiers are the methods that you apply to views to customize their appearance or behavior.
 - View Modifiers returns a new view with the applied changes allowing you to chain multiple modifiers together.

 ```swift
    Text("Hello")
        .font(.headline) // Modifier to change the font
        .foregroundColor(.red) // Modifier to change the text color
        .padding() // Modifier to add the padding
        .background(Color.blue) // Modifier to set the background color 
        .cornerRadius(10) // Modifier to round the corners
 ```

 Key Points About View Modifiers
  - Chaining: Modifiers can be chained together to apply multiple customizations
  - Order Matters: The order of modifiers can affect the final result.
    - In the above example padding is applied to the before a background will include the padding in the background, but padding applied after the 
        the background will not.
  - Reusability: You can create custom view modifiers to reuse common styling across your app.