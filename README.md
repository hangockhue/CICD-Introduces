# CICD-Introduces
### CI/CD là một bộ đôi công việc, bao gồm
- CI là viết tắt của Continuous Integration
    - Nó là phương pháp phát triển phần mềm yêu cầu các thành viên của team tích hợp công việc của họ thường xuyên, mỗi ngày ít nhất một lần. Mỗi tích hợp được "build" tự động (bao gồm cả test) nhằm phát hiện lỗi nhanh nhất có thể. 
    ![Alt text](images/ci.webp?raw=true "Title")

- CD là viết tắt của Continuous Delivery/Continuous Deployment
    - triển khai tất cả thay đổi về code (đã được build và test) đến môi trường testing hoặc staging. Continuous Delivery cho phép developer tự động hóa phần testing bên cạnh việc sử dụng unit test, kiểm tra phần mềm qua nhiều thước đo trước khi triển khai cho khách hàng (production). 
    ![Alt text](images/cd.webp?raw=true "Title")

### Vì sao phải sử dụn CI/CD:
- Tính năng mà mất 2, 3 tháng mới release thì dẫn đến mất đi cái lợi thế dẫn đầu. Do đó, việc làm ra một sản phẩm, tính năng đòi hỏi thần tốc là ưu tiên số một hiện nay.
- Bên cạnh đó, để nhanh chóng ra mắt một tính năng, phiên bản mới nếu theo cách cổ điển sẽ mất nhiều thời gian bởi công việc chân tay khá nhiều và mỗi lần release cũng huy động một cơ số người không nhỏ để cập nhật một thay đổi dù là nhỏ nhất. Bởi vậy, xu hướng CI/CD giúp cung cấp các framework, workflow giúp tiết kiệm thời gian, nguồn lực của quá trình release (delivery).

### Dưới đây là các bước thông thường của quá trình release tính năng trong một dự án.
- Bước 1: [Manual] Khởi tạo repository và có branch default là master và dev.
- Bước 2: [Manual] Trừ owner ra, thì các coder sẽ push code tính năng lên branch dev
- Bước 3: [Auto] Hệ thống tự động thực hiện test source code, nếu PASS thì sẽ deploy tự động (rsync) code lên server beta.
- Bước 4: [Manual] Tester/QA sẽ vào hệ thống beta để làm UAT (User Acceptance Testing) và confirm là mọi thứ OK.
- Bước 5: [Manual] Coder hoặc owner sẽ vào tạo Merge Request, và merge từ branch dev sang branch master.
- Bước 6: [Manual] Owner sẽ accept merge request.
- Bước 7: [Auto] Hệ thống sẽ tự động thực hiện test source code, nếu PASS sẽ enable tính năng cho phép deploy lên production server.
- Bước 8: [Manual] Owner review là merge request OK, test OK. Tiến hành nhấn nút để deploy các thay đổi lên môi trường production.
- Bước 9: [Manual] Tester/QA sẽ vào hệ thống production để làm UAT và confirm mọi thứ OK. Nếu không OK, Owner có thể nhấn nút Deploy phiên bản master trước đó để rollback hệ thống về trạng thái stable trước đó.
- Bước 10: [Manual] Chờ email trả lời của khách hàng.

### Devops là gì
- là một văn hóa làm việc kết hợp giữa kỹ sư phát triển phần mềm (dev) với bộ phận operator (kỹ sư hệ thống, nhân viên bảo mật, kỹ sư mạng, kỹ sư hạ tầng,...) nhằm mục đích rút ngắn vòng đời phát triển sản phẩm (SDLC).
- Trước kia quy trình phát triển phần mềm không hề có sự phân tách rạch ròi giữa hai giai đoạn phát triển (development) và vận hành (operations), nhất là đối với các sản phẩm vừa và nhỏ. Vì là người phát triển sản phẩm, Developer sẽ hiểu rõ về sản phẩm để chọn cách vận hành phù hợp nhất nên anh ta sẽ đảm nhiệm việc develop, đồng thời cũng kiêm luôn việc test, deploy sản phẩm.
    - Giai đoạn phát triển (development) bao gồm phần việc của UI designer, developer, QA/QC…
    - Giai đoạn vận hành (operations) có sự tham gia của system engineer, system administrator, operation executive, release engineer, DBA, network engineer,…
- Sau đó, sự bùng nổ về quy mô của các công ty và sản phẩm công nghệ diễn ra: Từ đó, kéo theo quy mô hệ thống phình ra theo cấp số nhân. Từ một vài server, hệ thống có thể phát triển lên đến hàng chục, hàng trăm, hàng nghìn, hoặc thậm chí hàng triệu server.
Yêu cầu chuyên môn hóa trở nên gắt gao, khiến quy trình phát triển phần mềm chia tách thành những giai đoạn riêng biệt. Đây là giai đoạn mà Dev và Ops tách bạch.
- Ngoài ra, ngành phát triển phần mềm cũng dịch chuyển theo một hướng khác – microservices.

    ``` Microservices: Một sản phẩm lớn được chia tách làm rất nhiều service nhỏ, các service này liên kết với nhau tạo thành một sản phẩm hoàn chỉnh.```
- Những lợi ích chính của DevOps là:
    - Tăng cường sự cộng tác chặt chẽ giữa nhóm phát triển (development) và nhóm vận hành (operation), cũng như khả năng làm việc liên chức năng (cross-functional).
    - Nâng cao tần suất triển khai (deployment), giúp rút ngắn thời gian phát triển/cải tiến sản phẩm.
    - Tận dụng các công cụ tự động hóa, giúp hạn chế rủi ro, giảm tỉ lệ thất bại.
    - Thời gian phục hồi sản phẩm nhanh hơn.
