# Các siêu tham số:
1. Learning rate anpha
2. Beta (khi sử dụng trung bình động gradient descent)
3. mini-batch size
4. Hidden units ?
5. Layer?
6. Learning rate decay
7. ADAM: beta1 = 0.9, beta2 = 0.999, epsilon = 10^-8  
**Việc ưu tiên điều chỉnh siêu tham số theo thứ tự 1 --> (2,3,4) --> (5,6). Và ít khi điều chỉnh các siêu tham số khi sử dụng ADAM**

# Cách thử nghiệm các siêu tham số:  
1. **Hãy lấy mẫu ngẫu nhiên, không thử nghiệm theo mô hình lưới.**   

Ví dụ: Bạn cần thử 2 siêu tham số anpha và epsilon:    
<img src ='https://i.imgur.com/4NlUe4w.jpg'>   
Ở TH1 Bạn thử 2 siêu tham số theo mô hình lưới --> khi đó bạn chỉ thử được 5 mẫu của anpha, trong khi đó ở TH2, với việc lấy mẫu ngẫu nhiên, bạn sẽ thử được 25 giá trị của anpha.   

2. **Đi từ thô đến tinh**   
<img src ='https://i.imgur.com/T0ULWV4.jpg'>   
Khi bạn thử nghiệm các siêu tham số hãy khoanh vùng giá trị cho kết quả tốt và tiếp tục thử nghiệm để khoanh vùng cho kết quả tốt để lựa chọn siêu tham số. Ví dụ ta đã đi từ vùng lớn đến vùng nhỏ hơn trên ảnh.  

3. **Hãy sử dụng thang đo thích hợp**   
**VD1:** Với số Layer bạn có thể chọn 2,3,4,... nhưng ví dụ với anpha thì sao? Nếu bạn cho rằng anpha sẽ nằm trong khoảng 0.0001 đến 1? Nếu bạn chọn ngẫu nhiên, sẽ rao sao nếu anpha chỉ tập trung vào khoảng 0.1 đến 1? Hãy xem cách chọn thang đo cho anpha:  
<img src ='https://i.imgur.com/SMLbGgC.jpg'>  
Ở ví dụ trên, ta thực hiện 2 bước: chọn r ngẫu nhiên thuộc (-4, 0), sau đó chọn anpha = 10^ r. Việc lựa chọn như vậy khiến anpha trải đều hơn và tránh việc tập trung vào 1 khoảng không mong muốn.   

**VD2:** Ta hãy xem cách chọn beta (khi sử dụng trung bình động gradient descent):   
<img src= 'https://i.imgur.com/d9HrOJ4.jpg'>   
Khi chọn beta = 0.9000 đến beta = 0.9005 sẽ không có nhiều thay đổi, nhưng nếu beta = 0.999 đến 0.9995 thì sẽ ảnh hưởng lớn đến kết quả; vì bạn đang thay đổi xem kết quả cuối cùng phụ thuộc vào 2000 giá trị trước thay vì 1000 giá trị trước đó.   

4. **Hãy định kỳ kiểm tra lại các siêu tham số**   
Việc lựa chọn được các siêu tham số rất tốn thời gian, nhưng đừng vội hài lòng với mô hình của bạn, bởi vì khi dữ liệu đầu vào cho mô hình của bạn thay đổi hàng ngày --> các siêu tham số sẽ trở nên cũ kỹ và có thể không phù hợp --> do đó hãy định kỳ đánh giá lại mô hình cũng như các siêu tham số đã lựa chọn để xem xét chúng có phù hợp nữa hay không!!    
5. **Hai cách phát triển mô hình: Panda và Caviar**
<img src = 'https://i.imgur.com/5zcR797.jpg'>   

**Panda:** Khi bạn không có nhiều tài nguyên CPU, GPU để xử lý, bạn trông nom mô hình hàng ngày, thay đổi để xem hàm mất mát giảm dần. Giống như Gấu trúc không có nhiều con, chúng trông nom con hàng ngày :))   
**Caviar** Khi bạn thuộc dạng rick kid, thử một lúc nhiều mô hình và sau đó chọn mô hình phù hợp nhất, giống như cá hồi để hàng loạt trứng và sau đó một số trứng nở ra con.  

# Batch Norm
1. **Nhắc lại về chuẩn hóa dữ liệu đầu vào:**
<img src ='https://i.imgur.com/xXV34ge.jpg'>   

- Chuẩn hóa dữ liệu đầu vào làm tăng quá trình học tập của mô hình. Câu hỏi đặt ra là: với các lớp ẩn, việc chuẩn hóa sẽ ra sao?  

- Ví dụ chuẩn hóa a[2] có thúc đẩy nhanh quá trình tính toán w[3], b[3]? Và thường thì ta lựa chọn chuẩn hóa z[2] thay vì a[2]. Nếu có thể chuẩn hóa được thì việc chuẩn hóa đó như thế nào?
2. **Cách Batch Norm thực hiện ở 1 layer cụ thể**
<img src ='https://i.imgur.com/680lu9y.jpg'>  
Từ z[l](i) ta xây dựng z-norm[l](i) như trên.   
Ta tính: z~[l](i) từ z-norm thông qua 2 tham số gamma và beta. Việc thêm 2 tham số này sẽ khiến cho z~ không gần 0 và hàm g(z) sẽ không gần tuyến tính như z-norm (đương nhiên là ta không muốn các lớp ẩn tuyến tính). z~ sẽ được sử dụng thay cho z khi thực hiện các tính toán về sau.

3. **Batch Norm trong mô hình Neural Network**
<img src ='https://i.imgur.com/Q4vBCXV.jpg'>  

Ta dùng a[l-1] để tính z[l]; dùng z[l] để tính z~[l]; dùng z~[l] để tính a[l+1],....
--> có các tham số: w, gamma, beta (xem cách xây dựng z-norm ta thấy b sẽ bị loại bỏ khi tính trung bình, nên tham số b thực sự không cần thiết trong mô hình).



