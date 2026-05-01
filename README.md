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
├── datathon26-ec9819.ipynb <-> Mô hình   
├── eda-datathon-final.ipynb <-> EDA  
├── notebookmcq.ipynb <-> MCQ  
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

## Chạy trên Kaggle

### Bước 1 – Upload notebook

Vào [kaggle.com/code](https://www.kaggle.com/code) → **New Notebook** → Import file `.ipynb` cần chạy.

### Bước 2 – Thêm dataset

Trong Kaggle Notebook, click **+ Add data** ở góc phải và thêm dataset tương ứng:

| Notebook | Dataset cần thêm | Loại |
|---|---|---|
| `datathon26-ec9819.ipynb` | `datathon-2026-round-1` | Competition Data |
| `notebookmcq.ipynb` | `datathon-2026-round-1` | Competition Data |
| `eda-datathon-final.ipynb` | `dungz878/datathon2026` | Dataset |

### Bước 3 – Đổi path trong notebook

Sau khi thêm dataset, sửa biến path ở cell đầu tiên:

**`datathon26-ec9819.ipynb` và `notebookmcq.ipynb`:**
```python
# Đổi từ:
DATA_DIR = 'datathon-2026-round-1/'
# Thành:
DATA_DIR = '/kaggle/input/competitions/datathon-2026-round-1/'
```

**`eda-datathon-final.ipynb`:**
```python
# Đổi từ:
base_path = "datathon-2026-round-1/"
# Thành:
base_path = "/kaggle/input/datasets/dungz878/datathon2026/"
```

### Bước 4 – Chạy

**Run All** → Kết quả `submission.csv` sẽ xuất hiện trong tab **Output** của Kaggle.

---

## Ghi chú

- Tất cả notebook đã được cập nhật path trỏ về thư mục local `datathon-2026-round-1/`.
- File `submission.csv` sẽ được tạo tại thư mục gốc sau khi chạy `datathon26-ec9819.ipynb`.
