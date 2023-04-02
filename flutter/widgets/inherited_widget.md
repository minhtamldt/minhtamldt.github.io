# Inherited Widget

1. **Truyền Data Giữa Các Widget.**
   
   - Giải pháp : Sử dụng kĩ thuật "Passing state down". Nghĩa là mỗi widget con cần tạo các contructors để hứng data muốn truyền từ widget cha. 
     
     =>  Cách này có quá nhiều bất cập :
     
     - Khi mà mỗi widget lại phải tạo contructors để hứng. Trong tình huống data thay đổi chúng ta lại phải đổi contructor.
     
     - Khi đổi layout chúng ta cũng phải thay đổi contructor
     
     - Trường hợp khoảng cách giữa 2 widget quá lớn thì lại phải tạo contructors rất nhiều.

2. **Inherited Widget**
   
   - Là nơi chứa data chung cho một nhóm widgets, thay vì mỗi widget cần contrucotors để truyền dữ liệu
   
   - Widget sẽ lưu data chung khi các widget khác cần dùng thì truy cập đến nó và lấy data.

3. **Triển Khai InheritedWidget Widget**
   
   - Bước 1: Tạo subclass của `InheritedWidget`. Trong class này, bạn nên định nghĩa dữ liệu cần được chia sẻ giữa các widget và phương thức để truy cập dữ liệu đó.
     
     ```dart
     class MyInheritedWidget extends InheritedWidget {
       final int data;
     
       MyInheritedWidget({
         Key key,
         @required this.data,
         @required Widget child,
       }) : super(key: key, child: child);
     
       static MyInheritedWidget of(BuildContext context) {
         return context.dependOnInheritedWidgetOfExactType<MyInheritedWidget>();
       }
     
       @override
       bool updateShouldNotify(MyInheritedWidget oldWidget) {
         return data != oldWidget.data;
       }
     }
     ```
   
   - Bước 2: Bọc widget cha của các widget cần truy cập dữ liệu bằng `MyInheritedWidget`
     
     ```dart
     class MyApp extends StatelessWidget {
       @override
       Widget build(BuildContext context) {
         return MyInheritedWidget(
           data: 42,
           child: MaterialApp(
             title: 'MyApp',
             home: MyHomePage(),
           ),
         );
       }
     }
     ```
   
   - Bước 3: Truy cập dữ liệu bằng phương thức `of` của `MyInheritedWidget` trong các widget con
     
     ```dart
     class MyApp extends StatelessWidget {
       @override
       Widget build(BuildContext context) {
         return MyInheritedWidget(
           data: 42,
           child: MaterialApp(
             title: 'MyApp',
             home: MyHomePage(),
           ),
         );
       }
     }
     ```

4. **Method  `updateShouldNotify`**
   
   - Khi tạo một subclass từ `InheritedWidget` , method này bắt buộc override.
   
   - Nó xác định liệu rằng những widget con của nó có bị build lại khi nó được build lại hay không. Để tránh việc các widget luôn bị build lại ảnh hưởng performace

    
