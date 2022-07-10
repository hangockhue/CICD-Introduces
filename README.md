# CICD-Introduces
CI/CD là một bộ đôi công việc, bao gồm
- CI là viết tắt của Continuous Integration
- CD là viết tắt của Continuous Delivery/Continuous Deployment
là quá trình tích hợp (integration) thường xuyên, nhanh chóng hơn khi code cũng như thường xuyên cập nhật phiên bản mới (delivery).

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
