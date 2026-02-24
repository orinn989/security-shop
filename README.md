# 🛡️ SecureShop — E-Commerce & POS Security Devices Management System

Hệ thống quản lý và bán hàng E-Commerce tích hợp POS (Bán hàng tại quầy) chuyên dụng cho các thiết bị an ninh (camera, cảm biến, khóa thông minh...). Hệ thống cung cấp giải pháp toàn diện từ bán hàng online, quản lý kho bãi, đến hỗ trợ chăm sóc khách hàng và bảo hành sản phẩm.

---

## 📖 Overview

**1. Purpose (Mục đích)**  
Xây dựng một nền tảng thương mại điện tử kết hợp hệ thống POS mạnh mẽ, giúp số hóa quy trình bán lẻ thiết bị an ninh. Đảm bảo luồng dữ liệu thông suốt từ lúc nhập kho, bán hàng (online + offline), đến khi hỗ trợ sau bán.

**2. Problem it solves (Vấn đề giải quyết)**  
- Quản lý kho hàng thiết bị an ninh phức tạp với số serial/phiên bản cụ thể.
- Tích hợp bán hàng đa kênh: Khách hàng mua online qua Web, Nhân viên bán hàng trực tiếp tại quầy qua màn hình POS nhanh chóng.
- Theo dõi toàn trình trạng thái bảo hành, yêu cầu hỗ trợ khi thiết bị gặp sự cố.

**3. Target users (Đối tượng người dùng)**  
- **Khách hàng (Customer):** Mua sắm thiết bị an ninh, theo dõi đơn hàng, gửi yêu cầu bảo hành/hỗ trợ đổi trả.
- **Nhân viên (Staff):** Thao tác bán hàng tại quầy (POS), quản lý kho, in hóa đơn, chăm sóc khách hàng.
- **Quản trị viên (Admin):** Quản lý toàn bộ hệ thống, xem báo cáo doanh thu, quản lý nhân viên.

**4. Real-world use case (Ứng dụng thực tế)**  
Chuỗi cửa hàng bán lẻ thiết bị camera an ninh, thiết bị nhà thông minh sử dụng hệ thống để đồng bộ tồn kho giữa cửa hàng và website, xử lý thanh toán tự động qua VNPay và xuất báo cáo PDF cuối ngày.

---

## ✨ Features

- **🛍️ E-Commerce & Product Management (Quản lý sản phẩm & Bán hàng):**
  - Quản lý danh mục, nhãn hiệu, và biến thể sản phẩm chi tiết.
  - Quản lý giỏ hàng với Session lưu trữ trên Redis.
  - Xử lý đơn hàng, theo dõi lộ trình giao hàng (Shipment).
- **🏪 POS System (Bán hàng tại quầy):**
  - Giao diện bán hàng nhanh cho thu ngân.
  - Hỗ trợ quét mã vạch (Barcode) để thanh toán tức thì.
- **📦 Inventory & Barcode Tracking (Quản lý kho & Mã vạch):**
  - Kiểm soát tồn kho, theo dõi lịch sử nhập/xuất kho (StockLog).
  - Khởi tạo và quản lý Barcode cho từng mặt hàng (EAN-13 hoặc tự sinh).
- **💳 Payment & Invoicing (Thanh toán & Hóa đơn):**
  - Thanh toán online an toàn qua VNPay.
  - Tự động tạo và xuất hóa đơn PDF chuyên nghiệp (OpenPDF).
- **🔐 Authentication & Authorization (Xác thực & Phân quyền):**
  - Đăng nhập bảo mật sử dụng JWT (JSON Web Tokens).
  - Tích hợp đăng nhập Social Login (OAuth2 - Google/Facebook).
  - Phân quyền chặt chẽ Role-based Access Control (Admin / Staff / Customer).
- **🛠️ Support & Warranty (Hỗ trợ & Bảo hành):**
  - Quản lý yêu cầu bảo hành (Warranty Requests) và ticket hỗ trợ (Support Tickets).
  - Tích hợp Live Chat hỗ trợ khách hàng.
- **📊 Reporting & Analytics (Báo cáo & Thống kê):**
  - Tổng hợp dữ liệu doanh thu, phân tích sản phẩm bán chạy.

---

## 🏛️ System Architecture

- **Pattern Used:** Kiến trúc đa tầng (N-Tiered / Layered Architecture) chuẩn hóa cho Spring Boot bao gồm: `Controller` -> `Service` -> `Repository` -> `Database`. Kết hợp DTO (Data Transfer Object) Pattern và Mapper để đảm bảo an toàn dữ liệu trả về Frontend.
- **Component Structure:**
  - **Client (Frontend):** React.js SPAs tạo giao diện người dùng tương tác cao, quản lý state bằng Redux Toolkit.
  - **API Server (Backend):** Spring Boot đóng vai trò RESTful API cung cấp dữ liệu, xử lý nghiệp vụ, đảm bảo ACID cho các giao dịch.
  - **Caching Layer:** Redis dùng để tối ưu hóa truy xuất và quản lý giỏ hàng/session.
