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
1. Hãy lấy mẫu ngẫu nhiên, không thử nghiệm theo mô hình lưới.   

Ví dụ: Bạn cần thử 2 siêu tham số anpha và epsilon:    
<img src ='https://i.imgur.com/4NlUe4w.jpg'>   
Ở TH1 Bạn thử 2 siêu tham số theo mô hình lưới --> khi đó bạn chỉ thử được 5 mẫu của anpha, trong khi đó ở TH2, với việc lấy mẫu ngẫu nhiên, bạn sẽ thử được 25 giá trị của anpha.   

2. Hãy sử dụng thang đo thích hợp
