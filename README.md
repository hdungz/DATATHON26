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

## Cài đặt môi trường (Nếu chạy dưới Local)

### Yêu cầu
- Python **3.10+**
- Jupyter Notebook / JupyterLab

### Cài thư viện

```bash
pip install pandas numpy scikit-learn matplotlib seaborn plotly \
            lightgbm xgboost shap jupyter
```

---

## Hướng dẫn chạy trên Kaggle (Mặc định)

Tất cả các file notebook đã được thiết lập mặc định với đường dẫn của môi trường Kaggle. 

### Bước 1 – Upload notebook

Vào [kaggle.com/code](https://www.kaggle.com/code) → **New Notebook** → Import file `.ipynb` tương ứng mà bạn muốn chạy.

### Bước 2 – Thêm dataset

Trong Kaggle Notebook, click **+ Add data** ở góc phải và thêm dataset sau (tuỳ vào notebook):

| Notebook | Dataset cần thêm | Loại |
|---|---|---|
| `datathon26-ec9819.ipynb` | `datathon-2026-round-1` | Competition Data |
| `notebookmcq.ipynb` | `datathon-2026-round-1` | Competition Data |
| `eda-datathon-final.ipynb` | `dungz878/datathon2026` | Dataset |

### Bước 3 – Chạy

Nhấn **Run All** → Sau khi notebook `datathon26-ec9819.ipynb` chạy xong, kết quả `submission.csv` sẽ xuất hiện trong tab **Output** của Kaggle.

---

## Hướng dẫn chạy dưới Local

Clone repo về máy, bạn sẽ có sẵn toàn bộ dataset (nằm trong thư mục `datathon-2026-round-1/`) mà không cần tải thêm gì.

```bash
git clone https://github.com/hdungz/DATATHON26.git
cd DATATHON26
```

### Chú ý quan trọng khi chạy Local: Đổi Path

Do notebook mặc định cấu hình cho Kaggle, trước khi chạy trên máy cá nhân, bạn cần sửa đường dẫn thư mục dữ liệu ở **cell khai báo đầu tiên** của từng file:

**Đối với `datathon26-ec9819.ipynb` và `notebookmcq.ipynb`:**
```python
# Đổi từ:
DATA_DIR = '/kaggle/input/competitions/datathon-2026-round-1/'
# Thành:
DATA_DIR = 'datathon-2026-round-1/'
```

**Đối với `eda-datathon-final.ipynb`:**
```python
# Đổi từ:
base_path = "/kaggle/input/datasets/dungz878/datathon2026/"
# Thành:
base_path = "datathon-2026-round-1/"
```

### Tổng quan các Notebook

1. **Notebook dự đoán – `datathon26-ec9819.ipynb`**
   - Chạy lệnh: `jupyter notebook datathon26-ec9819.ipynb`
   - Mô tả: Load data `sales.csv`, Feature engineering theo chu kỳ Fourier, train mô hình tổng hợp Prophet + Hồi quy tuyến tính.
   - Output: file `submission.csv` (dự đoán Revenue & COGS) tạo tại thư mục hiện tại.

2. **Notebook EDA – `eda-datathon-final.ipynb`**
   - Chạy lệnh: `jupyter notebook eda-datathon-final.ipynb`
   - Mô tả: Phân tích xu hướng doanh thu dài hạn, vùng địa lý, kênh thanh toán, độ nhạy khuyến mãi. Chứa biểu đồ Plotly tương tác.

3. **Notebook MCQ – `notebookmcq.ipynb`**
   - Chạy lệnh: `jupyter notebook notebookmcq.ipynb`
   - Mô tả: Code giải đáp 10 câu hỏi trắc nghiệm của Vòng 1.
