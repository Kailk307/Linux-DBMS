# Triển khai MySQL trên Linux
## Mô tả: 
Dự án này triển khai một hệ thống quản lý dữ liệu MySQL trên máy chủ Linux, áp dụng các kiến thức về quản lý hệ điều hành Linux, cơ sở dữ liệu MySQL, và bảo mật hệ thống
### Mục tiêu chính:
1. Cài đặt và cấu hình MySQL trên hệ điều hành Linux (Ubuntu/CentOS).
2. Thiết lập cơ sở dữ liệu mẫu để quản lý thông tin nhân viên (Employee Management).
3. Tăng cường bảo mật MySQL bằng cách cấu hình quyền truy cập, đặt mật khẩu và tường lửa (firewall).
#### Các bước thực hiện dự án
1. Chuẩn bị môi trường
- Sử dụng Ubuntu Server 20.04 LTS làm hệ điều hành
- Link download: https://releases.ubuntu.com/focal/
- Cập nhật hệ thống:
#sudo apt update && sudo apt upgrade -y
- Cài đặt các gói cần thiết (nano, curl, firewall):
#sudo apt install nano ufw wget -y
2. Cài đặt và cấu hình MySQL
- Cài đặt MySQL:
 # sudo apt install mysql-server -y
- Kiểm tra dịch vụ MySQL:
  # sudo systemctl status mysql
- Đặt mật khẩu root MySQL và bảo mật MySQL:
  # sudo mysql_secure_installation
3. Tạo cơ sở dữ liệu và bảng dữ liệu
- Đăng nhập vào MySQL:
 # sudo mysql -u root -p
- Tạo một cơ sở dữ liệu mới và bảng nhân viên:
# CREATE DATABASE employee_db;
# USE employee_db;

# CREATE TABLE employees (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    position VARCHAR(50),
    salary DECIMAL(10, 2),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
- Chèn dữ liệu vào bảng nhân viên
# INSERT INTO employees (name, position, salary) VALUES
       ('Nguyen Van A', 'Manager', 1500.00),
       ('Tran Thi B', 'Developer', 1200.00),
       ('Le Van C', 'Tester', 1000.00);
4. Tăng cường bảo mật MySQL
- Cấu hình tường lửa (UFW) để chỉ cho phép cổng 3306 kết nối từ localhost:
# sudo ufw allow 3306
# sudo ufw enable
- Cấu hình user và cấp quyền cụ thể:
# CREATE USER 'admin'@'localhost' IDENTIFIED BY 'password123';
# GRANT ALL PRIVILEGES ON employee_db.* TO 'admin'@'localhost';
# FLUSH PRIVILEGES;
- Kiểm tra kết nối bằng tài khoản admin:
#  mysql -u admin -p



