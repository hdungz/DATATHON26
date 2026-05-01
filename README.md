# Datathon 2026 – Round 1

## Cấu trúc thư mục

```
Datathon26/
├── datathon-2026-round-1/       ← Dataset cuộc thi
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
├── datathon26-ec9819.ipynb      ← Notebook dự đoán chính (mô hình LTSF)
├── eda-datathon-final.ipynb     ← Notebook EDA toàn diện
├── notebookmcq.ipynb            ← Notebook giải câu hỏi trắc nghiệm (MCQ)
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

---

## Tái lập kết quả

Clone repo về là có sẵn toàn bộ dataset, không cần tải thêm gì.

```bash
git clone https://github.com/hdungz/DATATHON26.git
cd DATATHON26
```

### 1. Notebook dự đoán – `datathon26-ec9819.ipynb`

```bash
jupyter notebook datathon26-ec9819.ipynb
```

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

---

## Ghi chú

- Tất cả notebook đã được cập nhật path trỏ về thư mục local `datathon-2026-round-1/`.
- Để chạy lại trên Kaggle, đổi path về `/kaggle/input/competitions/datathon-2026-round-1/` (notebook dự đoán & MCQ) hoặc `/kaggle/input/datasets/dungz878/datathon2026/` (EDA notebook).
- File `submission.csv` sẽ được tạo tại thư mục gốc sau khi chạy `datathon26-ec9819.ipynb`.
