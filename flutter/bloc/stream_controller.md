1. **Khái Niệm**
   
   - Tạo ra nguồn dữ liệu và ở nơi khác trong App có thể lắng nghe.

2. **Ví Dụ**
   
   - Bước 1: Khởi tạo đối tượng StreamController
   
   - Bước 2: Đổ dữ liệu vào StreamController
   
   - Bước 3: Đăng kí để nhận thông báo khi mà StreamController có thay đổi dữ liệu.
   
   - Bước 4: Đóng StreamController khi không còn dùng nữa. Để giải phóng tài nguyên và tránh rò rỉ bộ nhớ
     
     ```dart
     import 'dart:async';
     
     // Bước 1: Khởi tạo đối tượng StreamController
     StreamController<int> _counterController = StreamController<int>();
     
     //Bước 2: Đổ dữ liệu vào StreamController
     _counterController.sink.add(1);
     
     //Bước 3: Đăng kí để nhận thông báo khi mà StreamController có thay đổi dữ liệu.
     _counterController.stream.listen((event) {
       print('Received event: $event');
     });
     
     //Bước 4: Đóng StreamController khi không còn dùng nữa.
     _counterController.close();
     ```

3. **Thành Phần**
   
   - **sink** : được sử dụng để phát ra các sự kiện tới luồng
   
   - **stream** : là một đối tượng `Stream` mà bạn có thể lắng nghe để xử lý các sự kiện đó

4. **Cách Dùng**
   
   - Single subscription : 
   
   - Broadcast subscription: 

5. **Một Số Lưu Ý**
   
   - Đóng StreamController khi không cần dùng thiết để giải phóng tài nguyên và tránh rò rỉ bộ nhớ.
   
   - Khi dùng **single subscription** thì không đăng kí nhièu listener.
   
   - Khi dùng **Broadcast subscription** cần quan tâm đến vấn đề hiệu suất.
   
   - Khi dùng StreamController trong StatefulWidget, hãy đảm bảo nó được khi **State** bị xoá