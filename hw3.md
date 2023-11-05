<h1>HW3</h1>
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
        TitleView()
        HStack{
            FruitView(imageName: "book")
            FruitView(imageName: "bottle")
            FruitView(imageName: "computer")
        }
        ZStack{
            FruitView(imageName: "bottle")
        }
        HStack{
            FruitView(imageName: "computer")
            FruitView(imageName: "bottle")
        }
    }
}
    struct TitleView: View{
        var body: some View{
            VStack(alignment: .center, spacing: 2)
            {
                Text("劉威佑的")
                    .font(.system(size:30))
                Text("書櫃")
                    .font(.title)
                    .foregroundColor(Color(red:29/255,green :40/255,blue:192.255))
            }
        }
        
    }
    
    struct FruitView: View{
        var imageName:String
        var body: some View{
            VStack{
                Image(imageName)
                    .resizable()
                    .aspectRatio(contentMode: .fit)
                    .frame(height:200,alignment: .center)
                Text(imageName.capitalized)
                    .fontWeight(.bold)
                    .font(.system(size:20))
            }.padding(.all,2)
        }
    }
    extension UIScreen{
        static let screenwidth = UIScreen.main.bounds.size.width
        static let screensize = UIScreen.main.bounds.size
        static let screenheight = UIScreen.main.bounds.size.height
        
    }

  ```
   
  </tr>
</table>
