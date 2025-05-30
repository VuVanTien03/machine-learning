# Machine Learning Project

## Mô tả tổng quan
Dự án này xử lý dữ liệu Cardiotocography (CTG) để thực hiện phân tích, tiền xử lý, giảm chiều và huấn luyện các mô hình học máy giám sát và không giám sát, tập trung chính vào bài toán phân loại.

---

## Cấu trúc thư mục và mô tả chi tiết

### `data/`
Thư mục chứa toàn bộ dữ liệu sử dụng trong dự án, từ dữ liệu gốc đến dữ liệu đã qua xử lý và dữ liệu giảm chiều.

- `raw_data/`  
  Chứa dữ liệu gốc chưa qua xử lý.  
  - `CTG.xls`: Tập dữ liệu gốc của bài toán Cardiotocography.

- `data_processed/`  
  Chứa dữ liệu sau khi đã tiền xử lý như làm sạch, chuẩn hóa, mã hóa nhãn,...  
  - `data_processed.csv`: Dữ liệu sẵn sàng cho bước phân tích và huấn luyện mô hình.

- `dimension_reduction/`  
  Dữ liệu đã áp dụng kỹ thuật giảm chiều để giảm số lượng đặc trưng.  
  - `lda/`: Dữ liệu sau khi giảm chiều bằng Linear Discriminant Analysis (LDA).  
    Bao gồm toàn bộ dữ liệu (`lda_all.csv`) và các tập train-test với tỷ lệ 60:40, 70:30, 80:20.  
  - `pca/`: Dữ liệu sau khi giảm chiều bằng Principal Component Analysis (PCA).  
    Cấu trúc tương tự thư mục `lda`.

---

### `notebook/`
Chứa các file Jupyter Notebook để xử lý dữ liệu, trực quan hóa và huấn luyện mô hình.

- `data_preprocessing.ipynb`  
  Thực hiện tiền xử lý dữ liệu: xử lý dữ liệu thiếu, chuẩn hóa, mã hóa nhãn,...

- `EDA.ipynb`  
  Phân tích dữ liệu khám phá (Exploratory Data Analysis): biểu đồ phân phối, quan sát đặc trưng,...

- `clustering/kmeans.ipynb`  
  Áp dụng thuật toán phân cụm KMeans để nhóm dữ liệu không giám sát.

- `dimension_reduction/`  
  - `lda.ipynb`: Thực hiện giảm chiều bằng LDA và trực quan hóa kết quả.  
  - `pca.ipynb`: Thực hiện giảm chiều bằng PCA và trực quan hóa kết quả.

- `model/`  
  Chứa các notebook huấn luyện mô hình học máy.

  - `classification/` (Mô hình phân loại)  
    - `knn.ipynb`: Mô hình K-Nearest Neighbors.  
    - `svm.ipynb`: Mô hình Support Vector Machine với nhiều kernel (linear, RBF, polynomial, sigmoid).  
    - `softmax.ipynb`: Mô hình Softmax Regression (đa lớp).  
    - `softmax_evaluate_acc.ipynb`: Đánh giá độ chính xác và trực quan hóa ma trận nhầm lẫn cho mô hình softmax.

  - `Regression/`  
    - `regression_model.ipynb`: Mô hình hồi quy để dự đoán đầu ra liên tục.

---

### `requirements.txt`
Danh sách các thư viện Python cần cài đặt để chạy các notebook và mã nguồn trong dự án.

---

## Hướng dẫn sử dụng

1. **Cài đặt môi trường**  
   Tạo môi trường ảo (virtual environment) và cài đặt các thư viện:
   ```bash
   python -m venv env
   source env/bin/activate     # Linux/MacOS
   .\env\Scripts\activate      # Windows
   pip install -r requirements.txt
2. **Chạy Notebook** \
    Khởi động Jupyter Notebook:
    ```bash
    jupyter notebook

Mở các file .ipynb trong thư mục notebook/ để chạy từng bước xử lý dữ liệu, phân tích, giảm chiều và huấn luyện mô hình.
3. **Quy trình làm việc gợi ý**

   - Tiền xử lý dữ liệu: notebook/data_preprocessing.ipynb 
   - Phân tích khám phá: notebook/EDA.ipynb 
   - Phân cụm : notebook/clustering/kmeans.ipynb 
   - Giảm chiều: notebook/dimension_reduction/lda.ipynb và pca.ipynb 
   - Huấn luyện mô hình phân loại: notebook/model/classification/
   - Hồi quy : notebook/model/Regression/regression_model.ipynb

# Ghi chú
Dữ liệu giảm chiều được chia sẵn theo tỷ lệ train-test giúp thuận tiện cho việc huấn luyện và đánh giá mô hình.

Các mô hình phân loại được thử nghiệm với nhiều kernel khác nhau nhằm tối ưu hiệu quả.

