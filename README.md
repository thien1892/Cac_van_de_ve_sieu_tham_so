# Cac_van_de_ve_sieu_tham_so

## ML là quá trình mang tính lặp lại cao:
<img src = 'https://i.imgur.com/piDPivF.jpg'>

Đứng trước 1 vấn đề: bạn có ý tưởng --> code -->  kiểm nghiệm xem mô hình có ok hay ko?  
Và vấn đề là làm sao để thúc đẩy nhanh vòng lặp này, việc lựa chọn các siêu tham số như thế nào, xử lý ra sao ?

## Việc lựa chọn chia tách dữ liệu ra sao?
<img src ='https://i.imgur.com/ExTH607.jpg'>

Thời xưa, khi dữ liệu chưa nhiều, ta có thể chia dữ liệu thành train/ test theo tỷ lệ 70/30; hoặc train/dev/test thành 60/20/20.   
Nhưng khi dữ liệu thu thập được lớn (>1.000.000, ...) thì việc chia tách nên cân nhắc lại có thể là 99/ 0.5/0.5 là đã ok rồi. 
Dẫu nguồn dữ liệu rất nhiều nhưng ML vẫn ở trong 1 cơn đói về dữ liệu, và dữ liệu sẽ được tập hợp từ nhiều nguồn khác nhau --> các phân phối sẽ khác nhau.   
Việc đào tạo mô hình ML phải lưu ý tập dev/ test phải đến từ 1 phân phối!!!!

## Lỗi bias hay lỗi variance?
Cho rằng: Lỗi bayer (lỗi không thể tránh khỏi, như tập ảnh mờ quá không thể nhìn ra) = Lỗi con người = 0
Ta có:   
Khoảng cách giữa lỗi tập train và lỗi bayer là lỗi bias.   
Khoảng cách giữa lỗi tập test và tập train là lỗi variance.  

## Công thức cơ bản cho ML:
<img src ='https://i.imgur.com/C3JvmxE.jpg'>

Khi đào tạo mô hình ML, bạn xem mô hình của mình có lỗi bias hay lỗi variance cao?
Ví dụ:  
Bạn có lỗi bias cao --> cần xem xét đào tạo mô hình lớn hơn, sâu hơn, lâu hơn, nhiều vòng lặp hơn hoặc chọn mô hình xây dựng NN đã phù hợp chưa?   
Bạn có lỗi variance cao ---> cần xem xét lấy thêm dữ liệu (do mô hình đào tạo tạo trên tập train không có tính tổng quát cao), hay bạn thử giám sát(điều chuẩn) regularization, hay chọn lại cấu trúc mô hình NN?

Câu hỏi đặt ra:    
**Nếu bạn có mô hình chỉ lỗi bias cao thì việc lấy thêm dữ liệu có ý nghĩa lớn hay ko?**   
Lấy thêm dữ liệu có ý nghĩa cho lỗi variance, trong trường hợp nay nên ưu tiên việc khác ngoài lấy thêm dữ liệu :))   
**Liệu có phải đánh đổi giữa lỗi bias và lỗi variace hay không? việc giảm lỗi bias thì có tăng lỗi variace và ngược lại?**  
Việc bạn có một mô hình với dữ liệu lớn, được regalarization tốt, được đào tạo một NN lớn phù hợp thì sẽ không phải đánh đổi giữa 2 lỗi này.  






