# DIO

install : https://pub.dev/packages/dio/install

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

### 5. Đối tượng Response

- Nó đại diện cho kết quả trả về từ server. Nó bao gồm.
  
  - `status code` : trạng thái của request.
  
  - `header`  : những thông tin liên quan đến request.
  
  - `data` : phần dữ liệu chính 
    
    
  
  ```dart
  import 'package:dio/dio.dart';
  
  void getData() async {
    try {
      Response response = await Dio().get('https://jsonplaceholder.typicode.com/todos/1');
      print(response.statusCode); // In ra mã trạng thái, ví dụ 200
      print(response.headers); // In ra tiêu đề
      print(response.data); // In ra dữ liệu phản hồi từ server
    } catch (e) {
      print(e);
    }
  }
  ```

### 6. Thông Tin Thêm

1. LogInterceptor
   
   - Là một interceptor được sử dụng để ghi log các request và response.
   
   - Khi sử dụng `LogInterceptor`, mỗi lần gửi một request bằng `Dio`, ta sẽ nhận được các thông tin như sau: 
     
     - Thời điểm bắt đầu gửi request.
     
     - Request method, URL, headers, body.
     
     - Thời điểm nhận được response.
     
     - Response status code, headers, body.
     
     - Thời gian request/response.
   
   - Để sử dụng `LogInterceptor`, ta có thể tạo một instance mới và thêm nó vào danh sách các interceptors của `Dio` như sau:
   
   ```dart
   import 'package:dio/dio.dart';
   
   void main() {
     final dio = Dio();
     dio.interceptors.add(LogInterceptor());
     // ...
   }
   ```
   
   - Sau đó, mỗi lần gửi request bằng `Dio`, ta sẽ nhận được các thông tin log được ghi lại.

2. InterceptorsWrapper
   
   - Cung cấp một cách tiện lợi để định nghĩa các interceptors bằng cách kế thừa và override các phương thức.
   
   - Bạn có thể định nghĩa một interceptor bao gồm nhiều phương thức như :
     
     - onRequest
     
     - onResponse
     
     - onError
     
     - onRequestError
     
     - onResponseError
   
   - Ví dụ, nếu bạn muốn thêm header cho tất cả các request, bạn có thể định nghĩa một interceptor bằng cách kế thừa `InterceptorsWrapper` và override phương thức `onRequest` như sau :
     
     ```dart
     import 'package:dio/dio.dart';
     
     class MyInterceptor extends InterceptorsWrapper {
       @override
       Future onRequest(RequestOptions options, RequestInterceptorHandler handler) async {
         options.headers.addAll({"Authorization": "Bearer $myToken"});
         return super.onRequest(options, handler);
       }
     }
     
     void main() {
       final dio = Dio();
       dio.interceptors.add(MyInterceptor());
       // ...
     }
     ```
     
     