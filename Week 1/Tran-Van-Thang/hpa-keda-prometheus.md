Tóm tắt kiến thức quan trọng khi tìm hiểu HPA, KEDA, Prometheus

# HPA

- là một tính năng trong k8s giúp auto scale pod dựa vào các metrics và ngưỡng được định nghĩa
- hpa thực hiện loop (mặc định là 15s) để lấy metrics từ các deployments mà user muốn auto scale. Tóm gọn quy trình gồm có 3 bước lặp đi lặp lại: Query dữ liệu -> Tính toán so với giá trị mong muốn -> Điều chỉnh số pods
- hpa sử dụng `metrics registry` để lấy các metrics. Trong đó gồm 3 loại:
  - Resource Metrics API (Ở đây có thể lấy những thông số cơ bản như Ram, CPu,..)
  - Custom Metrics API (Các metrics custom lấy từ các nguồn khác)
  - External Metrics API

# Prometheus

- Prometheus là một lựa chọn được nhiều người tin dùng khi sử dụng `Custom Metrics API`
- Cấu trúc Prometheus gồm 3 phần chính:

  - Retrieval (có tác dụng collect metric từ nhiều nguồn)
  - Time Seri Database (lưu trữ metrics dưới dạng `thời gian: giá trị`)
  - HTTP Server (cung cấp api, query giúp bên ngoài có thể lấy được các metrics đã lưu trữ ở Database )

- Cách retrive lấy metrics:
  - Mặc định sẽ lấy được các thông số cơ bản như ram,cpu. network,..
  - Muốn lấy các metrics đặc biệt theo từng ứng dụng khác nhau thì phải thông qua một `exporter` (Ví dụ như `mongodb exporter` giúp lấy tổng số document đã lưu trữ)
  - Ngoài ra exporter còn hỗ trợ lấy metrics từ các services do developer viết ra với yêu cầu services đó có hỗ trợ `enpoint /metrics` chứa dữ liệu mong muốn để trigger và được xuất ra dưới một định dạng chuẩn. (Cái này yêu cầu developer có thêm kỹ năng lập trình, biết sử dụng  thư viện `prometheus` ngôn ngữ đang sử dụng và hiểu về metrics)

> Tóm lại, Prometheus giúp ta lấy được toàn bộ các metrics theo ý muốn từ đó có thể tích hợp với `hpa` để auto scaled với bất kì loại metrics nào.

# KEDA

- KEDA là một `lightweight component` được sử dụng cùng với k8s giúp mở rộng tính năng của k8s mà không tạo ra xung đột.

- KEDA giúp auto scaled app dựa vào events (nó như là một phiên bản nâng cấp của hpa). Nó có thể đưa số pod của một depployment về 0.

- KEDA sử dụng `ScaledObject` để định nghĩa các trigger giúp auto scaled ứng dụng theo ý của bạn

> Tóm lại, có thể sử dụng KEDA như là thành phần giao tiếp chính với k8s để auto scaled, KEDA sẽ sử dụng Prometheus là một `scaler` giúp KEDA lấy các metrics. Từ đó, KEDA giao tiếp với k8s để thực hiện scaled.

# Ví dụ

> Giả sử bạn muốn scaled web server dựa vào số lượng request trên một giây thì các công việc chính cần làm theo thứ tự sau:

- Web server bạn phải hỗ trợ endpoint /metrics
- Exporter lấy metrics từ webserver của bạn
- Prometheus lấy metrics từ exporter
- KEDA sử dụng HTTP Server của prometheus để query lấy metrics rồi ra quyết định scaled thông qua việc định nghĩa `ScaledObject`



# Câu hỏi càn giải đáp
- Có vẻ cần rất nhiều exporter?
- Tự định nghĩa enport /metrics thì có tạo ra tính phức tạp không ?
- KEDA hỗ trợ events trigger nó gồm những events gì? Tại sao không sự dụng thuần Prometheus?
- Tại sao ObjectScaled nó giúp tạo ra HPA?
