# Phần 2: Quản lý State nhiều màn hình trong Flutter với Provider

1. **Xây Dựng Tình Huống**
   
   - Màn hình FristPage có một Text widget, hiển thị giá trị `100`
   
   - Di chuyển sang màn hình SecondPage, cũng có Text widget, hiển thị giá trị 100
   
   - Tăng giá trị ở màn hình SecondPage lên 1 => 101
   
   - **Yêu cầu : Khi Back về màn hình FristPage, giá trị của Text cũng được update.**