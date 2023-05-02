# SCHEDULER BINDING

- Là một lớp singleton được sử dụng để đăng ký các callbacks cho bộ lập lịch (scheduler) của Flutter

- Quản lý các task đăng ký để chạy trong bộ lập lịch.

- Các phương thức quan trọng của `SchedulerBinding` bao gồm:
  
  - `addPersistentFrameCallback()` : 
    
    - Đăng ký một callback để chạy sau mỗi frame được vẽ trên màn hình.
    
    - Giữ cho callback này hoạt động liên tục trong toàn bộ quá trình chạy của ứng dụng.
  
  - `addPostFrameCallback()` : 
    
    - Đăng ký một callback để chạy sau khi frame hiện tại đã được vẽ và kết thúc bộ lập lịch hiện tại.
    
    - Callback này chỉ được chạy một lần.
  
  - `ensureVisualUpdate()` : 
    
    - Đảm bảo rằng một khung hình mới nhất đã được vẽ trên màn hình trước khi tiếp tục thực hiện các task khác.
  
  - `scheduleFrame()` : 
    
    - Đăng ký một frame mới và sắp xếp các task được đăng ký để chạy trong frame mới này.

**LƯU Ý** : `SchedulerBinding` chỉ hoạt động trong framework binding của Flutter. Phải chắc chắn rằng bạn đã bắt đầu framework binding trước khi sử dụng `SchedulerBinding`