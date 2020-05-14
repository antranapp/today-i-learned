---
title: 3 Ways to React to @State Changes in SwiftUI

createdAt: 2020-05-14T09:37:47Z
---

# 3 Ways to React to @State Changes in SwiftUI

*We don’t have didSet anymore. Now what?*

## onEditingChanged

According to Apple’s Developer Documentation, this callback is available on the inits of three controls: TextField, Slider, and Stepper.

```swift
TextField:
init(_:text:onEditingChanged:onCommit:)

Slider:
init(value:in:onEditingChanged:)

Stepper:
init(_:onIncrement:onDecrement:onEditingChanged:)
```

```swift
@State var textValue: String = "Hello"
@State var enteredTextValue: String = ""
@State var textsMatch: Bool = false    

//  ADD THIS
func checkIfTextsMatch(changed: Bool) {
    self.textsMatch = self.textValue == self.enteredTextValue
}

var body: some View {
  VStack {
      HStack {
          Text("Write this word: ")
          Text(textValue)
      }

      TextField("Write here:", 
                text: $enteredTextValue,
                //  USE HERE
                onEditingChanged: self.checkIfTextsMatch)
      .padding(10)
      .border(Color.green, width: 1)

      Toggle(isOn: $textsMatch) {
          Text("Matching?")
      }
      .disabled(true)
      .padding()

  }.padding()
}
```

## Binding Variables

```swift
func checkIfTextsMatch() {
    self.textsMatch = self.textValue == self.enteredTextValue
}

var body: some View {

  // ADD THIS
  let textValueBinding = Binding<String>(get: {
      self.enteredTextValue
  }, set: {
      self.enteredTextValue = $0
      self.checkIfTextsMatch()
  })

  return VStack {
      HStack {
          Text("Write this word: ")
          Text(String(textValue))
      }

      TextField("Write here:", text: textValueBinding)
          .padding(10)
          .border(Color.green, width: 1)
      Text(enteredTextValue)

      Toggle(isOn: $textsMatch) {
          Text("Matching?")
      }
      .disabled(true)
      .padding()
  }.padding()
}
```

## Combine Framework

In Combine’s vocabulary, we have:
- **ObservableObject**: A type of object with a publisher that emits before the object has changed.
- **ObservedObject**: Declares dependency on a reference type that conforms to the ObservableObject protocol. It's a property wrapper type that subscribes to an observable object and invalidates a view whenever the observable object changes.
- **Published**: A type that publishes a property marked with an attribute.

```swift
class ContentViewModel: ObservableObject {
    @Published var textValue: String = "Hello"
    @Published var enteredTextValue: String = "" {
        didSet {
            checkIfTextsMatch()
        }
    }
    @Published var textsMatch: Bool = false

    func checkIfTextsMatch() {
        self.textsMatch = textValue == enteredTextValue
    }
}
```

```swift
struct ContentView: View {

  @ObservedObject var viewModel = ContentViewModel()

  var body: some View {
      VStack {
          HStack {
              Text("Write this word: ")
              Text(String(viewModel.textValue))
          }

          TextField("Write here:", text:$viewModel.enteredTextValue)
              .padding(10)
              .border(Color.green, width: 1)
          Text(viewModel.enteredTextValue)

          Toggle(isOn: $viewModel.textsMatch) {
              Text("Matching?")
          }
          .disabled(true)
          .padding()
      }.padding()
  }
}
```

---

https://medium.com/better-programming/three-ways-to-react-to-state-changes-in-swiftui-a30545c72361