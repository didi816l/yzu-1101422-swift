<h1>HW1</h1>
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/didi816l/yzu-1101422-swift/main/IMG_0276.jpeg">
    </td>
    <td>
      
```swift
  import SwiftUI
struct ContentView: View {
    var body: some View {
        VStack {
            Image(systemName: "applelogo")
                .imageScale(.large)
                .foregroundColor(.red)
            Text("1101422 劉威佑")
            .foregroundColor(.red)
        }

        Image("me")
            .resizable()
            .aspectRatio( contentMode:.fill)
            .frame(width: 400, height: 300, alignment: /.center)
            .clipShape(Circle())
                Text("不是對你沒感覺， \n是你沒開保時捷。")
                    .fontWeight(.heavy)
                    .lineSpacing(20)
                    .font(.system(size:32))
                    .foregroundColor(.white)
                    .frame(width:350,height:150,alignment:.center)
                    .background(Color.blue)
                    .cornerRadius(20.0)
                    .opacity(0.8)        
    }
}

  ```
    </td>
  </tr>
</table>
