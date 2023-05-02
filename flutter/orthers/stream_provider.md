# STREAM PROVIDER

- Được sử dụng để cung cấp một `Stream` cho các widget con của nó và tự động cập nhật lại chúng khi `Stream` có sự thay đổi.

- Các thành phần của `StreamProvider` bao gồm:
  
  - `stream` : được cung cấp cho các widget con của `StreamProvider`
  
  - `initialData`: Dữ liệu khởi tạo được sử dụng cho widget con của `StreamProvider` cho đến khi `Stream` được lấy ra lần đầu tiên.
  
  - `updateShouldNotify`: Hàm được sử dụng để xác định xem liệu widget con của `StreamProvider` có cần được cập nhật lại hay không khi `Stream` thay đổi.