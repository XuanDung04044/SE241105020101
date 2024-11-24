1. Single Responsibility Principle (SRP)
* Ý nghĩa:
* Nguyên tắc này nhấn mạnh rằng mỗi lớp hoặc module chỉ nên thực hiện một nhiệm vụ duy nhất. Điều này đảm bảo mỗi lớp có một lý do duy nhất để thay đổi.

* Ứng dụng trong Bank Statement Analyzer:

* BankTransaction: Lưu trữ thông tin chi tiết của một giao dịch (ngày, số tiền, mô tả).
* TransactionParser: Đảm nhận việc phân tích dữ liệu từ file CSV để tạo danh sách các BankTransaction.
* TransactionAnalyzer: Phân tích danh sách giao dịch, thực hiện các phép tính như tổng số tiền giao dịch, đếm giao dịch theo tháng.
* Lợi ích:
* Việc chia nhỏ trách nhiệm giúp dễ bảo trì, mở rộng và kiểm thử từng thành phần độc lập. Mỗi lớp chỉ cần tập trung thực hiện tốt nhiệm vụ của mình.

2. Cohesion (Độ gắn kết)
* Ý nghĩa:
* Cohesion đo lường mức độ các phần bên trong một lớp/module hỗ trợ nhau để thực hiện một nhiệm vụ chung.

* Cohesion cao: Các thành phần trong lớp tập trung vào một nhiệm vụ cụ thể.
* Cohesion thấp: Lớp chứa nhiều chức năng không liên quan, dẫn đến khó quản lý.
* Ứng dụng trong Bank Statement Analyzer:

* BankTransaction: Tất cả thuộc tính (date, amount, description) và phương thức đều phục vụ quản lý thông tin của một giao dịch duy nhất.
* TransactionParser: Chỉ tập trung vào việc đọc và phân tích file, không xử lý logic khác.
* TransactionAnalyzer: Chỉ thực hiện các phép toán phân tích trên danh sách giao dịch, đảm bảo tập trung vào nhiệm vụ của mình.
* Lợi ích:
* Mã nguồn trở nên rõ ràng hơn, dễ bảo trì và giảm thiểu lỗi do các nhiệm vụ không liên quan gây ra.

3. Coupling (Độ kết nối)
* Ý nghĩa:
* Coupling mô tả mức độ phụ thuộc giữa các module/lớp trong hệ thống.

* Coupling thấp: Các thành phần độc lập, dễ thay đổi và mở rộng.
* Coupling cao: Các thành phần phụ thuộc chặt chẽ vào nhau, gây khó khăn khi chỉnh sửa hoặc thay thế.
* Ứng dụng trong Bank Statement Analyzer:

* Giảm phụ thuộc giữa các lớp:
* TransactionParser chỉ tạo ra danh sách BankTransaction mà không biết TransactionAnalyzer xử lý danh sách đó như thế nào.
* TransactionAnalyzer chỉ làm việc với danh sách giao dịch, không cần biết chúng được tạo ra bởi TransactionParser.
* Sử dụng đối tượng thay vì chi tiết cụ thể:
* Các lớp giao tiếp thông qua danh sách BankTransaction, không trực tiếp sử dụng các thuộc tính cụ thể của lớp khác.
* Lợi ích:
* Sự thay đổi trong một thành phần sẽ không ảnh hưởng đến các thành phần khác. Điều này giúp hệ thống linh hoạt và dễ mở rộng.

