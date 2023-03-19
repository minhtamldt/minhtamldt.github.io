### COLUMN

1. **KHÁI NIỆM**
   
   - Widget dùng để sắp xếp các widget con theo chiều dọc
   
   - Widget con của Column sẽ được xếp chồng lên nhau theo thứ tự được liệt kê, từ trên xuống dưới.
   
   ✍️ Ví dụ : 
   
   ```dart
   Column(
     children: <Widget>[
       Text('Widget con 1'),
       Text('Widget con 2'),
       Text('Widget con 3'),
     ],
   )
   ```

2. **THUỘC TÍNH**
   
   | STT | Thuộc Tính         | Mô Tả                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   |:---:|:------------------ |:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | 1   | mainAxisAlignment  | Chỉ định cách sắp xếp các widget con theo chiều **dọc**<br/>- **start (default)** : các widget nằm trên cùng của cột.<br/>- **center** : nằm giữa cột <br/>- **end** : nằm dưới cùng của cột <br/>- **spaceBetween** : các widget có khoảng cách với nhau (các khoảng cách đều nhau)<br/>- **spaceAround** : bên trên và bên dưới widget đều có khoảng cách, nếu các widget đối diện nhau thì khoảng cách này **không tăng lên**<br/>- **spaceEvenly** : bên trên và bên dưới widget đều có khoảng cách, nếu các widget đối diện nhau thì khoảng cách này **tăng lên** |
   | 2   | crossAxisAlignment | Chỉ định cách sắp xếp các widget con theo chiều **ngang**<br/>- **start (default)** : các widget nằm bên trái.<br/>- **center** : nằm giữa cột <br/>- **end** : nằm bên phải cột <br/>- **stretch** : widget con sẽ được kéo dãn theo chiều ngang của cột để lấp đầy không gian<br/>- **baseline** : widget con sẽ được kéo dãn theo chiều ngang của cột để lấp đầy không gian**<br/>                                                                                                                                                                                  |
   | 3   | mainAxisSize       | chỉ định kích thước của Column trong chiều dọc, <br/>Các giá trị có thể sử dụng là **MainAxisSize.max** (mặc định) và **MainAxisSize.min.**                                                                                                                                                                                                                                                                                                                                                                                                                            |

![Test Image ](https://images.pexels.com/photos/572897/pexels-photo-572897.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1)
