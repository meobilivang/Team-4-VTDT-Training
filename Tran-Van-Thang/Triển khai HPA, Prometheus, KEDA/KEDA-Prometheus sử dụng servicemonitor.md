# Triển khai KEDA, Prometheus sử dụng service monitor
> Đọc bài `KEDA-Prometheus sử dụng exporter` trước khi làm bài này.
> Bài này thực hiện tương tự như bài`KEDA-Prometheus sử dụng exporter` nhưng thay vì phải sử dụng exporter có sẵn thì ta sẽ tự viết service monitor để lấy metrics từ web server chúng ta tự code.

- Triển khai một web-server đã tích hợp sẵn enpoint /metrics ở trong code

```console
apiVersion: apps/v1
kind: Deployment
metadata:
  name: example-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: example-app
  template:
    metadata:
      labels:
        app: example-app
    spec:
      containers:
      - name: example-app
        image: fabxc/instrumented_app
        ports:
        - name: web
          containerPort: 8080
---
kind: Service
apiVersion: v1
metadata:
  name: example-app
  labels:
    app: example-app
spec:
  selector:
    app: example-app
  ports:
  - name: web
    port: 8080
```

- Sau đó tạo một service monitor như sau:

```console
apiVersion: monitoring.coreos.com/v1
kind: ServiceMonitor
metadata:
  name: example-app
  labels:
    release: prometheus
spec:
  selector:
    matchLabels:
      app: example-app
  endpoints:
  - port: web
```

> `release: prometheus` giúp prometheus nhận diện và lấy được metric, `app: example-app` sẽ match với service `example-app`.

Sau khi triển khai tất cả thành công, truy cập trang `http://localhost:9090/targets` ta sẽ thấy 1 endpoint mới tên là `example-app`

<img src="./img/example-target.PNG">

Query thử metrics là tổng số lượng request

<img src="./img/metric-http.PNG">


- Triển khai ScaledObject
  
> Tương tự như bài sử dụng exporter, ta chỉ cần thay đổi tên deployment và thay đổi câu query prometheus.
