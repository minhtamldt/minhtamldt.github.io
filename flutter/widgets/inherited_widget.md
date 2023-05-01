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

```dart
import 'package:flutter/material.dart';

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

class ChildTwo extends StatelessWidget {
  final String colorOfHair;
  const ChildTwo({Key? key, required this.colorOfHair}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Center(child: Text(colorOfHair));
  }
}

```

-  **Hạn Chế :** Đối với cấu trúc cây widget lớn và phức tạp. Chúng ta không thể cứ mỗi widget lại tạo một contructors tương ứng để truyền data xuống. Nhưng vậy rất phức tạp và việc bảo trì mở rộng rất khó khăn. 

    
