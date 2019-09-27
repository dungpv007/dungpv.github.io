---
title: Java Performance
subtitle: An Approach to Performance testing
tag: java
---

Phần này sẽ nói về 4 nguyên tắc chính trong performance testing.

# Test a Real Application


## Microbenchmarks
Microbenchmark như tên của nó là việc test hướng đến những đơn vị nhỏ trong code như thời gian chạy một function giữa sync và async, overhead khi khởi tạo thread mỗi khi cần hay dùng threadpool, giữa việc chạy thuật toán này với thuật toán khác...

Microbenchmark là một cách tốt để test hiệu năng của hệ thống, nó test từng phần, từng chức năng nhỏ nhất của hệ thống nên sẽ dễ tìm ra được chỗ đang gây ảnh hưởng đến hệ thống và cần tối ưu. Tuy nhiên microbenchmark cũng khó để viết chính xác, đúng yêu cầu.
Sau đây là một số lưu ý khi viết microbenchmark:
* Microbenchmarks must use their result: 
	Đối với java, jvm và compile ngày càng được tối ưu để cho ưng dụng chạy một cách hiệu quả. Vì thế nên những gì thực sự chạy ở JVM không hẳn là những gì được viết trong code. Ví dụ việc không sử dụng kết quả trả về từ 1 method đang được test, JVM sẽ tự hiểu rằng đoạn code đó không cần thiết và bỏ qua không thực hiện dẫn đến kết quả test bị sai lệch. Vì vậy cần đảm bảo được rằng đoạn code cần test sẽ thực sự được chạy khi test.
* Microbenchmarks must not include extraneous operations:
	Vì đây là microbenchmark, chỉ tập trung vào test những phần nhỏ trong ứng dụng nên việc sử dụng những thứ không liên quan đến phần cần test sẽ gây sai lệch kết quả test.
* Microbenchmarks must measure the correct input
* Warm-up period before test


## Macrobenchmarks

Macrobenchmarks là thực hiện test cả một ứng dụng hoàn chỉnh như khi chạy production.


## Mesobenchmarks



# Understand Throughput, Batching and response time

