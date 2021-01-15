# Cac_van_de_ve_sieu_tham_so

## ML là quá trình mang tính lặp lại cao:
<img src = 'https://i.imgur.com/piDPivF.jpg'>

Đứng trước 1 vấn đề: bạn có ý tưởng --> code -->  kiểm nghiệm xem mô hình có ok hay ko?  
Và vấn đề là làm sao để thúc đẩy nhanh vòng lặp này, việc lựa chọn các siêu tham số như thế nào, xử lý ra sao ?

## Việc lựa chọn chia tách dữ liệu ra sao?
<img src ='https://i.imgur.com/ExTH607.jpg'>

Thời xưa, khi dữ liệu chưa nhiều, ta có thể chia dữ liệu thành train/ test theo tỷ lệ 70/30; hoặc train/dev/test thành 60/20/20.   
Nhưng khi dữ liệu thu thập được lờn (>1.000.000, ...) thì việc chia tách nên cân nhắc lại có thể là 99/ 0.5/0.5 là đã ok rồi. 
Dẫu nguồn dữ liệu rất nhiều nhưng ML vẫn ở trong 1 cơn đói về dữ liệu, và dữ liệu sẽ được tập hợp từ nhiều nguồn khác nhau --> các phân phối sẽ khác nhau.   
Việc đào tạo mô hình ML phải lưu ý tập dev/ test phải đến từ 1 phân phối!!!!

