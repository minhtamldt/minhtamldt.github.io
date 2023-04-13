# Phần 1: Quản lý state bằng Provider trong Flutter

1. **Thêm Thư Viện Provider.**
   
   Bước 1:  Vào file `pubspec.yaml` , tìm kiếm `dependencies` và thêm `provider`
   
   ```dart
   dependencies:
     flutter:
       sdk: flutter
     provider: ^5.0.0 //tuỳ thuộc vào version mới nhất tại thời điẻm của bạnBước 2: 
   ```

        Bước 2: Save file, thực hiện Pug Get để kéo thư viện về.

2. **Phân Tích Cơ Chế Hoạt Động.**
   
   Chúng ta lấy ví dụ về chuỗi cung ứng hàng hoá gồm 3 đối tượng tham gia: 
   
   + Nhà cung cấp `(class YourClass extend ChangeNotifer)`
     
     + Mỗi khi có hàng mới, gọi `notifyListeners` để thông báo có hàng cho phân phối chuyển đến người sử dụng
   
   + Nhà phân phối `(ChangeNotifierProvider, MultiProvider)`
     
     + Kết nối nhà cung cấp với người sử dụng
   
   + Người sử dụng `(Consumer, context.watch/context.read)`

3. Ví dụ
   
   ```dart
   class CounterProvider extend ChangeNotifer {
       int _counter = 100;
       int get counter => _counter;
   
       void add(){
           _counter ++ //cho counter tăng thêm 1.
           notifyListeners(); //thông báo cho nhà phần phối. 
       }
   }
   ```
   
   Trên UI, ví dụ ở đây là method `main()`
   
   ```dart
   main(){
       runApp(
           ChangeNotifierProvider( //Nhà phân phối.
               create: (_) => CounterProvider()),
               child: MaterialApp(
                   home: CounterHomePage(),    
               ) //Nhà cung cấp
           )
       )
   }
   ```
   
   Theo dõi sự thay đổi của giá trị với `context.watch`
   
   ```dart
   class CounterHome extends StatelessWidget {
       @override
       Widget build(BuildContext context) {
           return Scaffold(
               child: Center(
                   child: Text(
                       //Text dõi sự thay đổi của counter để update lên UI
                       context.watch<CounterProvider>().counter.toString()
                   )
               )
           )
       }
   }
   ```
   
   Cập nhật giá trị với `context.read`
   
   ```dart
   onPressed:() {
       context.read<CounterProvider>().add()
   }
   ```
   
   