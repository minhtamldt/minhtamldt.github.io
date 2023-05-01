# CÀI ĐẶT MÔI TRƯỜNG FLUTTER TRÊN MACOS

### Bước 1: Tải SDK

- [Lên trang chủ tải Flutter SDK](https://docs.flutter.dev/get-started/install/macos)

- [Tải AndroidStudio](https://developer.android.com/studio)

- [Tải XCode](https://apps.apple.com/us/app/xcode/id497799835)

### Bước 2: Chọn nơi lưu SDK

- Giải nén file vừa tải về. Bạn sẽ được một folder `flutter`

- [Optional] : Copy folder `flutter` vào folder `Development` . (Tuỳ chọn một nơi mà bạn muốn lưu folder sdk của flutter).

- Ví dụ : `MacintoshHD`/`User`/`tamtm`/`Development`/`flutter`

### Bước 3: Cài đặt biến môi trường.

- Bước 1:  Chuẩn bị đường dẫn để cấu hình biến môi trường : 
  
  `export PATH="$PATH:[PATH_OF_FLUTTER_GIT_DIRECTORY]/bin"`
  
  Ví dụ : 
  
  `export PATH="$PATH:/Users/tamtm/Development/flutter/bin"`

- Bước 2: Mở terminal, thực hiện lệnh :  `nano ~/.zshrc source`

- Bước 3: Copy và Paste đường dẫn đã chuẩn bị ở #1

- Bước 4. Nhấn `Ctrl + X` để xác nhận lưu.

- Bước 5: Nhấn `Y` để đồng ý.

- Bước 6: Chạy file vừa save để hệ thống nhận biết có biết môi trường mới. Thực hiện lệnh `source ~/.zshrc`

- Bước 7: Thực hiện lệnh `flutter` để kiểm tra đã setup thành công chưa.

### Bước 4: Kiểm tra xem môi trường flutter còn thiếu những gì ?

- Thực hiện lệnh : `flutter doctor`

### Bước 5: Xử lý một số thành phần còn thiếu.

- Đây là quá trình cài đặt mình gặp phải, tuỳ thuộc vào thời điểm nó có thể khác.

- Thiếu `CocoaPods`
  
  - Để giải quyết lỗi này cần cài đặt CocoaPods thông qua homebrew. Mình đã cài đặt trực tiếp nhưng dễ bị lỗi. Nhưng thành công khi cài thông qua homebrew. 
  
  - Cài đặt homebrew : (Trình quản lý trên MacOS)
    
    - Vào trang chủ , copy `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
    
    - Mở terminal, chạy đoạn lệnh vừa copy
    
    - Trong quá trình cài đặt, trong Terminal, homebrew sẽ có hướng dẫn làm bước tiếp theo, chúng ta cần lưu ý.
    
    - ![](/Users/tamtm/Library/Application%20Support/marktext/images/2023-05-01-08-43-01-image.png)
  
  - Sau khi cài thành công homebrew, thực hiện cài đặt `CocoaPods`
    
    - Thực hiện lệnh : `brew install cocoapods`

- cmdline-tools component is missing
  
  ![Enter image description here](https://i.stack.imgur.com/mO5qr.png)

        
