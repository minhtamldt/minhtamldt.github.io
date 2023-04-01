**BUILD CONTEXT**

1. **BuildContext Là Gì ?**
   
   - Mỗi Widget đều có hàm build. Mỗi hàm build lại có tham số là một BuildContext.
   
   - BuildContext đại diện cho widget đó trên WidgetTree.

2. **Tìm Parent Widget**
   
   ```dart
   //<Widget>.of(context);
   //example : Tìm Scaffold Widget
    Scaffold.of(context);
   //Phương thức of sẽ duyệt ngược lên widget tree, để tìm widget đầu
   //tiên có type là Scaffold.
   ```

3. **Builder Widget**
   
   ```dart
   class MyHomePage extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return Scaffold(
         floatingActionButton: FloatingActionButton(onPressed: () {
             Scaffold.of(context).showBottomSheet(
               (context) => Text('Flutter From Zero to Hero'),
             );
         }),
       );
     }
   }
   ```
   
   - **Context** : đang được truyền vào method `Scaffold.of` là của MyHomePage. Nên khi tìm kiếm sẽ không tìm thấy bất cứ Scaffold nào.
   
   - **Giải quyết** : ta wrap nó vào một widget là Builder. Widget này ta có được một đối tượng context, mà đảm bảo rằng widget này là con của Widget mà chúng ta cần tìm (ví dụ ở đây là Scaffold)

    