# Detecting TCP SYN Port Scanning using Wireshark
## Giới thiệu
Project này mô phỏng và phân tích hoạt động quét cổng (Port Scanning) trong mạng. 
Cuộc tấn công được thực hiện bằng Nmap và lưu lượng mạng được bắt và phân tích bằng Wireshark để phát hiện dấu hiệu quét cổng.

## Mục tiêu
- Hiểu cách hoạt động của kỹ thuật Port Scanning
- Bắt lưu lượng mạng trong quá trình quét cổng
- Phân tích các gói tin TCP SYN
- Xác định địa chỉ IP của attacker thực hiện quét cổng

## Công cụ
- Wireshark
- Nmap

## Môi trường lab
- Kali Linux (máy tấn công)
- Windows 10 (máy mục tiêu)

## Mô phỏng tấn công
Thực hiện quét cổng từ máy Kali Linux bằng lệnh:

nmap -p 1-600 <target-ip>

Lệnh này gửi nhiều gói TCP SYN tới các cổng khác nhau trên máy mục tiêu.

## Phân tích lưu lượng mạng
Sử dụng Wireshark với filter sau:

tcp.flags.syn == 1 && tcp.flags.ack == 0
tcp.flags.reset == 1
Filter này giúp phát hiện các gói SYN được gửi tới nhiều cổng khác nhau, dấu hiệu của hoạt động quét cổng.

## Kết quả
- Phát hiện nhiều gói SYN từ một địa chỉ IP gửi tới nhiều cổng khác nhau.
- Máy mục tiêu phản hồi bằng gói RST đối với các cổng đóng.
- Dấu hiệu này cho thấy có hoạt động TCP SYN Port Scanning.

## Cấu trúc project
report.pdf – báo cáo phân tích chi tiết  
pcapng – file capture lưu lượng mạng  
screenshots – hình ảnh minh họa phân tích packet
