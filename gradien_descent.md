# Làm thế nào để tăng tốc độ tính toán gradient descent?  
- Mini- batch gradient
- ADAM (kết hợp gradient descent with momentum và RMSprop)
# Cách giảm suy giảm tỷ lệ học tập?  

# Mini-batch gradient  
- Là cách chia tập train thành các nhóm nhỏ gồm 64 (2^6), 128 (2^7), 256 (2^8), 512 (2^9 hoặc 1024 (2^10) mẫu.
- Đối với mỗi vòng lặp qua các nhóm nhỏ, cập nhật tham số qua từng lần lặp lại. Mỗi lần lặp lại qua tập train được gọi là 1 epoch.
- Ta xem 1 vòng lặp qua từng mini-batch làm những gì?  
<img src = "https://i.imgur.com/N5p3fD7.jpg">   
- Qua từng lần lặp, hàm mất mát J có xu hường giảm dần như sau:  
<img src ="https://i.imgur.com/49zsQ2J.jpg">  

# ADAM (Adaptive moment estimation)
- Trực quan của ADAM là kết hợp cùng lúc 2 cách tăng tốc độ tính toán gradient descent của trung bình động (tăng tốc chiều ngang) và RMSprop (tăng tốc chiều ngang và chiều dọc). Cụ thể như sau:  
<img src ='https://i.imgur.com/obSHDkJ.jpg'>