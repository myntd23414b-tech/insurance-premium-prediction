# DỰ ĐOÁN CHI PHÍ BẢO HIỂM BẰNG DATA MINING

**Dự án cá nhân | Python | Data Mining | Machine Learning**

## 1. Giới thiệu dự án

Dự án ứng dụng kỹ thuật khai phá dữ liệu (Data Mining) và mô hình hồi quy tuyến tính để phân tích các yếu tố ảnh hưởng đến chi phí bảo hiểm của khách hàng.

Thông qua việc xử lý, phân tích và trực quan hóa dữ liệu, dự án hướng đến việc xác định những đặc điểm có liên quan đến mức chi phí bảo hiểm và xây dựng mô hình dự đoán dựa trên thông tin khách hàng.

**Mục tiêu dự án:**
- Kiểm tra chất lượng và làm sạch dữ liệu.
- Phân tích mối quan hệ giữa đặc điểm khách hàng và chi phí bảo hiểm.
- Trực quan hóa dữ liệu để nhận diện các xu hướng.
- Xây dựng mô hình Multiple Linear Regression.
- Đánh giá và cải thiện hiệu quả dự đoán thông qua kỹ thuật Feature Engineering.

## 2. Công nghệ sử dụng

| Công nghệ | Mục đích |
|---|---|
| Python | Ngôn ngữ lập trình chính |
| Pandas, NumPy | Xử lý và phân tích dữ liệu |
| Matplotlib, Seaborn | Trực quan hóa dữ liệu |
| Scikit-learn | Tiền xử lý, xây dựng và đánh giá mô hình |
| Jupyter Notebook | Môi trường lập trình và trình bày kết quả |

## 3. Mô tả dữ liệu

Dự án sử dụng bộ dữ liệu gồm **1.338 quan sát và 7 biến** liên quan đến thông tin khách hàng và chi phí bảo hiểm.

| Biến | Ý nghĩa |
|---|---|
| age | Tuổi của khách hàng |
| sex | Giới tính |
| bmi | Chỉ số khối cơ thể |
| children | Số người phụ thuộc |
| smoker | Tình trạng hút thuốc |
| region | Khu vực sinh sống |
| charges | Chi phí bảo hiểm – biến mục tiêu |

Bài toán được xây dựng dưới dạng học máy có giám sát (Supervised Learning), thuộc nhóm hồi quy (Regression).

## 4. Quy trình thực hiện

### Bước 1: Kiểm tra và làm sạch dữ liệu

- Kiểm tra kích thước và cấu trúc dữ liệu.
- Kiểm tra giá trị thiếu (Missing Values).
- Phát hiện và loại bỏ dữ liệu trùng lặp.
- Phát hiện ngoại lệ bằng phương pháp IQR.
- Phân tích và quyết định giữ lại các giá trị ngoại lệ có ý nghĩa trong bối cảnh bảo hiểm.

**Kết quả kiểm tra:**
- Không có giá trị thiếu.
- Phát hiện một dòng dữ liệu trùng lặp.
- Phát hiện 139 giá trị ngoại lệ của biến charges theo phương pháp IQR.

### Bước 2: Phân tích khám phá dữ liệu (EDA)

Thực hiện thống kê mô tả và xây dựng các biểu đồ:

- Histogram: Phân phối chi phí bảo hiểm.
- Boxplot: Phát hiện và trực quan hóa ngoại lệ.
- Violin Plot: So sánh chi phí theo tình trạng hút thuốc.
- Scatter Plot: Phân tích mối quan hệ giữa BMI, tuổi và chi phí.
- Bar Chart: So sánh chi phí theo khu vực sinh sống.
- Point Plot: Phân tích chi phí theo số người phụ thuộc.

**Một số nhận xét:**

