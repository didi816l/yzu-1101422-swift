<h1>BONUS</h1>
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/didi816l/yzu-1101422-swift/main/IMG_0370.jpg">
    </td>
    <td>
      
```swift
swift
 import SwiftUI

struct ContentView: View {
    let displayFontType = [".default",".rounded",".monospaced",".serif"]
    @State var displayFontSelected = 0
    @State var IsDeepScheme = false;
    @State var colorArray:Array = [255.0,255.0,255.0]
    @State var stepperValue = 0
    @State var sliderValue = 0.0
    @State var date = Date()
    
    var body: some View {
        NavigationView{
            Form(
                content: {
                    Section(header: Text("字型設定"), content: {
                        Picker(selection: $displayFontSelected, label: Text("字型選擇")){
                            ForEach(0..<displayFontType.count, id: \.self, content:{
                                Text(self.displayFontType[$0])  
                            })
                        }
                    })
                    Section(header: Text("背景風格"), content: {
                        Toggle(isOn: $IsDeepScheme, label: {
                            Text("深色\(String(IsDeepScheme))")
                        })
                    })
                    Section(header: Text("計數器"), content: {
                        Stepper( onIncrement: {stepperValue+=1}, onDecrement: {stepperValue-=1},
                                 label: {
                            Text("Stepper \(stepperValue)")
                        })
                    })
                    Section(header: Text("滑桿\(sliderValue,specifier: "%.2f")"), content: {
                        Slider(value: $sliderValue, in: 0...1)
                    })  
                    Section(header: Text("日期"), content: {
                        DatePicker("date", selection: $date, displayedComponents: [.date])
                    })
                }
            )
            .navigationTitle("Settings 設定")
        }
    }
}

  ```
   
  </tr>
</table>
