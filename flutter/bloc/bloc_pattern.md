### Bloc Pattern

1. **Bloc Pattern Là Gì ?**
   
   - Mục đích tách code Logic ra khỏi code UI.
   
   - Giúp quản lý `State` của màn hình tốt hơn.
   
   ✍️ Ví dụ : Chức năng load image khi nhấn vào một button.
   
   - Khi User tap vào button.
   
   - Button sẽ gửi URL của image đến cho Bloc.
   
   - Bloc xử lý download image và gửi lại cho Image Widget hiển thị.