- **Data Flow Overview:**
  Client gửi HTTP request (kèm JWT Header) -> Spring Security Filter (Xác thực/Phân quyền) -> Controller (Tiếp nhận/Validate) -> Service (Xử lý Business Logic) -> Repository (Giao tiếp Database) -> Trả về Client (JSON).

---

## 💻 Technology Stack

**Backend:**
- **Framework:** Java 21, Spring Boot 3
- **ORM & Data Access:** Spring Data JPA, Hibernate, JDBC
- **Security:** Spring Security, OAuth2 Client, JWT (Auth0)
- **Caching & Media:** Spring Data Redis, Supabase (cho Storage/File Upload)
- **Tools:** OpenPDF, Lombok, Maven

**Frontend:**
- **Core:** React 19 (TypeScript), Vite
- **Styling:** TailwindCSS, Radix UI Themes
- **State Management:** Redux Toolkit, Redux Persist
- **Form & Validation:** React Hook Form, Zod
- **Libraries:** Framer Motion (Animation), Recharts (Biểu đồ), Axios

**Database:**
- **Primary DB:** Microsoft SQL Server (MSSQL)
- **In-memory DB:** Redis Server

**Other Tools:**
- Git & GitHub
- IntelliJ IDEA / VS Code
- Docker (Planned for deployment)

---

## 🗄️ Database Design

Hệ thống được thiết kế theo chuẩn Database Normalization, các Entities chính bao gồm:
- **`User` / `Address`:** Lưu thông tin người dùng, tài khoản và nhiều địa chỉ giao hàng.
- **`Product` / `Category` / `Brand` / `MediaAsset`:** Lưu trữ thông tin phân cấp sản phẩm, hệ thống hình ảnh và thương hiệu.
- **`Inventory` / `StockLog` / `Barcode`:** Quản lý kho, theo dõi số lượng tồn thực tế của từng sản phẩm và các mã vạch đi kèm.
- **`Order` / `OrderItem`:** Xử lý đơn hàng E-Commerce, quản lý các mặt hàng trong từng đơn.
- **`Invoice` / `InvoiceItem` / `Payment`:** Lưu trữ dữ liệu thanh toán và biên lai xuất cho khách hàng hoặc từ hệ thống POS.
- **`Discount`:** Hệ thống mã khuyến mãi, giảm giá.
- **`SupportTicket` / `WarrantyRequest` / `Review`:** Xử lý các nghiệp vụ chăm sóc khách hàng, phản hồi và chính sách hậu mãi.

---

## ⚙️ Installation

**1. Clone repository**
```bash
git clone https://github.com/yourusername/secureshop.git
cd secureshop
```

**2. Setup Database & Redis**
- Cài đặt **SQL Server** và tạo database tên `secure_shop`.
- Cài đặt và khởi chạy **Redis server** trên port mặc định `6379`.

**3. Configure Environment Variables**
Tạo file `backend/.env` với các cấu hình bảo mật:
```env
DB_URL=jdbc:sqlserver://localhost:1433;databaseName=secure_shop;encrypt=true;trustServerCertificate=true
DB_USERNAME=your_db_username
DB_PASSWORD=your_db_password
JWT_SECRET=your_super_secret_jwt_key
REDIS_HOST=localhost
REDIS_PORT=6379
OAUTH2_GOOGLE_CLIENT_ID=your_google_client_id
OAUTH2_GOOGLE_CLIENT_SECRET=your_google_client_secret
```

Tạo file `frontend/.env` với cấu hình API:
```env
VITE_API_BASE_URL=http://localhost:8080/api/v1
```

**4. Run Backend Server**
- Mở thư mục `backend` bằng IntelliJ IDEA hoặc Eclipse.
- Reload Maven dependencies.
- Chạy file `SecureShopApplication.java` hoặc dùng command:
```bash
cd backend
./mvnw spring-boot:run
```

**5. Run Frontend Application**
- Mở thư mục `frontend` bằng VS Code.
```bash
cd frontend
npm install
npm run dev
```
Hệ thống frontend sẽ chạy tại địa chỉ: `http://localhost:5173`.

---

## 🎯 Usage

