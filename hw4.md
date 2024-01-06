<h1>HW4</h1>
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/didi816l/yzu-1101422-swift/main/IMG_0369.jpg">
    </td>
    <td> 
      
```swift
import SwiftUI
/*
struct CardView:View{
    @State var currentCard = 0
    var body: some View{
        VStack{
            VStack{
                Text(myDictionary[currentCard].term)
                    .font(.title)
                    .padding(.all,10)
                Text(myDictionary[currentCard].description)
                    .font(.body)
                    .foregroundColor(.blue)
                    .padding(.all,10)
            }
            .frame(minWidth:0,idealWidth:100,maxWidth:300,minHeight: 0,idealHeight: 100,maxHeight: 300,alignment: .center)
            .background(Color.green)
            .onTapGesture {
                if currentCard<myDictionary.count-1{
                    currentCard+=1
                }else{
                    currentCard=0
                }
            }
            Text("點擊看下一張")
                .padding(.all,10)
        }
    }
}
struct WelcomeView:View{
    @AppStorage("UserName") var UserName:String = ""
    var body:some View{
        VStack{
            Text(UserName.isEmpty ? "" : UserName).font(.system(size:30))
            Image("Apple")
                .resizable()
                .aspectRatio( contentMode: .fit)
            Text("是時候該換電腦了！")
                .fontWeight(.heavy)
                .lineSpacing(20)
                .font(.system(size:32.0))
                .foregroundColor(.white)
                .frame(width:350,height:150,alignment: .center)
                .background(Color.blue)
                .cornerRadius(20.0)
                .multilineTextAlignment(.center)
        }
    }
}

struct SettingView: View {
    let displayFontType = [".default",".rounded",".monspaced",".serif"]
    @State var displayFontSelected = 0
    @State var IsDeepScheme = false
    @State var colorArray:Array = [255.0,255.0,255.0]
    @State var stepperValue = 0
    @State var sliderValue = 0.0
    @State var date = Date()
    @AppStorage("UserName") var UserName:String = ""
    
    var body: some View {
        NavigationView{
            Form(content:{
                Section(content:{
                    TextField("請輸入您的名字",text:$UserName)
                    
                },header:{
                    Text("使用者名稱")
                })
                Section(header:Text("字型設定"),content:{
                    Picker(selection: $displayFontSelected,
                           label:Text("字型選擇(\(displayFontSelected))"),
                           content: {
                        ForEach(0..<displayFontType.count,
                                id:\.self,
                                content:{
                            Text(self.displayFontType[$0])
                        })
                    })    
                })
                Section(header:Text("背景風格"),
                        content:{
                    Toggle(isOn: $IsDeepScheme,
                           label:{Text("深色(\(String(IsDeepScheme)))")
                        
                    })
                })
                Section(header:Text("計數器")){
                    Stepper("Stepper(\(stepperValue))",
                            onIncrement:{stepperValue+=1},
                            onDecrement:{stepperValue-=1}
                    )
                }
                Section(header:Text("滑桿(\(sliderValue,specifier:"%.2f"))")){
                    Slider(value:$sliderValue,in:0...1)
                }
                Section(header: Text("日期"), content: {
                    DatePicker("\(date.formatted(date: .numeric, time: .omitted))", selection: $date, displayedComponents: [.date])
                })
            }
            )
            .navigationBarTitle("Settings")
        }
    }
}*/
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
struct Course:Identifiable{
    var id=UUID()
    var name:String
    var image:String
    var description:String
    var isFeature:Bool
}

var courses = [
    Course(name:"iMac",image:"iMac",description: "$44900",isFeature: true),
    Course(name:"Mac mini",image:"mini",description: "$18900",isFeature: true),
    Course(name:"Mac Studio",image:"studio",description: "$64999",isFeature: false),
    Course(name:"MacBook Air",image:"air",description: "$42900",isFeature: false),
    Course(name:"MacBook Pro",image:"pro",description: "$54900",isFeature: true)
    
]

struct BasicImageRow:View{
    var thisCourse:Course
    var body:some View{
        HStack{
            Image(thisCourse.image)
                .resizable()
                .frame(width:40,height:40)
                .cornerRadius(5)
            Text(thisCourse.name)
        }
    }
}
struct FullImageRow:View{
    var thisCourse:Course
    var body:some View{
        ZStack{
            Image(thisCourse.image)
                .resizable()
                .frame(height:180)
                .aspectRatio(contentMode: .fit)
                .cornerRadius(10)
                .overlay(
                    Rectangle()
                        .foregroundColor(.black)
                        .cornerRadius(10)
                        .opacity(0.2)
                )
            Text(thisCourse.name)
                .font(.system(.title))
                .fontWeight(.black)
                .foregroundColor(.white)
                .offset(x:0.0,y:50.0)
        }
    }
}

struct CourseDetailView:View{
    @Environment(\.presentationMode) var presentationMode
    var thisCourse:Course
    var body: some View{
        ScrollView{
            VStack{
                Image(thisCourse.image)
                    .resizable()
                    .aspectRatio(contentMode:.fill)
                    .clipped()
                Text(thisCourse.name)
                    .font(.system(.title, design: .rounded))
                    .fontWeight(.black)
                Spacer()
                Text(thisCourse.description)
                    .font(.system(.subheadline,design: .rounded))
                    .fontWeight(.light)
                Spacer()
            }
        }
        .overlay(
        HStack{
            Spacer()
            VStack{
                Button(action:{
                    self.presentationMode.wrappedValue.dismiss()
                },label: {
                    Image(systemName: "chevron.down.circle.fill")
                        .font(.largeTitle)
                        .foregroundColor(.white)
                })
                .padding(.trailing,20)
                .padding(.top,40)
                Spacer()
            }
        }
        )
    }
}

struct CourseListView:View{
    @State var showDetailView = false
    @State var selectedCourse:Course?
    var body: some View{
        NavigationView{
            List(courses){ 
                courseItem in
                if courseItem.isFeature
                {
                   FullImageRow(thisCourse: courseItem)
                    .onTapGesture{
                        self.showDetailView = true
                        self.selectedCourse = courseItem
                    }
                }else{
                    BasicImageRow(thisCourse: courseItem)
                        .onTapGesture {
                            self.showDetailView = true
                            self.selectedCourse = courseItem
                        }
                }
            }
            .sheet(item:self.$selectedCourse){ thisCourse in
                CourseDetailView(thisCourse:thisCourse)
            }
            .navigationBarTitle("動畫列表")
        }
    }
}
struct TermAndDescription:Identifiable{
    var id = UUID()
    var term:String
    var description:String
}

var myDictionary = [
    TermAndDescription(term:"R2 Score",description: "1"),
    TermAndDescription(term:"R2 Score",description: "2"),
    TermAndDescription(term:"R2 Score",description: "3"),
    TermAndDescription(term:"R2 Score",description: "4")
    
]



  ```
  </tr>
</table>
