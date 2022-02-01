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

3. Cách thức hoạt động

-	Sơ đồ hoạt động của từng phần:

![image](https://user-images.githubusercontent.com/59023235/151993601-a58b6d84-42da-4280-8995-60d0636b18c5.png)
                                     
Hình 1: Sơ đồ hoạt động của từng phần:

-	Webserver thiết lập wifi, số điện thoại và nội dung tin nhắn, chế độ hoạt động modul sim, chế độ bật tắt cảnh báo,…

![image](https://user-images.githubusercontent.com/59023235/151993646-2f95bcda-5d63-416c-92d6-59cd8f9e198b.png)

                                    
Hình 2: Thiết lập Webserver

-	Gửi tin nhắn cho Modul Sim 900A để tắt hoặc bật cảnh báo:

![image](https://user-images.githubusercontent.com/59023235/151993671-86f6112e-9c4d-4179-93f8-c38f068970f8.png)

                                      
Hình 3: Gửi tin nhắn modul sim

-	Chương trình cảnh báo khi có đột nhâp:

![image](https://user-images.githubusercontent.com/59023235/151993739-17722901-83b6-4c92-b66a-59d0686f5733.png)

  
Hình 4: Chương trình cảnh báo

4. Sơ đồ tổng quan hệ thống

![image](https://user-images.githubusercontent.com/59023235/151993826-761349fb-9f3a-42e6-b5a4-024d4d4718ca.png)

-	Đầu tiên vi xử lý ESP8266 phát ra một mạng có tên và mật khẩu wifi do ta cấu hình từ trước.

-	Sau đó ta dùng mội thiết bị khác kết nối vào mạng và vào webserver với địa chỉ ip là 192.168.1.1 đề cấu hình lại wifi nếu muốn sau đó cấu hình tiếp số điện thoại, nội dung tin nhắn để khi phát hiện đột nhập thì Module Sim 900A sẽ gọi báo động về cho số điện thoại cài đặt.

-	Khi đã cấu hình xong thì mọi dữ liệu sẽ được lưu trữ vào bộ nhớ EEPROM, nếu có đột nhập thì sẽ gọi điện cho chúng ta mà chúng ta muốn tắt chế độ cảnh báo mà không muốn vào webserver nữa thì ta có thể gọi lại cho số của Module Sim 900A hoặc gửi tin nhắn với cú pháp “OFF CB”.

5. Công nghệ

a. Phần cứng 

- ESP8266 V3 CH340 NODEMCU LUA WIFI

- Modul Sim 900A

- Cảm biến ánh sáng

- Đầu phát laser

- Nguồn Power Adaptor AC-DC 5V 2A

b. Modul sim 900A

-	Hàm cấu hình cho Module Sim 900A sau đó lưu những thông tin đã có vào bộ nhớ EEPROM

![image](https://user-images.githubusercontent.com/59023235/152003196-87d7b0fc-a56b-422c-81e5-baae6f3f7127.png)

-	Hàm dùng để setup cho Module Sim 900A

![image](https://user-images.githubusercontent.com/59023235/152003620-781934e7-bc41-401c-8780-6456a08e9820.png)

-	Hàm dùng để Module gọi về số điện thoại 

![image](https://user-images.githubusercontent.com/59023235/152003714-861f3cb1-a6e4-4a4f-9232-95196c2b0d4f.png)

-	Hàm dùng để Module Sim 900A thực hiện tin nhắn đến số điện thoại

![image](https://user-images.githubusercontent.com/59023235/152003836-077ffe21-ecb4-4b3b-afad-9fd90b5441d1.png)

c. Hướng dẫn sử dụng ESP8266

  Trong project này thì ESP8266 vừa là 1 điểm Access Point vừa là 1 Webserver có địa chỉ ip là 192.168.1.1.

c.1 Sử dụng ESP8266 là 1 điểm Access Point

![image](https://user-images.githubusercontent.com/59023235/151996242-21175e8f-a541-4c61-b6a0-ef1cb17826a1.png)

![image](https://user-images.githubusercontent.com/59023235/151996251-a3fe7b01-4854-470e-a6a4-19e544494b7f.png)

c.2 Sử dụng ESP8266 là Webserver

![image](https://user-images.githubusercontent.com/59023235/151996371-efac3d01-6d8f-4bfa-a20f-1e7c824019b6.png)
d. ESP8266 làm WebSocket Server

- Khai báo các thư viện cần thiết:

![image](https://user-images.githubusercontent.com/59023235/152004497-fa255fd2-be3e-461a-a502-54d69f8eedc1.png)

- Để sử dụng thư viện WebSocketsServer ta cần khởi tạo một đối tượng tên là là webSocket chạy trên port 81.

WebSocketsServer webSocket = WebSocketsServer(81);

-	Khai báo hàm dùng để khởi tạo và xử lý các sự kiện của WebSocket 

![image](https://user-images.githubusercontent.com/59023235/152005141-dbf5e86f-7090-405d-92a3-716d7e344bbd.png)

- Cuối cùng chúng ta cần gọi phương thức webSocket.loop() trong vòng lặp chính để kiểm tra khi có sự kiện WebSocket xảy ra.

![image](https://user-images.githubusercontent.com/59023235/152005226-2543a9e5-bd63-41b1-b057-98fd6274d752.png)


e . Bộ nhớ EEPROM trong ESP8266

![image](https://user-images.githubusercontent.com/59023235/151996932-ac81efa5-62a1-4452-a2e3-da23ea63f9f2.png)

Đầu tiên ta sẽ dùng câu lệnh EEPROM.begin(size); để khởi tạo vùng nhớ trong EEPROM tiếp đó ta sẽ dùng câu lệnh EEPROM.write(); để ghi dữ liệu vào và dùng câu lệnh EEPROM.commit(); để hoàn tất việc ghi dữ liệu cuối cùng để đọc bộ nhớ EEPROM ra thì ta chỉ cần câu lệnh EEPROM.read()

6. Kết quả

-	Mạch của hệ thống được lắp như sau: 

![image](https://user-images.githubusercontent.com/59023235/151997272-7fe46218-be95-4f0e-92a3-fa6151abf907.png)

-	Giao diện của Webserver: 

![image](https://user-images.githubusercontent.com/59023235/151997311-9ec42f8c-b42c-4485-bb71-92b9441b9d36.png)

![image](https://user-images.githubusercontent.com/59023235/151997334-03949cc0-7631-4b78-9aa5-7733b2b250d2.png)

![image](https://user-images.githubusercontent.com/59023235/151997360-3610fd8c-7bbb-459b-9a35-a3baa682c008.png)

-	Tài liệu về ESP8266

esp8266-technical_reference_en.pdf (espressif.com)
https://getblocky.com/courses/p2-ket-noi-internet/lessons/che-do-wifi-access-point/

-	Tài liệu về Module Sim900A

https://mlab.vn/index.php?_route_=huong-dan-su-dung-module-sim900.html
-	Tài liệu về Websocket

https://getblocky.com/courses/p2-ket-noi-internet/lessons/websocket-la-gi/


