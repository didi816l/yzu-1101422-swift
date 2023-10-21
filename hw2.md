<h1>HW2</h1>
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/didi816l/yzu-1101422-swift/main/imghw2.png">
    </td>
    <td>
      
```swift
  import SwiftUI

struct ContentView: View {
    @State private var opponentChoice = ""
    @State private var yourChoice = ""
    @State private var result = ""
    
    var body: some View {
        VStack {
            Text("系統出拳：\(opponentChoice)")
                .font(.system(size: 50))
            Text("你出拳：\(yourChoice)")
            .font(.system(size: 50))
            Text("结果：\(result)")
            .font(.system(size: 50))
            HStack {
                Button(action: {
                    yourChoice = "剪刀"
                    playGame()
                }) {
                    Text("剪刀")
                        .font(.system(size: 50))
                        .padding()
                        .background(Color.blue)
                        .foregroundColor(.white)
                        .cornerRadius(10)
                }
                
                Button(action: {
                    yourChoice = "石頭"
                    playGame()
                }) {
                    Text("石頭")
                        .font(.system(size: 50))
                        .padding()
                        .background(Color.green)
                        .foregroundColor(.white)
                        .cornerRadius(10)
                }
                
                Button(action: {
                    yourChoice = "布"
                    playGame()
                }) {
                    Text("布")
                        .font(.system(size: 50))
                        .padding()
                        .background(Color.red)
                        .foregroundColor(.white)
                        .cornerRadius(10)
                }
            }
        }
    }
    
    func playGame() {
        let choices = ["剪刀", "石頭", "布"]
        opponentChoice = choices.randomElement()!
        
        if yourChoice == opponentChoice {
            result = "平局"
        } else if (yourChoice == "剪刀" && opponentChoice == "布") ||
                    (yourChoice == "石頭" && opponentChoice == "剪刀") ||
                    (yourChoice == "布" && opponentChoice == "石頭") {
            result = "你赢了"
        } else {
            result = "你输了"
        }
    }
}

struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}


  ```
   
  </tr>
</table>
