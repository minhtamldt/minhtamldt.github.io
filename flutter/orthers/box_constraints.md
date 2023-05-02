# BOXCONSTRAINTS

### 1. Chức Năng

- Được sử dụng để **giới hạn kích thước** của một widget

### 2. Thuộc Tính

- `minWidth` và `maxWidth`: Giới hạn kích thước của widget theo chiều ngang.

- `minHeight` và `maxHeight`: Giới hạn kích thước của widget theo chiều dọc.

- `tighten`: Xác định xem liệu `BoxConstraints` có phải là giới hạn chặt chẽ hay không. Nếu `tighten` được đặt thành `true`, Flutter sẽ giả định rằng widget không được phép thay đổi kích thước của nó.

### 3. Phương Thức

- `BoxConstraints.expand()` : widget có thể được mở rộng ra tối đa về kích thước của parent.

- `BoxConstraints.tight(Size size)` : Widget **không** được phép thay đổi kích thước của nó và sẽ có kích thước chính xác như `size` được cung cấp.

- `BoxConstraints.tightFor(width: double, height: double)` : Tạo một `BoxConstraints` có giới hạn chặt chẽ trên chiều rộng và chiều cao được cung cấp.

- `BoxConstraints.tightForFinite({double width, double height})` : Tạo một `BoxConstraints` có giới hạn chặt chẽ trên chiều rộng và chiều cao, nhưng **cho phép giới hạn** tối đa về kích thước của parent.

- `BoxConstraints.loose(Size size)` : Điều này có nghĩa là widget có thể có kích thước lớn hơn hoặc nhỏ hơn `size`.

- `BoxConstraints.lerp(BoxConstraints a, BoxConstraints b, double t)` : Tạo một `BoxConstraints` nằm giữa hai `BoxConstraints` được cung cấp `a` và `b`, với tỉ lệ tương ứng được cung cấp bởi `t`.