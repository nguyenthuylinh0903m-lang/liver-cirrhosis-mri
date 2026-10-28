# Phân vùng và phân loại xơ gan dựa trên ảnh MRI

## 1. Giới thiệu

Xơ gan là bệnh lý mạn tính của gan, đặc trưng bởi sự hình thành mô sẹo và những thay đổi trong cấu trúc gan. Ảnh cộng hưởng từ (Magnetic Resonance Imaging – MRI) cung cấp thông tin về cấu trúc và đặc điểm mô của gan, hỗ trợ nghiên cứu các phương pháp phân tích hình ảnh y tế.

Đề tài khảo sát các phương pháp xử lý ảnh và học máy để phân tích ảnh MRI gan, hướng tới xây dựng quy trình phân vùng vùng quan tâm và phân loại theo nhãn có trong bộ dữ liệu. Phạm vi và phương pháp cụ thể sẽ được chốt sau khi kiểm tra dữ liệu thực tế.

## 2. Mục tiêu

- Khảo sát nguồn dữ liệu, cấu trúc, định dạng ảnh và nhãn.
- Tiền xử lý ảnh MRI phù hợp với định dạng và đặc điểm dữ liệu.
- Nghiên cứu phân vùng vùng quan tâm trên ảnh MRI, tùy thuộc vào việc bộ dữ liệu có nhãn phân vùng hay không.
- Trích xuất đặc trưng từ ảnh hoặc vùng đã phân vùng.
- Xây dựng và đánh giá mô hình phân loại theo các nhóm chẩn đoán thực tế trong bộ dữ liệu.
- So sánh các phương pháp bằng những chỉ số đánh giá phù hợp và trình bày rõ giới hạn của kết quả.

## 3. Dữ liệu

Đề tài sử dụng bộ dữ liệu ảnh MRI gan. Nguồn dữ liệu, thông tin bệnh nhân, số lượng ảnh và nhãn chưa được xác nhận; các chi tiết này sẽ được bổ sung sau khi kiểm tra dữ liệu thực tế. Không giả định trước bộ dữ liệu có nhãn xơ gan hoặc mặt nạ phân vùng.

Các thông tin cần thống kê:

- Tên, nguồn, giấy phép và điều kiện sử dụng bộ dữ liệu.
- Loại ảnh MRI, chuỗi xung, định dạng tệp và số chiều ảnh.
- Số lượng bệnh nhân, ca chụp, thể tích ảnh và lát cắt.
- Các nhãn chẩn đoán, số lượng mẫu mỗi nhóm và cách xác định nhãn.
- Sự tồn tại, định dạng và ý nghĩa của mặt nạ phân vùng.
- Dữ liệu thiếu, chất lượng ảnh và các đặc điểm có thể gây sai lệch.

Việc chia tập huấn luyện, kiểm định và kiểm thử cần thực hiện theo bệnh nhân (nếu xác định được mã bệnh nhân), tránh để các lát cắt từ cùng một bệnh nhân xuất hiện ở cả tập huấn luyện và tập đánh giá.

## 4. Phương pháp thực hiện

### 4.1. Khảo sát và tiền xử lý dữ liệu

- Kiểm tra cấu trúc thư mục, định dạng, kích thước, hướng ảnh, khoảng cách voxel và thông tin metadata.
- Đối chiếu ảnh với nhãn chẩn đoán và mặt nạ phân vùng (nếu có).
- Kiểm tra dữ liệu lỗi, trùng lặp, thiếu nhãn và mất cân bằng giữa các nhóm.
- Xây dựng quy trình tiền xử lý phù hợp với dữ liệu, có thể gồm chuẩn hóa cường độ, thay đổi kích thước, xử lý vùng ảnh và tăng cường dữ liệu.
- Chỉ áp dụng các phép biến đổi phù hợp với ý nghĩa giải phẫu; tham số tiền xử lý được ước lượng trên tập huấn luyện để hạn chế rò rỉ dữ liệu.

### 4.2. Phân vùng vùng quan tâm

Phương pháp phân vùng phụ thuộc vào nhãn có sẵn:

