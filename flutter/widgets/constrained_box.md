# CONSTRAINED BOX

- **Là một widget trong Flutter cho phép bạn giới hạn kích thước của widget con của nó.**

- Widget này sẽ ràng buộc kích thước tối thiểu và tối đa của widget con bên trong của nó dựa trên các tham số được cung cấp.

```dart
ConstrainedBox(
  constraints: BoxConstraints(
    minWidth: 100,
    maxWidth: 200,
    minHeight: 50,
    maxHeight: 100,
  ),
  child: childWidget,
)
```

- `constraints` : Là một đối tượng `BoxConstraints` xác định giới hạn kích thước của widget con.

- Bạn có thể chỉ định một số giá trị kích thước tối thiểu hoặc tối đa bằng cách thiết lập chúng thành `null` 
