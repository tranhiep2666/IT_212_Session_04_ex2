Bạn là một chuyên gia gỡ lỗi Java (Java Debugger) có kinh nghiệm phân tích Stack Trace và xử lý lỗi Runtime Exception trong các ứng dụng Java theo nguyên tắc OOP.

### Ngữ cảnh

Tôi đang chạy chương trình Java và gặp lỗi NullPointerException.

Mã nguồn gây lỗi:

```java
import java.util.List;

public class UserManager {

    private List<String> users; // Danh sách chưa được khởi tạo

    public void addUser(String user) {
        users.add(user); // Dòng gây lỗi
    }
}
```

Stack Trace thực tế:

```text
Exception in thread "main" java.lang.NullPointerException:
Cannot invoke "java.util.List.add(Object)"
because "this.users" is null

    at UserManager.addUser(UserManager.java:7)
    at Main.main(Main.java:6)
```

### Nhiệm vụ

1. Phân tích Stack Trace từng dòng.
2. Xác định nguyên nhân gốc rễ (Root Cause) của lỗi.
3. Giải thích vì sao lỗi xảy ra trong Java.
4. Đề xuất cách sửa an toàn và đúng chuẩn OOP.
5. Viết lại mã nguồn hoàn chỉnh để chương trình hoạt động bình thường.

### Ràng buộc

* Không chỉ nêu cách sửa mà phải giải thích lý do.
* Giữ nguyên tính bao đóng (Encapsulation), không chuyển thuộc tính `users` thành `public`.
* Sử dụng cách khởi tạo danh sách an toàn bằng `ArrayList`.
* Áp dụng thực hành tốt (Best Practice) của Java.
* Trình bày rõ ràng, dễ hiểu cho người mới học Java.

### Định dạng đầu ra

1. Phân tích Stack Trace.
2. Root Cause.
3. Cách khắc phục.
4. Mã nguồn Java hoàn chỉnh nằm trong khối code markdown.


Mã nguồn Java hoàn chỉnh và an toàn do AI sinh ra
import java.util.ArrayList;
import java.util.List;

public class UserManager {

    // Giữ tính bao đóng (Encapsulation)
    private final List<String> users;

    // Khởi tạo danh sách trong constructor
    public UserManager() {
        this.users = new ArrayList<>();
    }

    public void addUser(String user) {
        if (user != null && !user.trim().isEmpty()) {
            users.add(user);
        }
    }

    public List<String> getUsers() {
        return new ArrayList<>(users); // Trả về bản sao để tránh sửa trực tiếp dữ liệu nội bộ
    }
}

Ví dụ sử dụng:

public class Main {
public static void main(String[] args) {
UserManager manager = new UserManager();

        manager.addUser("Alice");
        manager.addUser("Bob");

        System.out.println(manager.getUsers());
    }
}

Kết quả:

[Alice, Bob]

Cách sửa này loại bỏ hoàn toàn NullPointerException bằng cách khởi tạo users ngay trong constructor với new ArrayList<>(), đồng thời vẫn đảm bảo nguyên tắc Encapsulation của OOP.

