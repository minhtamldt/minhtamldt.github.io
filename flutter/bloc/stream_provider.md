# STREAM PROVIDER

### 1. Chức Năng

- Widget này nằm trong gói `Provider`.

- Cung cấp dữ liệu  từ một Stream có các widget trong cây.

### 2. Thuộc Tính

- `create`: Hàm để tạo `Stream` mà `StreamProvider` sẽ sử dụng để cập nhật dữ liệu của nó. Hàm này phải trả về một `Stream` để `StreamProvider` có thể đăng ký và lắng nghe.

- `initialData`: Dữ liệu ban đầu để cung cấp cho các widget khi `Stream` chưa phát ra bất kỳ dữ liệu nào.

- `updateShouldNotify`: Hàm được sử dụng để kiểm tra xem liệu các giá trị mới được phát ra từ `Stream` có cần phải cập nhật lại các widget không. Mặc định là có.

### 3. Ví Dụ

```dart
Stream<int> countStream() async* {
  int count = 0;
  while (true) {
    await Future.delayed(Duration(seconds: 1));
    yield count++;
  }
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: StreamProvider<int>.value(
        value: countStream(),
        initialData: 0,
        child: MyHomePage(),
      ),
    );
  }
}

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    int count = context.watch<int>();
    return Scaffold(
      appBar: AppBar(
        title: Text("Counter"),
      ),
      body: Center(
        child: Text(
          "Count: $count",
          style: TextStyle(fontSize: 24.0),
        ),
      ),
    );
  }
}

```