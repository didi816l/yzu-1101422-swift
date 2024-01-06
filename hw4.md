<h1>HW4</h1>
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/didi816l/yzu-1101422-swift/main/IMG_0369.jpg">
    </td>
    <td> 
      
```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            Text("Apple Store")
                .font(.largeTitle)
                .fontWeight(.heavy)
                .foregroundStyle(.primary)
            TabView{
                //Group{
                    WelcomeView()
                        .tabItem {     
                            Image(systemName: "rosette")
                            Text("Welcome")
                        }
                   CourseListView()
                        .tabItem {  
                            Image(systemName: "list.dash")
                            Text("Course")
                        }
                CardView()                        
                    .tabItem { 
                            Image(systemName: "book")
                            Text("Learn")
                        }
                SettingView()                        
                    .tabItem { 
                        Image(systemName: "wrench")
                        Text("Learn")
                    }
            }
        }
    }
}


  ```
  </tr>
</table>
