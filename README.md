#Intrusion alert via call and text message 
1. Định hướng giải pháp

-Thiết kế, lập trình một WebServer cho Modul Wifi Node MCU ESP8266 có một số chức năng đơn giản như thiết lập wifi, số điện thoại gọi đến, nội dung tin nhắn sử dụng HTML, CSS đơn giản. 

-Lắp ráp mô hình, mạch điện bằng các linh kiện điện tử dễ tìm kiếm và phổ biến.

-Giúp phần cải thiện khả năng giao tiếp với phần cứng cũng như có thêm kiến thức về lập trình cho một số loại vi điều khiển. Khả năng tìm kiếm và tổng hợp thông tin về các giao thức được sử dụng trong IoT, và áp dụng nó vào mô hình trên.

2. Tổng quan chức năng

-	Chức năng bật hoặc tắc chế độ cảnh báo.

-	Thiết lập wifi

•	Thiết lập được tên và mật khẩu của wifi do ESP8266 ở chế độ access point phát ra

•	Wifi được thiết lập ở chế ẩn hoặc hiển thị. Khi wifi ở chế độ ẩn sẽ có độ bảo mật cao hơn vì khi đó muốn kết nối được đến webserver thì sẽ phải kết nối vào mạng do ESP8266 phát ra trước nên sẽ không dễ dàng vào được webserver để thay đổi cấu hình khi mà không biết tên và mật khẩu của wifi.

-	Thiết lập cho Module SIM 900A

  •	Thiết lập số điện thoại và nội dung tin nhắn khi có đột nhập thì module SIM 900A sẽ gọi về hoặc gửi tin nhắn về cho số điện thoại mà ta đã cấu hình.
  
  •	Có chức năng testcall, khi thực hiện nó sẽ gọi về cho số điện thoại mà ta đã cấu hình (không quan trọng có đột nhập).

-	Sử dụng điên thoại đã được cấu hình 

  •	Gọi điện thoại hoặc gửi tin nhắn “OFF CB” đến Module SIM 900A để tắt cảnh báo.
  
  •	Gửi Tin nhắn “ON CB0” và “ON CB1” để bật chế độ cảnh báo Call Module hoặc Send SMS 
