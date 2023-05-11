# SwiftUI-Switch-languages-on-iPad
Switch the language through the button. (SwiftUI)

# The first part:

1. Click the switch button "En"

![IMG_1110](https://github.com/S-way520/SwiftUI-Switch-languages-on-iPad/assets/95877651/d80b821a-5f94-4615-8344-7828c8c58d04)

<img src = "![IMG_1110](https://github.com/S-way520/SwiftUI-Switch-languages-on-iPad/assets/95877651/d80b821a-5f94-4615-8344-7828c8c58d04)" width = "400" height = "400">
     
2. Click the switch button "中"
     
<img src = "![IMG_1109](https://github.com/S-way520/SwiftUI-Switch-languages-on-iPad/assets/95877651/47e24823-0824-4106-9628-8c8f7e29e009)" width = "400" height = "400">

# The second part:
1. Code file 1:
```swift
import SwiftUI
@main
struct MyApp: App {
        @State var identifier = "zh"
    var body: some Scene {
        WindowGroup {
            ContentView(identifier: $identifier)
                .environment(\.locale, .init(identifier: identifier))
        }
    }
}
```
2. Code file 2:
```swift
import SwiftUI
struct ContentView: View {
    @Environment(\.locale) var locale
    var languageCode: String? {locale.language.languageCode?.identifier}
    var isChineseLanguage: Bool { languageCode == "zh"}
    @Binding var identifier: String
    @AppStorage(" ") var IDshow = false
    var body: some View {
        VStack {
            Image(systemName: "globe")
                .imageScale(.large)
                .foregroundColor(.accentColor)
            if isChineseLanguage {
                Text("你好，世界！")
            } else {
                Text("Hello, world!")
            }
            HStack{
                if IDshow {
                    Text("")
                        .onAppear(perform: {
                            identifier = "en"
                        })
                    Button("En", action: {
                        self.identifier = "zh"
                        self.IDshow.toggle()
                    })
                    .foregroundColor(Color.red)
                    .cornerRadius(15)
                } else {
                    Button("中", action: {
                        self.identifier = "en"
                        self.IDshow.toggle()
                    })
                    .foregroundColor(Color.red)
                    .cornerRadius(15)
                }
            }
        }
    }
}
```
