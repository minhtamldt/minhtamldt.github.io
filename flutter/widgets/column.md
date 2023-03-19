### COLUMN

1. **Khái niệm**
   
   - Widget dùng để sắp xếp các widget con theo chiều dọc
   
   - Widget con của Column sẽ được xếp chồng lên nhau theo thứ tự được liệt kê, từ trên xuống dưới.
   
   ✍️ Ví dụ : 
   
   ```
   Column(
     children: <Widget>[
       Text('Widget con 1'),
       Text('Widget con 2'),
       Text('Widget con 3'),
     ],
   )
   ```

2. **Thuộc tính**
   
   | STT | Tên Thuộc Tính     | Mô Tả                                                                                                                                                                                                                                                                                                                                                  |
   |:---:|:------------------ |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
   | 1   | mainAxisAlignment  | Chỉ định cách sắp xếp các widget con theo chiều dọc<br/>- **start (default)** : **các widget nằm trên** cùng của cột.<br/>- **center** : các widget nằm trên cùng của cột.<br/>- **end** : các widget nằm trên cùng của cột.<br/>- **spaceBetween** : các widget nằm trên cùng của cột.<br/>- **spaceAround** : các widget nằm trên cùng của cột.<br/> |
   | 2   | crossAxisAlignment |                                                                                                                                                                                                                                                                                                                                                        |
   | 3   | mainAxisSize       | chỉ định kích thước của Column trong chiều dọc, <br/>Các giá trị có thể sử dụng là **MainAxisSize.max** (mặc định) và **MainAxisSize.min.**                                                                                                                                                                                                            |