- **Truy cập cửa hàng:** Mở trình duyệt tại `http://localhost:5173`. Khách hàng có thể tìm kiếm, chọn mua thiết bị an ninh và thêm vào giỏ hàng.
- **Thanh toán:** Khách hàng tiến hành Checkout, có thể lựa chọn thanh toán qua VNPay hoặc COD.
- **Trang Quản trị (Admin Dashboard):** Admin đăng nhập sẽ được điều hướng vào khu vực quản trị để xem Analytics (Thống kê), xét duyệt Order (Đơn hàng), và Quản lý Kho (Inventory).
- **Hệ thống POS:** Nhân viên thu ngân truy cập `/pos` để mở giao diện point-of-sale đa cột, quét mã sản phẩm và gen Hóa đơn (Invoice) dạng PDF trực tiếp.

---

## 🖼️ Screenshots

*(Placeholder cho các hình ảnh thực tế của hệ thống)*

| Cửa hàng trực tuyến (E-Commerce) | Hệ thống bán hàng tại quầy (POS) |
|-----------------------------------|-----------------------------------|
| ![E-Commerce Home](https://via.placeholder.com/600x400?text=E-Commerce+Storefront) | ![POS Interface](https://via.placeholder.com/600x400?text=POS+System+Interface) |

| Admin Dashboard (Thống kê) | Quét mã vạch & Quản lý Kho |
|-----------------------------|-----------------------------|
| ![Analytics](https://via.placeholder.com/600x400?text=Analytics+Dashboard) | ![Inventory](https://via.placeholder.com/600x400?text=Inventory+&+Barcode) |

---

## 📂 Project Structure

```text
secureshop/
├── backend/                  # Spring Boot API Server
│   ├── src/main/java.../     # Mã nguồn Java
│   │   ├── config/           # Cấu hình Bean, Redis, Security, Swagger
│   │   ├── controller/       # REST API endpoints (POS, Auth, Products...)
│   │   ├── dto/              # Data Transfer Objects
│   │   ├── entities/         # JPA Entities map với SQL Server
│   │   ├── exception/        # Global Exception Handler
│   │   ├── mapper/           # Mapstruct/DTO Converters
│   │   ├── repositories/     # Spring Data JPA Repositories
│   │   ├── security/         # JWT Filters, OAuth2 Configuration
│   │   └── service/          # Business Logic Layer
│   └── pom.xml               # Maven dependencies
│
└── frontend/                 # React + Vite Client
    ├── src/
    │   ├── assets/           # Hình ảnh, icons, styles chung
    │   ├── components/       # Reusable UI components
    │   ├── hooks/            # Custom React Hooks
    │   ├── layouts/          # Các Layout chính (Admin, Client, POS)
    │   ├── pages/            # View theo từng Route
    │   ├── redux/            # Store quản lý state
    │   ├── services/         # API call (Axios)
    │   └── utils/            # Helper functions
    ├── package.json          # Node dependencies
    └── tailwind.config.js    # Cấu hình TailwindCSS
```

---

## 🌟 Key Technical Highlights

- **Clean & Layered Architecture:** Đảm bảo tính mở rộng cao và tách biệt rõ ràng giữa Business Logic và Cấu trúc Data, tuân thủ SOLID principles.
- **DTO & DAO (Repository) Pattern:** Cô lập database entity khỏi Presentation layer, giúp bảo mật cấu trúc thiết kế cơ sở dữ liệu và tối ưu hóa payload truyền tải mạng.
- **Security Best Practices:** Xác thực Stateless qua JWT, thiết kế Filter cấp thấp chặn request độc hại. Mật khẩu được băm toàn bộ trên database sử dụng thuật toán Bcrypt.
- **Tối ưu hiệu năng:** 
  - Áp dụng Redis Cache để tăng tốc độ truy vấn đối với dữ liệu tần suất đọc cao.
  - Phân trang (Pagination) và Lọc dữ liệu động phía Database với JPA Specification.
- **Thiết kế CSDL chuẩn hóa:** Áp dụng Database Normalization chặt chẽ, sử dụng khóa ngoại, Index đánh đúng trọng tâm tại các trường truy vấn liên tục trên SQL Server.

---

## 🚀 Future Improvements

- Áp dụng Microservices Architecture nếu hệ thống scale quy mô doanh nghiệp lớn.
- Bổ sung ElasticSearch hỗ trợ tìm kiếm toàn văn bản (Full-text Search) mượt mà cho tập sản phẩm lớn.
- Triển khai Docker Compose cho toàn bộ vòng đời ứng dụng, thiết lập CI/CD pipeline với GitHub Actions.
- Tích hợp thêm AI gợi ý sản phẩm dựa trên hành vi người mua.

---

## ✒️ Author

**Fiveting.org Development Team**  
*Mã nguồn thuộc đồ án phát triển Hệ thống phần mềm chuyên sâu.*

---

## ⚖️ License

Dự án được phân phối dưới giấy phép **MIT License**. Bạn có quyền tự do sửa đổi, phân phối với mục đích cá nhân hoặc nội bộ doanh nghiệp.
