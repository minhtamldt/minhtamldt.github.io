# LAYOUT BUILDER

- **Là một widget trong Flutter cho phép bạn xây dựng layout dựa trên kích thước của widget cha.**

- Bao gồm các tham số : 
  
  - `builder` : Hàm callback này phải trả về một widget, và kích thước của widget được trả về phải thỏa mãn với `BoxConstraints` đã cho.
    
    - `BuildContext` :
    
    - `BoxConstraints` : Đối tượng này chứa thông tin về kích thước `tối đa` và `tối thiểu` mà widget cha có thể có
      
      
  
  ```dart
  LayoutBuilder(
    builder: (BuildContext context, BoxConstraints constraints) {
      return Container(
        width: constraints.maxWidth,
        height: constraints.maxWidth,
        color: Colors.blue,
      );
    },
  )
  ```
  
  
  
  
