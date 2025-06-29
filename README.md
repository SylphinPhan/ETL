# 📊 ETL Project: Enrollies & Employment Analysis

## 🧩 Giới thiệu
Dự án này tự động thực hiện quy trình ETL từ nhiều nguồn dữ liệu để phân tích mối quan hệ giữa đặc điểm học viên và khả năng được tuyển dụng sau khóa học.

## 📁 Nguồn dữ liệu sử dụng

| Nguồn | Loại | Link / Chi tiết |
|-------|------|------------------|
| Enrollies Info | Google Sheet | [Link](https://docs.google.com/spreadsheets/d/1VCkHwBjJGRJ21asd9pxW4_0z2PWuKhbLR3gUHm-p4GI) |
| Education Info | Excel (.xlsx) | [Link](https://assets.swisscoding.edu.vn/company_course/enrollies_education.xlsx) |
| Work Experience | CSV (.csv) | [Link](https://assets.swisscoding.edu.vn/company_course/work_experience.csv) |
| Training Hours | MySQL DB | `company_course.training_hours` |
| Employment | MySQL DB | `company_course.employment` |
| City Index | HTML Table | [Link](https://sca-programming-school.github.io/city_development_index/index.html) |
## 🛠️ Kết nối đến MySQL (Training Hours & Employment)

Dự án cần kết nối đến CSDL MySQL từ xa để truy xuất bảng `training_hours` và `employment`.

| Thông tin | Giá trị |
|----------|---------|
| Host     | 112.213.86.31 |
| Port     | 3360 |
| Username | etl_practice |
| Password | 550814 |
| Database | company_course |

## ⚙️ Các bước xử lý (ETL)

### 🔍 Extract
- Tải dữ liệu từ nhiều nguồn (Google Sheets, Excel, CSV, MySQL, HTML).

### 🧼 Transform
- Làm sạch dữ liệu (`dropna`, chuẩn hóa tên cột)
- Gộp dữ liệu theo `enrollee_id` để tạo bảng tổng hợp

### 💾 Load
- Lưu vào SQLite (`data.db`) với các bảng:
  - `Fact_epl` – bảng fact chứa thông tin tuyển dụng
  - `Dim_Edu`, `Dim_hours`, `Dim_exp`, `Dim_Enroll`, `Dim_city_dev` – bảng chiều

## 🚀 Hướng dẫn chạy

### 1. Cài thư viện
```bash
pip install -r requirements.txt
