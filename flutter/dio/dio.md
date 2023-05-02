# [DIO]([dio | Dart Package](https://pub.dev/packages/dio/install))

### 1. Giới Thiệu

- Hỗ trợ gửi và nhận các request HTTP. 

- Có các tính năng xử lý lỗi, hỗ trợ cancel request, cache...

### 2. BaseOption

- Là một lớp được cung cấp bởi Dio để cấu hình các option mặc định cho các yêu cầu HTTP

- Các thuộc tính của `BaseOptions` bao gồm: 
  
  - `baseUrl` : Địa chỉ host của server cần truy vấn.
  
  - `connectTimeout` : Thời gian tối đa cho phép để kết nối tới máy chủ.
  
  - `receiveTimeout` : Thời gian tối đa cho phép để nhận response từ máy chủ.
  
  - `sendTimeout` : Thời gian tối đa cho phép để gửi request tới máy chủ.
  
  - `headers` : Các header được thêm vào mỗi yêu cầu.
  
  - `extra` : Các thông tin bổ sung khác như tên người dùng, token, ...
  
  ```dart
  final options = BaseOptions(
    baseUrl: 'https://example.com/api',
    connectTimeout: 5000, // 5 seconds
    receiveTimeout: 5000, // 5 seconds
    headers: {
      'Accept': 'application/json',
      'Content-Type': 'application/json',
    },
  );
  
  final dio = Dio(options);
  ```

- **Lưu ý :** Ngoài các truyền option lúc khởi tạo `Dio`, khi gọi các method của `Dio` , các method này cũng nhận một option. Nếu option được truyền vào method, nó sẽ ưu tiên hơn so với option truyền vào contructor của `Dio`

### 3. Phương Thức Get

- Trong Dio, phương thức `get` có các tham số như sau: 
  
  ```dart
  Future<Response<T>> get<T>(
    String path, {
    dynamic data,
    Options? options,
    CancelToken? cancelToken,
    ProgressCallback? onReceiveProgress,
    Map<String, dynamic>? queryParameters,
    String? baseUrl,
    bool? followRedirects,
  });
  ```
  
  - `path` : url của API
  
  - `data`: Dữ liệu được gửi cùng với yêu cầu.
  
  - `options` : Là một BaseOption dành riêng lượt gọi method get, nó sẽ bỏ quả option của `Dio`
  
  - `cancelToken` : Dùng để huỷ request.
  
  - `onReceiveProgress` : Được gọi khi nhận respone, giúp theo dõi quá trình nhận dữ liệu.
  
  - `queryParameters` : Các tham số truy vấn được thêm vào path.
  
  - `baseUrl` : (HOST), Địa chỉ cơ sở của API, nếu được sử dụng. Thông thường đã được chỉ định trong BaseOption.
  
  - `followRedirects` : Chỉ định liệu Dio có tự động chuyển hướng đến các URL khác không.

- Lưu ý : các tham số này là tùy chọn, bạn có thể sử dụng chỉ một vài trong số chúng.

### 4. Phương Thức Post

- Các tham số của phương thức post gần như tương tự so với phương thức `get`. 
  
  ```dart
  Future<Response<T>> post<T>(
    String path, {
    dynamic data,
    Options? options,
    CancelToken? cancelToken,
    ProgressCallback? onSendProgress,
    ProgressCallback? onReceiveProgress,
    Map<String, dynamic>? queryParameters,
    String? baseUrl,
    bool? followRedirects,
  });
  ```
  
  - `onSendProgress` : Được gọi khi gửi yêu cầu, giúp theo dõi tiến trình gửi dữ liệu.