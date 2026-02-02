# 5G_Channel_Coding_Polar_vs_LDPC_Codes
Dự án này thực hiện mô phỏng và so sánh chi tiết hiệu năng của hai loại mã hóa kênh chính trong tiêu chuẩn 5G NR: Polar Codes và LDPC Codes, sử dụng thư viện mô phỏng lớp vật lý Sionna (NVIDIA).
1. Mục tiêu
- So sánh hiệu năng: Đánh giá tỷ lệ lỗi bit (BER) và lỗi khối (BLER) của Polar và LDPC dưới các điều kiện SNR khác nhau.Phân tích độ dài khối: Làm rõ lý do 5G chọn Polar cho gói tin ngắn (Control Channel) và LDPC cho gói tin dài (Data Channel).
- Đánh giá thuật toán: So sánh các thuật toán giải mã thực tế (BP, SCL) với giới hạn tối ưu lý thuyết (OSD/ML).
- Khảo sát thông lượng: Phân tích sự đánh đổi giữa độ phức tạp tính toán và tốc độ giải mã.

2. Cách cài đặt và chạy code
Dự án được thiết kế để chạy trên Google Colab. 
- Mở file .ipynb trong Google Colab.
- Đảm bảo môi trường đã kích hoạt CPU (Runtime > Change runtime type > CPU)
- Cài đặt thư viện Sionna bằng lệnh:!pip install tensorflow sionna numpy matplotlib
- Chạy các cell theo thứ tự

3. Kết quả chính
- Hiệu năng sửa lỗi (BER/BLER)
Mã ngắn (N < 128): Polar Code vượt trội hơn LDPC đáng kể. Giải mã SCL-8 giúp Polar tiệm cận giới hạn tối ưu.
Mã dài (N > 1000): LDPC chiếm ưu thế, đường cong lỗi dốc đứng (waterfall) và đạt được hiệu suất cao hơn khi tăng kích thước khối.
- Tính linh hoạt (Rate-Matching)
Mã Polar 5G thể hiện khả năng thích ứng tuyệt vời với độ dài bit bất kỳ thông qua các kỹ thuật đục lỗ (Puncturing) và rút ngắn (Shortening).
- Thông lượng & Độ phức tạp
LDPC: Thông lượng ổn định, độ phức tạp tỷ lệ tuyến tính với độ dài mã, không phụ thuộc SNR.
Polar Hybrid: Tốc độ giải mã tăng mạnh khi SNR tốt (do chỉ cần dùng giải mã SC đơn giản) và giảm khi SNR thấp (do phải kích hoạt SCL phức tạp).

Kết luận: Dự án khẳng định tính đúng đắn của chuẩn 5G NR khi phân chia vai trò: Polar cho kênh điều khiển và LDPC cho kênh dữ liệu.
