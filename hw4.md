<h1>HW4</h1>
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/didi816l/yzu-1101422-swift/main/hw4photo.jpeg">
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
