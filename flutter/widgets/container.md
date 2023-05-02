# CONTAINER

- **Là một widget hiển thị một hình chữ nhật với kích thước và thuộc tính được xác định bởi người dùng.**

- Một số thuộc tính quan trọng của `Container` bao gồm: 
  
  - `color`: Màu sắc của container.
  
  - `width` và `height`: Chiều rộng và chiều cao của container.
  
  - `margin`: Khoảng cách giữa container và các widget khác xung quanh nó.
  
  - `padding`: Khoảng cách giữa các **nội dung bên trong** container và biên của container.
  
  - `alignment`: Cách thức căn chỉnh nội dung bên trong container.
  
  - `decoration`: Trang trí của container, bao gồm các thuộc tính như border, borderRadius, boxShadow và gradient.

- Một ví dụ sử dụng Container :
  
  ```dart
  Container(
    margin: EdgeInsets.all(16.0),
    padding: EdgeInsets.all(8.0),
    decoration: BoxDecoration(
      color: Colors.blue,
      borderRadius: BorderRadius.circular(10.0),
    ),
    child: Text(
      'Hello World!',
      style: TextStyle(
        color: Colors.white,
        fontSize: 24.0,
        fontWeight: FontWeight.bold,
      ),
    ),
  )
  ```
  
  - Trong ví dụ này, chúng ta sử dụng `Container` để tạo một hộp xung quanh văn bản "Hello World!".
  
  - Thuộc tính `margin` xác định khoảng cách giữa container và các widget xung quanh nó, còn `padding` xác định khoảng cách giữa nội dung bên trong container và các biên của container.
  
  - Thuộc tính `decoration` được sử dụng để thiết lập một số trang trí cho container, bao gồm màu sắc và bo góc.
  
  - Cuối cùng, chúng ta đặt văn bản bên trong container bằng cách sử dụng thuộc tính `child`.
