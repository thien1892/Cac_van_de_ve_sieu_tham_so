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
Khi chọn beta = 0.9000 đến beta = 0.9005 sẽ không có nhiều thay đổi, nhưng nếu beta = 0.999 đến 0.9995 thì sẽ ảnh hưởng lớn đến kết quả vì bạn đang thay đổi xem kết quả cuối cùng phụ thuộc vào 2000 giá trị trước thay vì 1000 giá trị trước đó.