- **Nếu có mặt nạ:** huấn luyện và đánh giá mô hình phân vùng có giám sát, đồng thời so sánh với một phương pháp cơ sở phù hợp.
- **Nếu không có mặt nạ:** khảo sát phương pháp xử lý ảnh hoặc phân vùng không giám sát; nếu cần nhãn chuẩn để đánh giá, phải tạo hoặc thu thập nhãn với quy trình được mô tả rõ.
- Có thể tập trung vào gan hoặc vùng tổn thương chỉ khi dữ liệu và nhãn cho phép xác định đáng tin cậy.

Kết quả phân vùng được đánh giá bằng Dice và IoU; có thể bổ sung các chỉ số khác khi phù hợp với mục tiêu và cách tạo nhãn chuẩn. Kết quả cần được tổng hợp ở mức lát cắt hoặc bệnh nhân một cách nhất quán.

### 4.3. Trích xuất đặc trưng và phân loại

- Thiết lập đường cơ sở bằng các đặc trưng ảnh phù hợp, chẳng hạn đặc trưng hình thái hoặc kết cấu, nếu dữ liệu cho phép.
- Khảo sát mô hình học máy truyền thống và/hoặc học sâu tùy theo quy mô, định dạng dữ liệu và nhãn.
- So sánh việc phân loại từ ảnh gốc với phân loại từ vùng đã phân vùng, khi thiết kế thí nghiệm cho phép.
- Chỉ sử dụng các nhóm chẩn đoán thực sự có trong dữ liệu; không suy diễn nhãn hoặc ý nghĩa lâm sàng từ ảnh.
- Hiệu chỉnh siêu tham số trên tập huấn luyện/kiểm định, không sử dụng tập kiểm thử để lựa chọn mô hình.

### 4.4. Đánh giá và so sánh

Với phân loại, báo cáo ma trận nhầm lẫn, accuracy, precision, recall và F1-score. Với bài toán nhiều lớp hoặc dữ liệu mất cân bằng, cần nêu rõ cách tính trung bình (macro, micro hoặc weighted); chỉ báo cáo ROC-AUC khi cách tính phù hợp với số lớp và thiết kế đánh giá.

Các kết quả cần:

- Được đo trên tập kiểm thử độc lập, chia theo bệnh nhân khi có thể.
- Bao gồm kết quả theo từng lớp bên cạnh chỉ số tổng hợp.
- So sánh với đường cơ sở và trình bày thiết lập thí nghiệm để có thể tái lập.
- Ghi nhận độ biến thiên hoặc khoảng tin cậy khi số lượng mẫu cho phép.
- Nêu các giới hạn do quy mô dữ liệu, mất cân bằng, khác biệt máy chụp/chuỗi xung và chất lượng nhãn.

## 5. Kế hoạch thực hiện

1. Khảo sát dữ liệu và xác nhận nhãn, đơn vị phân tích.
2. Xây dựng quy trình kiểm tra và tiền xử lý.
3. Thiết lập phương pháp phân vùng dựa trên nhãn hiện có.
4. Xây dựng đường cơ sở và các mô hình phân loại.
5. Đánh giá, so sánh, phân tích lỗi và tổng hợp kết quả.

Thứ tự và phạm vi có thể điều chỉnh sau khi xác định được cấu trúc dữ liệu và khả năng tạo tập đánh giá độc lập.

## 6. Kết quả dự kiến

- Báo cáo khảo sát bộ dữ liệu và các quyết định tiền xử lý.
- Quy trình thử nghiệm phân vùng (nếu dữ liệu hỗ trợ) và phân loại.
- Bảng so sánh kết quả định lượng cùng phân tích lỗi.
- Mã nguồn và hướng dẫn tái lập thí nghiệm, trong phạm vi điều kiện cấp phép dữ liệu cho phép.

## 7. Giới hạn và lưu ý

Đây là đề tài nghiên cứu xử lý ảnh và học máy trên bộ dữ liệu hiện có, không phải công cụ chẩn đoán. Kết quả mô hình không thay thế đánh giá của chuyên gia y tế và không được diễn giải như bằng chứng về hiệu quả lâm sàng. Dữ liệu y tế cần được sử dụng theo giấy phép, quy định bảo mật và phê duyệt phù hợp; không đưa thông tin nhận dạng bệnh nhân vào mã nguồn hoặc báo cáo công khai.