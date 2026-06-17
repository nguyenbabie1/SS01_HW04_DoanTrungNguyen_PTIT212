# BÀI 4: Phân tích & Lựa chọn (Tối ưu hóa hiệu năng)

## 1. Đáp án lựa chọn

**Prompt 2** là lựa chọn tối ưu và chính xác nhất.

> "Hãy chuyển đổi hàm Java duyệt mảng bằng vòng lặp for dưới đây sang sử dụng Java Stream API để code ngắn gọn và dễ bảo trì hơn. Giải thích lý do tối ưu."


## 2. Lý do chọn Prompt 2

Prompt 2 đáp ứng đầy đủ các tiêu chuẩn thiết kế một prompt tốt: **có mục tiêu rõ ràng (clear goal)**, **có ràng buộc cụ thể (constraints)** và **yêu cầu giải thích (reasoning)**.

| Tiêu chí | Phân tích Prompt 2 |
|---|---|
| **Mục tiêu rõ ràng** | Chỉ đích danh hành động: "chuyển đổi sang Java Stream API". |
| **Ràng buộc cụ thể** | Nêu rõ tiêu chí mong muốn: "code ngắn gọn và dễ bảo trì hơn". |
| **Bối cảnh đầy đủ** | Mô tả đúng input ("hàm duyệt mảng bằng vòng lặp for"). |
| **Yêu cầu lý giải** | Bắt AI "giải thích lý do tối ưu", giúp người dùng học và kiểm chứng. |

Nhờ vậy, AI sẽ trả về kết quả nhất quán, đúng kỳ vọng và có thể đánh giá được.

## 3. Vì sao Prompt 1 chưa tốt

> "Tối ưu hóa code Java này giúp tôi chạy nhanh hơn."

Prompt 1 yếu ở các điểm sau:

- **Mục tiêu mơ hồ:** "chạy nhanh hơn" là một yêu cầu về **hiệu năng (performance)**, nhưng thực tế thuật toán hiện tại đã là tuyến tính O(n) và gần như tối ưu về tốc độ — không có nhiều dư địa tăng tốc. Yêu cầu này lệch với nhu cầu thực sự (làm code **gọn và dễ bảo trì**).
- **Thiếu ràng buộc:** Không chỉ định công nghệ hay phong cách mong muốn (Stream API, lambda…), nên AI phải tự đoán, dễ cho ra kết quả không như ý.
- **Hiểu nhầm bản chất:** Trong trường hợp này, Stream API thậm chí có thể **chậm hơn một chút** so với vòng `for` do chi phí khởi tạo stream. Nếu mục tiêu chỉ là "nhanh hơn", AI có thể từ chối đổi sang Stream — đi ngược lại điều người dùng thực sự cần.
- **Không yêu cầu giải thích:** Người dùng khó kiểm chứng và khó học từ kết quả.



## 4. Kết quả mong đợi từ Prompt 2 (tham khảo)

\`\`\`java
import java.util.List;

public class NumberFinder {

    public static boolean hasLargeNumber(List<Integer> numbers) {
        return numbers.stream()
                      .anyMatch(n -> n > 100);
    }
}
\`\`\`

**Lý do tối ưu:**

- **Ngắn gọn:** Giảm từ ~8 dòng logic xuống còn 1 câu lệnh.
- **Dễ đọc & dễ bảo trì:** `anyMatch(n -> n > 100)` diễn đạt đúng ý định "có phần tử nào > 100 không" một cách khai báo (declarative).
- **An toàn hơn:** Tránh lỗi chỉ số mảng (index out of bounds) khi quản lý biến `i` thủ công.
- **Short-circuit:** `anyMatch` vẫn dừng ngay khi tìm thấy phần tử thỏa điều kiện, giữ hiệu năng tương đương vòng `for`.


## 5. Kết luận

Chọn **Prompt 2** vì nó tuân thủ nguyên tắc thiết kế prompt: **mục tiêu rõ ràng + ràng buộc cụ thể + yêu cầu giải thích**. Prompt 1 thất bại do mục tiêu mơ hồ và đặt sai trọng tâm tối ưu (tốc độ thay vì tính bảo trì).
