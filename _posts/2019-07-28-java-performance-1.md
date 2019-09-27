---
title: Java Performance
subtitle: Intro
tag: java
---

Seri này mình sẽ viết về việc làm sao để turning performance cho các project sử dụng Java. Tuy nhiên, nó cũng có thể được áp dụng đối với các ngôn ngữ khác.
Trước khi đi sâu vào việc turning riêng với các ứng dụng Java, sau đây là một số nguyên tắc để dạt được performance cho ứng dụng, không riêng gì Java.
Nội dung trong series này mình follow theo cuốn **Java Performance: The Definitive Guide**


* Write better algorithms
	Việc viết thuật toán tốt và tối ưu hơn tất nhiên sẽ mang lại hiệu năng tốt hơn cho chương trình. Hai chương trình có độ phức tạp O(n) và O(log(n)) sẽ mang lại 
	hiệu năng và tốc độ khác nhau khá nhiều khi n lớn.

* Write less code
	Đúng vậy, việc viết ít code hơn không những mang lại tốc độ compile và tốc độ chạy tốt hơn mà nó còn có thể it bug hơn.

* Prematurely optimize
	Việc optimize một cách vội vã mà chưa hiểu rõ vấn đề có thể sẽ làm mọi thứ tệ đi. Nó không chắc là có thể làm chương trình chạy nhanh hơn nhưng có thể làm chương trình phải gặp nhiều vấn đề hơn như tăng độ phức tạp, thêm bug, hoặc kể cả làm chương trình chậm đi. Đó là vì bạn có thể đã tối ưu sai chỗ, hoặc là tối ưu một cái mà hiệu quả nó mang lại là quá ít so với những gì đạt được. Vì vậy, chỉ tối ưu sau khi bạn đã hiểu rõ vấn đề( sau khi profiling và tìm được chỗ gây vấn đề hoặc có bằng chứng cụ thể về vấn đề gặp phải) và chắc rằng hiệu quả nó mang lại là xứng đáng. 


* External service
	Nếu ứng dụng của bạn có sử dụng những service ngoài như database, gọi qua service khác qua network... thì hiệu năng của ứng dụng sẽ phụ thuộc vào cả hiệu năng của các service này. Vì vậy việc tối ưu riêng cho ứng dụng của bạn là chưa đủ mà cần ở cả các service khác.
	Ví dụ ứng dụng của bạn có sử dụng database, đến 1 ngày lượng dữ liệu, lượng user quá lớn làm database trở thành bottleneck của hệ thống. Lúc này nếu bạn tối ưu bên ứng dụng của bạn làm nó chạy nhanh vào handle được nhiều request hơn nhưng database vẫn là bottleneck thì việc có nhiều request hơn chỉ làm hiệu năng của hệ thống đi xuống.

* Optimize for the common case
	Khi gặp vấn đề về performance của hệ thống, bạn có thể áp dụng một số case sau:
	** Profiling ứng dụng của bạn để tìm được bottleneck và tập trung tối ưu phần này trước
	** Sử dụng thuật toán đơn giản cho những thứ chung trong ứng dụng
	