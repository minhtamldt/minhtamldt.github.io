# INHERITED WIDGET

### 1. Truyền Data Giữa Các Widget

- **Đặt Vấn Đề** : 
  
  - Ta có một cấu trúc Widget như sau :  `ParentWidget` -> `ChildOneWidget `-> `ChildTwoWidget`
  
  - **Vấn đề** : Đứng từ vị trí của ChildTwoWidget làm sao để nhận data của ParentWidget.

- **Giải Pháp :**
  
  - Sử dụng kĩ thuật `Passing state down`  : Nghĩa là truyền trạng thái từ trên xuống. 
  
  - Ví dụ trong vấn đề trên. Từ `ParentWidget` sẽ truyền data xuống cho `ChildOneWidget`, sau đó từ `ChildOneWidget` sẽ truyền data xuống cho `ChildTwoWidget`

- **Triển Khai :**
  
  - Mỗi widget đều cần có khai báo contructors chứa tham số là data cần truyền xuống child.
  
  - ChildTwo widget, tạo contructor chứa `colorOfHair` để nhận data.
  
  ```dart
  class ChildTwo extends StatelessWidget {
    final String colorOfHair;
    const ChildTwo({Key? key, required this.colorOfHair}) : super(key: key);
  
    @override
    Widget build(BuildContext context) {
      return Center(child: Text(colorOfHair));
    }
  }
  ```
  
  - ChildOne Widget, cũng tạo contructor chứa `colorOfHair`. Và truyền giá trị này xuống cho ChildTwo Widget. 
  
  ```dart
  class ChildOne extends StatelessWidget {
  
    final String colorOfHair;
  
    const ChildOne({Key? key, required this.colorOfHair}) : super(key: key);
  
    @override
    Widget build(BuildContext context) {
      return ChildTwo(
        colorOfHair: colorOfHair,
      );
    }
  }
  ```
  
  - Từ ParentWidget, chúng ta truyền data cho ChildOneWidget
  
  ```dart
  class Parent extends StatefulWidget {
    const Parent({Key? key}) : super(key: key);
  
    @override
    State<Parent> createState() => _ParentState();
  }
  
  //Passing state down
  class _ParentState extends State<Parent> {
  
    String colorOfHair = 'black';
  
    @override
    Widget build(BuildContext context) {
      return ChildOne(
        colorOfHair: colorOfHair,
      );
    }
  }
  ```

-  **Hạn Chế :** Đối với cấu trúc cây widget lớn và phức tạp. Chúng ta không thể cứ mỗi widget lại tạo một contructors tương ứng để truyền data xuống. Nhưng vậy rất phức tạp và việc bảo trì mở rộng rất khó khăn. 



### 2. Inherited Widget

<img src="https://baoflutter.com/wp-content/uploads/2020/09/inherited_widget.png" title="" alt="NGHỆ THUẬT FLUTTER : CÁC CÁCH QUẢN LÝ STATE TRONG FLUTTER - InheritedWidget  - Báo Flutter" data-align="center">

- Widget này ra đời để giải quyết vấn đề trên. Nó giúp một widget con có thể truy cập data có widget mà không cần phải tạo bất cứ contructors nào để hứng data. 

- Cấu trúc cây widget mới nếu dùng `Inherited Widget`
  
  - `MyInherited Widget` => `ParentWidget` => `ChildOneWidget` => `ChildTwoWidget`
  
  - Lúc này, `MyInherited Widget` nó sẽ quả lý data cho cả cây widget.

- Triển khai : 
  
  - Viết một custom `InheritedWidget` : 
  
  ```dart
  class FamilyProvider extends InheritedWidget {
  
    final String colorOfHair;
    const FamilyProvider({super.key, required Widget child, required this.colorOfHair}) : super(child: child);
  
    @override
    bool updateShouldNotify(covariant InheritedWidget oldWidget) {
      //True, mong muốn update UI cho widget nào có truy cập đến FamilyProvider
      return true;
    }
  }
  ```
  
  - Wrap `InheritedWidget` vào `ParentWidget`
  
  ```dart
  @override
    Widget build(BuildContext context) {
      return MaterialApp(
        title: 'Flutter Demo',
        theme: ThemeData(
          // This is the theme of your application.
          //
          // Try running your application with "flutter run". You'll see the
          // application has a blue toolbar. Then, without quitting the app, try
          // changing the primarySwatch below to Colors.green and then invoke
          // "hot reload" (press "r" in the console where you ran "flutter run",
          // or simply save your changes to "hot reload" in a Flutter IDE).
          // Notice that the counter didn't reset back to zero; the application
          // is not restarted.
          primarySwatch: Colors.blue,
        ),
        home: const Scaffold(
        //Wrap FamilyProvider vào ParentWidget.
          body: FamilyProvider(
            colorOfHair: 'black',
            child: Parent(),
          ),
        ),
      );
    }
  ```
  
  - Truy cập data từ `InheritedWidget` 
  
  ```dart
  class ChildWidget extends StatelessWidget {
    const ChildWidget({Key? key}) : super(key: key);
  
    @override
    Widget build(BuildContext context) {
      //get familyProvider
      final familyProvider = context.dependOnInheritedWidgetOfExactType<FamilyProvider>();
      //get value
      final String colorOfHair = familyProvider!.colorOfHair;
      return Text(colorOfHair);
    }
  }
  ```
  
  
