# Probability-and-Statistics
This is code Probability and Statistics for Assignment "Computer parts"

# Intel CPU Analysis (with GPU Reference)

## 📁 Dataset

- **Intel CPU Dataset:** `Intel_CPUs.csv`
- **GPU Dataset (optional):** `All_GPUs.csv` *(used only for initial table preview)*

Place the CSV files in a folder such as `D:/data/` or adjust the path in the code accordingly.

---

## 📦 Required Libraries

Before running the code, install and load the following R packages:

```r
install.packages(c("GGally", "ggplot2", "corrplot", "dplyr", "mice", "ROSE",
                   "caret", "kableExtra", "glmnet", "knitr", "DT", "flextable",
                   "webshot2", "questionr", "reshape2", "gridExtra", "car"))

---
**## Vietnamese WorkFlow**
Phân tích TDP của CPU Intel
Giới thiệu
Dự án này tập trung vào việc phân tích và dự đoán Công suất Thiết kế Nhiệt (TDP - Thermal Design Power) của các bộ vi xử lý Intel bằng cách sử dụng các đặc trưng phần cứng. Chúng tôi sử dụng các kỹ thuật thống kê như hồi quy tuyến tính đa biến và phân tích tương quan để xây dựng và đánh giá mô hình dự đoán.

Dữ liệu
Dự án sử dụng hai tập dữ liệu chính:

All_GPUs.csv: Dữ liệu về GPU (có thể dùng cho phân tích mở rộng hoặc so sánh).

Intel_CPUs.csv: Dữ liệu chính về CPU Intel, chứa các thông số kỹ thuật và TDP.

Lưu ý: Các tệp dữ liệu này được giả định nằm trong thư mục D:/data/ trên hệ thống cục bộ. Bạn cần điều chỉnh đường dẫn trong code nếu vị trí tệp khác.

Yêu cầu (Prerequisites)
Dự án này yêu cầu môi trường R và các gói (packages) sau:

GGally

ggplot2

corrplot

dplyr

mice

ROSE

caret

kableExtra

glmnet

knitr

DT

flextable

webshot2

questionr

reshape2

gridExtra

car

Bạn có thể cài đặt tất cả các gói này bằng cách chạy:

install.packages(c("GGally", "ggplot2", "corrplot", "dplyr", "mice", "ROSE", "caret",
                   "kableExtra", "glmnet", "knitr", "DT", "flextable", "webshot2",
                   "questionr", "reshape2", "gridExtra", "car"))

Cài đặt và Chạy
Tải xuống mã nguồn:
Clone repository này về máy tính của bạn:

git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
cd your-repo-name

(Thay your-username và your-repo-name bằng thông tin của bạn)

Đặt dữ liệu:
Đảm bảo các tệp All_GPUs.csv và Intel_CPUs.csv được đặt trong thư mục D:/data/ hoặc cập nhật đường dẫn trong code R cho phù hợp với vị trí của bạn.

Chạy script R:
Mở tệp R chính (ví dụ: main_analysis.R nếu bạn đặt tên như vậy, hoặc chạy trực tiếp các khối code trong môi trường R/RStudio).

Các bước phân tích chính
Mã nguồn thực hiện các bước sau:

Tải và khám phá dữ liệu: Tải dữ liệu CPU và GPU, kiểm tra kích thước và hiển thị các dòng đầu tiên.

Tiền xử lý dữ liệu:

Xử lý các giá trị trống và chuyển đổi chúng thành NA.

Lọc bỏ các cột có tỷ lệ thiếu dữ liệu cao (trên 10%).

Loại bỏ các hàng chứa NA còn lại.

Làm sạch và chuyển đổi dữ liệu:

Chuyển đổi các cột như TDP, Processor_Base_Frequency, Cache, Recommended_Customer_Price, nb_of_Cores sang định dạng số bằng cách loại bỏ các đơn vị và ký tự không cần thiết.

Chuyển đổi các biến nhị phân và phân loại (Intel_Virtualization_Technology_VTx_, Embedded_Options_Available, Vertical_Segment, Status, Product_Collection, Instruction_Set) thành kiểu factor.

Phân tích tương quan:

Tính toán và hiển thị ma trận tương quan Pearson giữa các biến số quan trọng (TDP, nb_of_Cores, Processor_Base_Frequency, Cache, Lithography).

Vẽ biểu đồ tương quan để trực quan hóa mối quan hệ.

Thống kê mô tả:

Tính toán các chỉ số thống kê mô tả (Mean, SD, Min, Max, Quartiles) cho các biến số.

Thống kê tần suất và phần trăm cho các biến phân loại đã chọn.

Biến đổi Logarit:

Áp dụng biến đổi logarit cho TDP, nb_of_Cores, Cache, Processor_Base_Frequency để chuẩn hóa phân phối và cải thiện tính tuyến tính.

Vẽ biểu đồ histogram của TDP sau khi biến đổi.

Trực quan hóa mối quan hệ:

Vẽ biểu đồ boxplot của log(TDP) theo Vertical_Segment.

Vẽ biểu đồ scatter plot giữa log(TDP) với log(nb_of_Cores), log(Processor_Base_Frequency), và log(Cache).

Xây dựng và đánh giá mô hình hồi quy:

Chia dữ liệu thành tập huấn luyện (80%) và tập kiểm tra (20%).

Huấn luyện mô hình hồi quy tuyến tính (lm) để dự đoán TDP dựa trên nb_of_Cores, Processor_Base_Frequency, Cache, và Lithography.

Hiển thị tóm tắt mô hình và các biểu đồ chẩn đoán.

Xử lý các cấp độ Lithography mới trong tập kiểm tra để đảm bảo dự đoán chính xác.

Thực hiện dự đoán trên tập kiểm tra và hiển thị kết quả.

Vẽ biểu đồ so sánh giá trị TDP thực tế và dự đoán để đánh giá trực quan hiệu suất mô hình.

Vẽ biểu đồ phân phối:

Tạo các biểu đồ histogram và boxplot kết hợp cho các biến quan trọng để hiểu rõ hơn về phân phối của chúng.

Kết quả và Thảo luận
Mô hình hồi quy tuyến tính cung cấp một cách minh bạch để định lượng mối quan hệ tuyến tính giữa TDP và các đặc trưng phần cứng. Tuy nhiên, biểu đồ so sánh giá trị thực tế và dự đoán cho thấy mô hình hiện tại có thể chưa nắm bắt được toàn bộ động lực của tiêu thụ điện năng bộ xử lý, đặc biệt với các mối quan hệ phi tuyến tính hoặc phức tạp hơn.

Để cải thiện mô hình, có thể cần xem xét:

Tích hợp các mô hình phức tạp hơn (ví dụ: mô hình phi tuyến tính, mô hình dựa trên cây).

Mở rộng tập hợp các đặc trưng (ví dụ: điện áp, kích thước die,
