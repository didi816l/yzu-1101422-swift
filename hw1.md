<h1>HW1</h1>
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/didi816l/yzu-1101422-swift/edit/main/IMG_0276.jpeg">
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
            .aspectRatio( contentMode: /*@START_MENU_TOKEN@*/.fill/*@END_MENU_TOKEN@*/)
            .frame(width: 400, height: 300, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
            .clipShape(/*@START_MENU_TOKEN@*/Circle()/*@END_MENU_TOKEN@*/)
        
            
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
