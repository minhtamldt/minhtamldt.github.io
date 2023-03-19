### COLUMN

1. **Khái niệm**
   
   - Widget dùng để sắp xếp các widget con theo chiều dọc
   
   - Widget con của Column sẽ được xếp chồng lên nhau theo thứ tự được liệt kê, từ trên xuống dưới.
   
   ✍️ Ví dụ : 
   
   `Column(
     children: <Widget>[
       Text('Widget con 1'),
       Text('Widget con 2'),
       Text('Widget con 3'),
     ],
   )`

2. **Thuộc tính**
- **mainAxisAlignment** : Chỉ định cách sắp xếp các widget con theo chiều dọc
  
  + start (default) : các widget nằm trên cùng của cột.
  
  + center : các widget nằm giữa các cột
  
  + end: các widget nằm dưới cột
  
  + spaceBetween: 
  
  + spaceAround:
  
  + spaceEvenly: 

- **crossAxisAlignment** : Chỉ định cách sắp xếp các widget con theo chiều ngang
  
  - start (default) : 
  
  - center : 
  
  - end: 
  
  - spaceBetween:
  
  - spaceAround:
  
  - spaceEvenly:

- **mainAxisSize** : chỉ định kích thước của Column trong chiều dọc, Các giá trị có thể sử dụng là MainAxisSize.max (mặc định) và MainAxisSize.min.