- Chi phí bảo hiểm có phân phối lệch phải.
- Nhóm khách hàng hút thuốc có mức chi phí bảo hiểm cao hơn đáng kể so với nhóm không hút thuốc trong bộ dữ liệu.
- Tuổi và BMI có mối liên hệ với mức chi phí bảo hiểm.
- Tác động của BMI đến chi phí có sự khác biệt giữa nhóm hút thuốc và không hút thuốc.

### Bước 3: Tiền xử lý dữ liệu

Xây dựng quy trình tiền xử lý bằng Scikit-learn:

- Chia dữ liệu thành tập huấn luyện (80%) và tập kiểm tra (20%).
- Sử dụng SimpleImputer để xử lý giá trị thiếu nếu xuất hiện.
- Chuẩn hóa biến số bằng StandardScaler.
- Mã hóa biến phân loại bằng OneHotEncoder.
- Kết hợp các bước thông qua ColumnTransformer và Pipeline.

### Bước 4: Xây dựng mô hình hồi quy

Sử dụng Multiple Linear Regression để dự đoán chi phí bảo hiểm dựa trên sáu biến đầu vào.

Mô hình được huấn luyện trên tập dữ liệu huấn luyện và đánh giá trên tập kiểm tra.

Các chỉ số đánh giá:

- MAE – Mean Absolute Error.
- RMSE – Root Mean Squared Error.
- R² – Coefficient of Determination.

### Bước 5: Cải thiện mô hình bằng Feature Engineering

Bổ sung hai biến tương tác:

- **bmi_smoker:** Tương tác giữa BMI và tình trạng hút thuốc.
- **age_smoker:** Tương tác giữa tuổi và tình trạng hút thuốc.

Mục tiêu là phản ánh sự khác biệt trong mối quan hệ giữa các đặc điểm khách hàng và chi phí bảo hiểm theo tình trạng hút thuốc.

## 5. Kết quả mô hình

| Chỉ số | Mô hình ban đầu | Mô hình cải thiện |
|---|---:|---:|
| MAE | 4.177,05 | 2.831,65 |
| RMSE | 5.956,34 | 4.577,78 |
| R² | 0,8069 | 0,8860 |

**Nhận xét:**

- Sau khi bổ sung các biến tương tác, MAE và RMSE đều giảm.
- R² tăng từ 0,8069 lên 0,8860.
- Mô hình cải thiện giải thích được khoảng 88,6% sự biến thiên của chi phí bảo hiểm trên tập kiểm tra trong thực nghiệm này.
- Kết quả cho thấy Feature Engineering giúp cải thiện khả năng dự đoán trong phạm vi bộ dữ liệu được nghiên cứu.

## 6. Kỹ năng thể hiện qua dự án

- Lập trình và phân tích dữ liệu bằng Python.
- Làm sạch và kiểm tra chất lượng dữ liệu.
- Phân tích dữ liệu khám phá (EDA).
- Trực quan hóa và diễn giải dữ liệu.
- Tiền xử lý biến số và biến phân loại.
- Xây dựng Machine Learning Pipeline.
- Feature Engineering.
- Đánh giá và so sánh hiệu quả mô hình.
- Tổng hợp kết quả phân tích phục vụ ra quyết định.

## 7. Mã nguồn và dữ liệu

Mã nguồn dự án được trình bày trong Jupyter Notebook.

**File chính:** `file code.ipynb`

**Dữ liệu đầu vào:** `data4.csv`

Lưu ý: Nếu dữ liệu không được công khai trong repository, người sử dụng cần chuẩn bị dữ liệu đầu vào tương ứng để chạy lại toàn bộ chương trình.

## 8. Thông tin dự án

- **Hình thức:** Dự án cá nhân.
- **Học phần:** Data Mining.
- **Trường:** Đại học Kinh tế – Luật, ĐHQG TP.HCM.
- **Thời gian:** 03/2026.

---

*Dự án được thực hiện phục vụ mục đích học tập và nghiên cứu. Kết quả mô hình chỉ phản ánh bộ dữ liệu và phương pháp được sử dụng trong đồ án.*
