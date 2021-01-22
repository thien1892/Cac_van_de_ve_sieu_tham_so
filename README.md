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
Không, ví dụ: Việc bạn có một mô hình với dữ liệu lớn, được regularization tốt, được đào tạo một NN lớn phù hợp thì sẽ không phải đánh đổi giữa 2 lỗi này.

# Regularization
   Có 2 cách regularization thường được sử dụng là L2 - Regularization và Dropout.   
## L2 Regularization
   Ta xem cụ thể L2- regularization là như thế nào?   
   <img src ='https://i.imgur.com/1AKqeKb.jpg'>   
   Ta thêm vào hàm mất mát 1 lượng lambd/(2 x m) x numpy.linalg.norm(W)        
   --> Việc thêm Frobenius norm của ma trận W này khi truyền ngược, việc cập nhật W sẽ giảm (lambd * anpha/ m)        
   --> việc suy giảm trọng số này --> hàm Z = Wx A +b gần 0 hơn   
   --> các hàm kích hoạt tuyến tính hơn (khi Z gần 0, các hàm sigmoi, tanh thường gần tuyến tính)   
   --> cho ta cảm giác mô hình bớt phức tạp hơn, và có vẻ sẽ gần tuyến tính hơn      
   --> giảm được sự quá khớp xảy ra.

## Dropout Regularization   
   <img src = 'https://i.imgur.com/oQRoz2D.jpg'>   
   Trực quan thì dropout là việc tắt ngẫu nhiêu một số nút ở một lớp bất kỳ --> việc tắt các nút làm giảm Frobenius norm của ma trận W, giống như L2, thay vì giảm theo 1 tỷ lệ cập nhật thì dropout tắt hẳn.   
   Ví dụ, ta tắt ngẫu nhiên 20% số nút ở lớp 3, ta làm như sau:   
   <img src ='https://i.imgur.com/FyMKRqu.jpg'>   
   Sau khi tắt một số nút, ta cập nhật lại a3 = a3 / 0.8 --> không ảnh hưởng tới việc tính toán về sau.    
   Lưu ý, với tập test ta không sử dụng lại dropout. Dropout không đưa lại cho ta cảm giác rõ ràng về hàm mất mát như L2. Dropout thường được sủ dụng nhiều trong thị giác máy tính.

## Một số cách Regularization khác.  
1. Dừng sớm   
<img src ='https://i.imgur.com/h1tgcGT.jpg'>   
Ưu điểm: lửa chọn nhanh để tránh quá khớp.   
Nhược điểm: Việc dừng sớm làm 1 lúc 2 công việc (tối ưu hóa hàm mất mát, tránh quá khớp) --> những việc ta làm để tối ưu hóa ko được triệt để (vd: ta ko thể chọn hàm mất mát nhỏ nhất mà thuật toán của ta đang thực hiện)   
    
2. Tăng cường dữ liệu:   
Ví dụ bạn đang đào tạo thuật toán nhận dạng mèo, nhưng ít dữ liệu có thể thêm dữ liệu bằng cách: xoay ảnh, cắt ảnh,.... --> để tăng dữ liệu 1 cách ít tốn chi phí.

# Chuẩn hóa đầu vào:
1. Trực quan:  
<img src = 'https://i.imgur.com/LD9rpOJ.jpg'>
   Sau khi chuẩn hóa đầu vào x = (x - mu) / sigma ta đưa đầu vào về phương sai = 1. Lưu ý tập dev và test có cùng mu, sigma.   

2. Tai sao chuẩn hóa đầu vào làm cho việc tối ưu hóa hàm mất mát J nhanh hơn?   
<img src = 'https://i.imgur.com/ltrDEs5.jpg'>   
Chúng ta xem hình ảnh trực quan sau khi chuẩn hóa --> các bước gradient sẽ nhanh hơn khi ở các vòng tròn đồng tâm --> việc tính toán sẽ nhanh hơn khi chưa chuẩn hóa.

# Khởi tạo tham số   
1. Sự bùng nổ và biến mất của gradient   
Ví dụ với một NN đơn giản:   
<img src ='https://i.imgur.com/BdVgbtR.jpg'>   
x1, x2 = 1 khi đó ở lớp L, a[l] = 0.5 ^L --> với các mạng càng sâu việc biến mất hay bùng nổ của gradient sẽ xảy ra khi W >I hoắc W< I.   
Để tránh bùng nổ hay biến mất gradient, ta có thể chọn cách khởi tạo tham số để hạn chế việc bùng nổ hay biến mất của gradient.       

2. Khởi tạo tham số:       
<img src ='https://i.imgur.com/jD1sABs.jpg'>   
Để z không bùng nổ hay biến mất, thì với n ( số nút ẩn) càng lớn, ta muốn w càng nhỏ --> ta chọn w có var = 2/n, và khơi tạo:   

+ w = np.random.randn(shape).np.sqrt(2/n[l-1]), với hàm relu
            
+ w = np.random.randn(shape).np.sqrt(1/n[l-1]) hoặc w = np.random.randn(shape).np.sqrt(2/(n[l-1] X n[l])), với hàm tanh.

# Kiểm tra gradient:
<img src ='https://i.imgur.com/EFINDgY.jpg'>   
Ý tưởng bắt đầu từ d(theta) = (J(theta +epsilon) - J(theta - epsilon)) / (2 x epsilon)
--> việc kiểm tra gradient được thực hiện theo công thức trên ảnh.   
Lưu ý:     

+ Grard checking chỉ nên kiểm tra ở thời điểm gỡ lỗi, không nên kiểm tra trong lúc train.  

+ Nếu thấy lỗi grard check nên kiểm tra từng thành phần và xác định lỗi (theta bao gồm w, b --> kiểm tra db, dw có lỗi ko?)    

+ Nếu có L2 hãy chắc J() được tính chính xác khi có L2    

+ Không thực hiện với Dropout    

+ Hãy thực khởi tạo lại tham số xấp xỉ 0 và làm lại.  


















