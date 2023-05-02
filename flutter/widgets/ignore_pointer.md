# Ignore Pointer

- Là một widget được sử dụng để tạm thời vô hiệu hóa tương tác của người dùng với các widget con của nó.

- Các thuộc tính của `IgnorePointer` bao gồm :
  
  - `ignoring` : liệu các widget con của `IgnorePointer` có bị vô hiệu hóa hay không 
  
  - `ignoringSemantics` : liệu `IgnorePointer` có gửi thông báo tương tác với người dùng (semantics) cho các widget con của nó hay không.

```dart
class MyWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return IgnorePointer(
      ignoring: true,
      child: Container(
        color: Colors.blue,
        width: 200.0,
        height: 200.0,
      ),
    );
  }
}
```
