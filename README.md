# Datathon 2026 – Round 1 · Sales Forecasting & EDA


## Cấu trúc thư mục

```
Datathon26/
├── datathon-2026-round-1/          ← Dataset gốc của cuộc thi (xem hướng dẫn bên dưới)
│   ├── sales.csv
│   ├── sample_submission.csv
│   ├── customers.csv
│   ├── orders.csv
│   ├── order_items.csv
│   ├── payments.csv
│   ├── products.csv
│   ├── promotions.csv
│   ├── returns.csv
│   ├── reviews.csv
│   ├── inventory.csv
│   ├── geography.csv
│   ├── shipments.csv
│   └── web_traffic.csv
│
├── datathon26-ec9819.ipynb         
├── eda-datathon-final.ipynb       
├── notebookmcq.ipynb             
└── README.md
```

---

## Cài đặt môi trường

### Yêu cầu
- Python **3.10+**
- Jupyter Notebook / JupyterLab

### Cài thư viện

```bash
pip install pandas numpy scikit-learn matplotlib seaborn plotly \
            statsmodels prophet lightgbm xgboost jupyter
```

> **Lưu ý Kaggle:** Nếu chạy trên Kaggle, tất cả thư viện trên đã có sẵn. Chỉ cần thêm dataset theo hướng dẫn bên dưới.

---

## Chuẩn bị dữ liệu

Dataset **không được commit vào Git** do kích thước lớn (~130 MB+). Bạn cần tải về và đặt vào đúng thư mục:

### Cách 1 – Clone repo rồi đặt data thủ công

1. Clone repo:
   ```bash
   git clone <repo-url>
   cd Datathon26
   ```

2. Tải dataset từ trang cuộc thi .

3. Giải nén và copy tất cả file `.csv` vào:
   ```
   Datathon26/datathon-2026-round-1/
   ```

### Cách 2 – Dùng Kaggle CLI

Nếu dataset được host trên Kaggle:
```bash
kaggle competitions download -c datathon-2026-round-1 -p datathon-2026-round-1/
unzip datathon-2026-round-1/datathon-2026-round-1.zip -d datathon-2026-round-1/
```

### Xác minh dữ liệu

Sau khi đặt file, kiểm tra:
```bash
ls datathon-2026-round-1/
# Phải có: sales.csv, sample_submission.csv, customers.csv, orders.csv, ...
```

---

## Tái lập kết quả

### 1. Notebook Mô hình Dự đoán – `datathon26-ec9819.ipynb`

**Chạy trên máy local:**
```bash
jupyter notebook datathon26-ec9819.ipynb
```
**Chạy trên Kaggle:**  
Upload notebook lên Kaggle > Add dataset `datathon-2026-round-1` vào Competition Data.

**Mô tả:**  
- Load `sales.csv` và `sample_submission.csv`
- Feature engineering theo chu kỳ (Fourier terms cho tháng, quý, năm)
- Mô hình backbone tổng hợp: Prophet + hồi quy tuyến tính
- Sinh file `submission.csv` (548 dòng, dự đoán Revenue & COGS từ 2023-01-01)

**Output:** `submission.csv`

---

### 2. Notebook EDA – `eda-datathon-final.ipynb`

```bash
jupyter notebook eda-datathon-final.ipynb
```

**Mô tả:**  
- Load toàn bộ 14 bảng dữ liệu
- Phân tích xu hướng doanh thu dài hạn (MA 12M)
- Phân tích theo danh mục, vùng địa lý, kênh thanh toán
- Đánh giá độ nhạy với khuyến mãi theo category
- Biểu đồ Plotly tương tác


---

### 3. Notebook MCQ – `notebookmcq.ipynb`

```bash
jupyter notebook notebookmcq.ipynb
```

**Mô tả:**  
- Load tất cả CSV từ `datathon-2026-round-1/`
- Giải 10 câu hỏi trắc nghiệm phân tích dữ liệu Vòng 1
- Mỗi cell = 1 câu hỏi, có kèm giải thích kết quả

##  Ghi chú

- Tất cả notebook đã được cập nhật path trỏ về thư mục **local** `datathon-2026-round-1/` (thay vì `/kaggle/input/...`) để chạy được trên máy cá nhân.
- Để chạy lại trên Kaggle, đổi path về `/kaggle/input/competitions/datathon-2026-round-1/` (datathon26 & MCQ) hoặc `/kaggle/input/datasets/dungz878/datathon2026/` (EDA notebook).
- File `submission.csv` sẽ được tạo ra tại thư mục gốc sau khi chạy `datathon26-ec9819.ipynb`.
