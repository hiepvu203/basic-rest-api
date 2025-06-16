# Dự án Todo REST API với Go và Gin

## Giới thiệu

Đây là một dự án mẫu xây dựng RESTful API quản lý công việc (**Todo List**) sử dụng ngôn ngữ lập trình **Go** và framework **Gin**. API cho phép bạn thực hiện các thao tác cơ bản như: lấy danh sách công việc, thêm mới, xem chi tiết và cập nhật trạng thái hoàn thành của từng công việc.

---

## Tính năng

- **Lấy danh sách tất cả công việc**  
  `GET /todos`
- **Thêm công việc mới**  
  `POST /todos`
- **Xem chi tiết một công việc theo ID**  
  `GET /todos/:id`
- **Chuyển đổi trạng thái hoàn thành của công việc**  
  `PATCH /todos/:id`

---

## Cài đặt

### Yêu cầu
- Go >= 1.18
- Git

### Cách chạy dự án

```sh
# 1. Clone dự án
git clone <repository-url>
cd rest-api

# 2. Cài đặt các package phụ thuộc
go mod tidy

# 3. Chạy ứng dụng
go run main.go
```
Ứng dụng sẽ chạy tại địa chỉ: [http://localhost:9090](http://localhost:9090)

---

## 📁 Cấu trúc dự án

```
rest-api/
├── go.mod
├── go.sum
└── main.go
```
- **main.go**: Chứa toàn bộ mã nguồn API.
- **go.mod, go.sum**: Quản lý các package phụ thuộc.

---

## 🔗 Mô tả API

### 1. Lấy danh sách công việc
- **Endpoint:** `GET /todos`
- **Response:**
  ```json
  [
    {
      "id": "1",
      "item": "Learn Go",
      "completed": false
    },
    ...
  ]
  ```

### 2. Thêm công việc mới
- **Endpoint:** `POST /todos`
- **Request Body:**
  ```json
  {
    "id": "4",
    "item": "Viết tài liệu",
    "completed": false
  }
  ```
- **Response:** Trả về công việc vừa thêm.

### 3. Xem chi tiết công việc
- **Endpoint:** `GET /todos/:id`
- **Response:**
  ```json
  {
    "id": "1",
    "item": "Learn Go",
    "completed": false
  }
  ```

### 4. Chuyển đổi trạng thái hoàn thành
- **Endpoint:** `PATCH /todos/:id`
- **Response:** Trả về công việc với trạng thái đã được cập nhật.

---

## 💡 Ví dụ sử dụng với curl

```sh
# Lấy danh sách công việc
curl http://localhost:9090/todos

# Thêm công việc mới
curl -X POST http://localhost:9090/todos \
  -H "Content-Type: application/json" \
  -d '{"id":"4","item":"Viết tài liệu","completed":false}'

# Xem chi tiết công việc
curl http://localhost:9090/todos/1

# Chuyển đổi trạng thái hoàn thành
curl -X PATCH http://localhost:9090/todos/1
```
---