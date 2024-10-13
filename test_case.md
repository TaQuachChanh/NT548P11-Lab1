# Test Cases for VPC and EC2 Deployment

## 1. VPC Configuration Test Cases

### Test Case 1.1: Verify VPC Creation
- Description: Kiểm tra VPC đã được tạo với đúng CIDR block
- Steps:
  1. Mở AWS VPC Console
  2. Tìm VPC với tên được chỉ định trong stack
  3. Kiểm tra CIDR block của VPC
- Expected Result: VPC tồn tại với đúng CIDR block
- Actual Result: [Fill after testing]
- Status: [Pass/Fail]

### Test Case 1.2: Verify Subnet Creation
- Description: Kiểm tra Public và Private Subnet đã được tạo
- Steps:
  1. Trong VPC Console, chọn Subnets
  2. Xác nhận có ít nhất một Public Subnet và một Private Subnet
  3. Kiểm tra CIDR block của mỗi subnet
- Expected Result: Có ít nhất một Public và một Private Subnet với đúng CIDR block
- Actual Result: [Fill after testing]
- Status: [Pass/Fail]

### Test Case 1.3: Verify Internet Gateway
- Description: Kiểm tra Internet Gateway đã được tạo và gắn vào VPC
- Steps:
  1. Trong VPC Console, chọn Internet Gateways
  2. Tìm Internet Gateway được tạo cho VPC
  3. Xác nhận nó đã được gắn (attached) vào VPC
- Expected Result: Internet Gateway tồn tại và được gắn vào VPC
- Actual Result: [Fill after testing]
- Status: [Pass/Fail]

### Test Case 1.4: Verify NAT Gateway
- Description: Kiểm tra NAT Gateway đã được tạo trong Public Subnet
- Steps:
  1. Trong VPC Console, chọn NAT Gateways
  2. Tìm NAT Gateway được tạo
  3. Xác nhận nó nằm trong Public Subnet
- Expected Result: NAT Gateway tồn tại trong Public Subnet
- Actual Result: [Fill after testing]
- Status: [Pass/Fail]

## 2. Route Table Test Cases

### Test Case 2.1: Verify Public Route Table
- Description: Kiểm tra Public Route Table có route đến Internet Gateway
- Steps:
  1. Trong VPC Console, chọn Route Tables
  2. Tìm Route Table cho Public Subnet
  3. Kiểm tra có route 0.0.0.0/0 trỏ đến Internet Gateway
- Expected Result: Public Route Table có route đến Internet Gateway
- Actual Result: [Fill after testing]
- Status: [Pass/Fail]

### Test Case 2.2: Verify Private Route Table
- Description: Kiểm tra Private Route Table có route đến NAT Gateway
- Steps:
  1. Trong VPC Console, chọn Route Tables
  2. Tìm Route Table cho Private Subnet
  3. Kiểm tra có route 0.0.0.0/0 trỏ đến NAT Gateway
- Expected Result: Private Route Table có route đến NAT Gateway
- Actual Result: [Fill after testing]
- Status: [Pass/Fail]

## 3. EC2 Instance Test Cases

### Test Case 3.1: Verify Public EC2 Instance
- Description: Kiểm tra Public EC2 Instance có thể truy cập từ Internet
- Steps:
  1. Trong EC2 Console, tìm Public EC2 Instance
  2. Lấy Public IP của instance
  3. Thử SSH vào instance: `ssh -i your-key.pem ec2-user@public-ip`
- Expected Result: Có thể SSH thành công vào Public Instance
- Actual Result: [Fill after testing]
- Status: [Pass/Fail]

### Test Case 3.2: Verify Private EC2 Instance
- Description: Kiểm tra Private EC2 Instance chỉ có thể truy cập từ Public Instance
- Steps:
  1. SSH vào Public EC2 Instance
  2. Từ Public Instance, thử SSH vào Private Instance: `ssh -i your-key.pem ec2-user@private-ip`
  3. Thử ping google.com từ Private Instance
- Expected Result: Có thể SSH từ Public đến Private Instance và ping google.com thành công
- Actual Result: [Fill after testing]
- Status: [Pass/Fail]

## 4. Security Group Test Cases

### Test Case 4.1: Verify Public EC2 Security Group
- Description: Kiểm tra Security Group của Public EC2 chỉ cho phép SSH từ IP cụ thể
- Steps:
  1. Trong EC2 Console, xem Security Group của Public Instance
  2. Kiểm tra Inbound rules chỉ cho phép SSH (port 22) từ IP đã chỉ định
  3. Thử SSH từ IP được phép và một IP không được phép
- Expected Result: Chỉ có thể SSH từ IP được phép
- Actual Result: [Fill after testing]
- Status: [Pass/Fail]

### Test Case 4.2: Verify Private EC2 Security Group
- Description: Kiểm tra Security Group của Private EC2 chỉ cho phép kết nối từ Public EC2
- Steps:
  1. Trong EC2 Console, xem Security Group của Private Instance
  2. Kiểm tra Inbound rules chỉ cho phép kết nối từ Security Group của Public EC2
  3. Thử kết nối từ Public EC2 và từ một nguồn khác
- Expected Result: Chỉ có thể kết nối từ Public EC2
- Actual Result: [Fill after testing]
- Status: [Pass/Fail]

## 5. Overall Connectivity Test

### Test Case 5.1: End-to-End Connectivity Test
- Description: Kiểm tra kết nối từ Internet đến Public EC2 và từ Public EC2 đến Private EC2
- Steps:
  1. SSH vào Public EC2 từ máy local
  2. Từ Public EC2, SSH vào Private EC2
  3. Từ Private EC2, ping google.com
- Expected Result: Có thể thực hiện tất cả các bước trên thành công
- Actual Result: [Fill after testing]
- Status: [Pass/Fail]
