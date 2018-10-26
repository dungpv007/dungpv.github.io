---
layout: post
title: Testing trong Java với JUnit và Mockito
---

Làm dev cũng được một thời gian, trải qua cũng kha khá dự án thì mình cũng đã gặp nhiều khó khăn cũng như bug, sự cố khi chạy production. 
Và sau cùng mình nhận thấy việc test của mình chưa đủ tốt. Vì vậy mình sẽ tập trung học và luyện thêm việc viết test, 
cả unit test, intergration test ... Trong quá trình đấy mình sẽ viết thành các bài trên trang github này để tiện cho việc học và xem lại sau này nếu cần. Vì mình thường làm về Java là chính nên sẽ sự dụng 2 thư viện là JUnit và Mockito để viết test.

##Phân loại Test

Có nhiều kiểu phân loại test với các tên gọi, định nghĩa khác nhau. Tuy nhiên có thể chia thành 3 loại chính.
	* Unit Tests  
	Như tên gọi, unit test chỉ tập trung vào 1 class hoặc chức năng trong code của bạn và đảm bảo để nó chạy đúng. Vì vậy các unit test thường nhỏ gọn, chạy nhanh, chỉ tập trung vào logic cần test mà không biết đến những thứ xung quanh (các module, dịch vụ ngoài hay tài nguyên khác). 
	* Integration Tests. 
	Integration test hay test tích hợp là khi module của bạn có sử dụng các module khác hay tài nguyên bên ngoài. Ví dụ module của bạn cần gọi đến DB để lấy dữ liệu hoặc bạn làm module Order và cần gọi đến module Product để lấy thông tin của product... 
	* End-to-end Tests
	Với end-to-end test, hệ thống sẽ được test dưới góc độ của một user thực, từ giao diện front-end đến hệ thống back-end phía sau. 

Loạt bài này sẽ chỉ tập trung vào unit test vì nó có thể xem là nền tảng cơ bản và cần có của mỗi developer.

##Các kiểu tiếp cận test

Trước khi tìm hiểu và học thêm về test, mình nghĩ test đơn giản chỉ là viết các đoạn code để kiểm tra xem code của mình có chạy đúng mong đợi hay không. Sau khi code chán chê, gần xong project thì mình bắt đầu viết test một số chức năng mà mình nghĩ cần test, pass hết là xong. Mình nghĩ khá nhiều dev cũng sẽ có hướng tiếp cận tương tự. Nhưng sau khi tham khảo một số tài liệu, mình thấy thế giới thường có 2 loại người:  
	* Viết test chỉ để đảm bảo code chạy đúng. Đó là như trường hợp của mình, làm xong xuôi các thứ rồi mới viết test, sai thì sửa code khi nào được thì thôi. Và nhìn lại thì việc này gây khá nhiều khó khăn cho việc test. Khi đã code xong xuôi, mình muốn test một chức năng nhưng giờ nó đã khá rắc rối, liên quan đến các module khác... Khi đấy mình phải dùng các trick như sửa tạm code, giá lập đoạn gọi ra module ngoài và đấy là lúc làm cho code rối thêm. Và cuối cùng cả code và test đều là một mớ hỗn độn.
	* Test chính là thước đo chất lượng code. Test cần đúng chuẩn, dễ viết. Nếu gặp khó khăn khi viết test thì do code không tốt và cần sửa lại. Các dòng code viết ra đều có thể test được và tránh sử dụng các trick để thay đổi code cho việc test. Loại này giống với TDD(Test Driven Development), một phương pháp phát triển phần mềm xoay quanh việc viết test và refactor code để đảm bảo pass được test.

Việc phân chia ở trên cũng chỉ là tương đối, không phải ai cũng thuộc loại này hay loại kia mà thường sẽ ở giữa, chỉ là nghiêng về cái nào hơn thôi. Tất nhiên mình sẽ hướng đến việc trở thành loại người thứ 2, viết test một cách đúng đắn để đảm bảo code dễ bảo trì, nâng cấp, maintain.




