# CONSUMER

- Là một widget trong Flutter, được sử dụng để cập nhật giao diện người dùng khi có sự thay đổi trong dữ liệu.

- Bao gồm 2 thành phần chính :
  
  - `builder` : là một hàm callback được gọi khi có sự thay đổi trong đối tượng `ChangeNotifier`. Method này trả về một Widget.
    
    - `BuildContext` : 
    
    - `ChangeNotifier` : 
    
    - `Widget` : 
  
  - `child` : Được tạo một lần duy nhất khi `Consumer` khởi tạo. Được sử dụng để giữ các thuộc tính không thay đổi của `Consumer`, giúp tối ưu hóa hiệu suất.

```dart
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';

class ProductListScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Product List'),
      ),
      body: Consumer<ProductList>(
        builder: (context, productList, child) {
          return ListView.builder(
            itemCount: productList.products.length,
            itemBuilder: (context, index) {
              return ListTile(
                title: Text(productList.products[index].name),
              );
            },
          );
        },
        child: SizedBox(height: 100,),
      ),
    );
  }
}
```