* Lợi ích chung của thiết kế này:
* Dễ bảo trì:
* Các thay đổi ở một lớp không gây ảnh hưởng đến toàn bộ hệ thống.
* Dễ mở rộng:
* Có thể thêm các tính năng mới như hỗ trợ file JSON hoặc Excel mà không làm thay đổi các chức năng hiện tại.
* Dễ kiểm thử:
* Kiểm thử từng lớp đơn lẻ dễ dàng hơn vì các trách nhiệm được phân tách rõ ràng.
* Biểu đồ UML minh họa
* Class:
*  ![Diagram](https://www.planttext.com/api/plantuml/png/Z971QW8n48RlUOevkj1zWL34glJKGa7nFcPZ3SrE93DxiCKdy-0Z-GfDwefhNS4SViXavil_9yVzOSI2KPhQA-EH6SP8N_E8n6Z41O8V1McLKA5O3TEaRG7hq91eg4ApzETYPTb4jycJ6cOI7NsgdMhH7Um7HhQnXGDiydOoMmnMpgTRNfCM6juSo_C_FyDUt0kXttvtW0QzQNmoEm-2VY2NLhx3BQwI949ErsdWyVOzaAmVOJr1dLirE9BYJxFhs_XbERnvRmqcscISLL--_Way7RCQMQhoL_u2003__mC0)
* Use Case:
*  ![Diagram](https://www.planttext.com/api/plantuml/png/L8vD2i9038NtEKNelWkdUoaehaMP0uHfa4BwmoIpACMJkV18Ni6fpC8-2E-3zmZlytgtQXGj3G8KR8hebID0v60qFeJnlgZnW2jWLb8Ef8oLdsMY3Y-zS8Maw4-7VU5ACTjVxlRvkTTPQC4RQnBJKchW2R0jmBe-_fxcA-moky8Dj3nss-Wl0000__y30000)
* Activity:
* ![Diagram](https://www.planttext.com/api/plantuml/png/P50x3i8m3Drp2e_b2kr0-Sm82HWOJN1f84qgEn62gp5m9Av0KYg1XATd-_dvsQ_7ivQ0769drG1KkHDYYBtrU1HeZALAbMjaeI61ACQTOCle17KmtWqzhfHfeCWujoLgJI9DjDC9X9OS57kIYO8KvO890y4StUL71lpXJ3f8zI7D7DhRdI1y6VA_UsJnEBGqqbky0UQo604cYJPhaat-YvKVBMnQVmLYzWnTyecdT2IvesdI4tolweJpHzu0003__mC0)
* Giải thích cách tác giả sử dụng để giải quyết các vấn đề về: SRP, cohesion, coupling:
1 Single Responsibility Principle (SRP)
* SRP là nguyên tắc cho rằng mỗi lớp nên chỉ có một lý do để thay đổi, hay nói cách khác, mỗi lớp nên chỉ đảm nhận một trách nhiệm riêng.
* Trong mã của chúng ta, SRP đã được áp dụng thông qua việc chia chương trình thành ba lớp khác nhau:
* BankTransaction: Chịu trách nhiệm lưu trữ thông tin về một giao dịch (ngày, số tiền, mô tả).
* TransactionParser: Chịu trách nhiệm đọc và phân tích dữ liệu từ file CSV để tạo ra danh sách các BankTransaction. Lớp này chỉ tập trung vào việc xử lý các file đầu vào và không chứa logic ứng dụng khác.
* TransactionAnalyzer: Chịu trách nhiệm thực hiện các phép toán phân tích trên danh sách giao dịch, như tính tổng số tiền giao dịch và đếm số lượng giao dịch trong một tháng nhất định.
* Bằng cách tách biệt các chức năng này thành các lớp riêng biệt, tác giả đã đảm bảo rằng mỗi lớp chỉ có một trách nhiệm duy nhất, giúp tăng cường khả năng bảo trì và mở rộng trong tương lai.
2 Cohesion
* Cohesion đề cập đến mức độ mà các phần phức tạp của một lớp hoặc module tương tác với nhau để thực hiện một công việc duy nhất. Trong thiết kế của chúng ta, mỗi lớp đều có high cohesion:
* BankTransaction: Tất cả các phương thức và thuộc tính trong lớp này đều liên quan đến một giao dịch ngân hàng, như ngày, số tiền, và mô tả. Điều này làm cho lớp có mức độ tập trung cao và dễ hiểu.
* TransactionParser: Lớp này tập trung hoàn toàn vào việc phân tích dữ liệu từ file, không chứa bất kỳ logic nào liên quan đến việc phân tích giao dịch. Tất cả các phương thức đều liên quan đến hoạt động đọc và phân tích file.
* TransactionAnalyzer: Tương tự, lớp này chỉ xử lý các phép toán phân tích dữ liệu giao dịch. Mọi phương thức ở đây đều hướng tới việc tính toán và phân tích kết quả.
* Tất cả các lớp đều có mục tiêu rõ ràng và giữ cho các chức năng của nó liên kết chặt chẽ, do đó đạt được sự gắn kết cao.

3 Coupling
* Coupling mô tả mức độ phụ thuộc giữa các lớp trong một hệ thống. Trong thiết kế này, tốc độ thấp về coupling đã được đảm bảo:
* Các lớp trong chương trình tương tác với nhau thông qua các đối tượng chứ không phải thông qua các thuộc tính trực tiếp.
* Ví dụ:
* TransactionParser tạo ra danh sách các BankTransaction, nhưng không biết gì về cách mà TransactionAnalyzer sử dụng chúng.
* TransactionAnalyzer nhận vào danh sách các giao dịch mà không cần biết lớp TransactionParser đã tạo ra danh sách này như thế nào.
* Điều này có nghĩa là nếu cần thay đổi logic trong lớp TransactionParser hoặc TransactionAnalyzer, điều đó sẽ không ảnh hưởng đến các lớp khác. Sự giảm thiểu coupling này giúp cho hệ thống dễ dàng bảo trì và mở rộng.
