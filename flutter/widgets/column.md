### COLUMN

1. **KHÁI NIỆM**
   
   - Widget dùng để sắp xếp các widget con theo chiều dọc
   
   - Widget con của Column sẽ được xếp chồng lên nhau theo thứ tự được liệt kê, từ trên xuống dưới.
   
   ✍️ Ví dụ : 
   
   ```dart
   Column(
     children: <Widget>[
       Text('Widget con 1'),
       Text('Widget con 2'),
       Text('Widget con 3'),
     ],
   )
   ```

2. **THUỘC TÍNH**
   
   | STT | Thuộc Tính         | Mô Tả                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   |:---:|:------------------ |:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | 1   | mainAxisAlignment  | Chỉ định cách sắp xếp các widget con theo chiều **dọc**<br/>- **start (default)** : các widget nằm trên cùng của cột.<br/>- **center** : nằm giữa cột <br/>- **end** : nằm dưới cùng của cột <br/>- **spaceBetween** : các widget có khoảng cách với nhau (các khoảng cách đều nhau)<br/>- **spaceAround** : bên trên và bên dưới widget đều có khoảng cách, nếu các widget đối diện nhau thì khoảng cách này **không tăng lên**<br/>- **spaceEvenly** : bên trên và bên dưới widget đều có khoảng cách, nếu các widget đối diện nhau thì khoảng cách này **tăng lên** |
   | 2   | crossAxisAlignment | Chỉ định cách sắp xếp các widget con theo chiều **ngang**<br/>- **start (default)** : các widget nằm bên trái.<br/>- **center** : nằm giữa cột <br/>- **end** : nằm bên phải cột <br/>- **stretch** : widget con sẽ được kéo dãn theo chiều ngang của cột để lấp đầy không gian<br/>- **baseline** : widget con sẽ được kéo dãn theo chiều ngang của cột để lấp đầy không gian**<br/>                                                                                                                                                                                  |
   | 3   | mainAxisSize       | chỉ định chiều cao của Column trong chiều dọc, <br/>Các giá trị có thể sử dụng là <br/>- **MainAxisSize.max** (mặc định) : Chiếm toàn bộ chiều cao của parent <br/>- **MainAxisSize.min.** : Chiều cao vừa đủ với content bên trong cột.                                                                                                                                                                                                                                                                                                                               |

3. CODE SAMPLE
   
   ```dart
   import 'package:flutter/material.dart';
   
   void main() {
     runApp(const MyApp());
   }
   
   class MyApp extends StatelessWidget {
     const MyApp({super.key});
   
     // This widget is the root of your application.
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
         home: Scaffold(
           body: SafeArea(
             child: Center(
               child: Container(
                 width: 200, //set width để thể hiện các thuộc tính của colum rõ ràng hơn
                 color: Colors.black12,
                 child: Column(
                   mainAxisAlignment: MainAxisAlignment.end,
                   crossAxisAlignment: CrossAxisAlignment.center,
                   mainAxisSize: MainAxisSize.min,
                   children: [
                     Container(
                       width: 100,
                       height: 100,
                       color: Colors.red,
                     ),
                     Container(
                       width: 100,
                       height: 100,
                       color: Colors.yellow,
                     ),
                     Container(
                       width: 100,
                       height: 100,
                       color: Colors.green,
                     ),
                   ],
                 )
               ),
             ),
           ),
   
         ),
       );
     }
   }
   
   
   ```
