# INTRINSIC HEIGHT

- **Được sử dụng khi bạn muốn các widget con của nó có cùng chiều cao, mặc dù chúng có nội dung khác nhau**

- Nó hoạt động bằng cách tính toán chiều cao tối thiểu và tối đa của các widget con. Sau đó sử dụng giá trị này để thiết lập kích thước cho tất cả các widget con để chúng có cùng chiều cao.

- Bạn có thể sử dụng `IntrinsicHeight` như sau: 
  
  ```dart
  IntrinsicHeight(
    child: Row(
      children: [
        Expanded(
          child: Container(
            child: Text('Widget 1'),
          ),
        ),
        Expanded(
          child: Container(
            child: Text('Widget 2\nMultiline Text'),
          ),
        ),
      ],
    ),
  )
  ```

- **Lưu ý :  rằng `IntrinsicHeight` có thể làm giảm hiệu suất của ứng dụng nếu nó được sử dụng quá nhiều, vì nó phải tính toán lại kích thước của các widget con mỗi khi chúng thay đổi.**
