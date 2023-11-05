<h1>BONUS</h1>
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/didi816l/yzu-1101422-swift/main/IMG_0370.jpg">
    </td>
    <td>
      
```swift
import SwiftUI

struct ContentView: View {
    let displayFontType = [".default",".rounded",".monspaced",".serif"]
    @State var displayFontSelected = 0
    @State var IsDeepScheme = false
    @State var colorArray:Array = [255.0,255.0,255.0]
    @State var stepperValue = 0
    @State var sliderValue = 0.0
    @State var date = Date()
    
    var body: some View {
        NavigationView{
            Form(content:
            {
                
            }
            )
                .navigationBarTitle("Settings")
        }
    }
}

  ```
   
  </tr>
</table>
