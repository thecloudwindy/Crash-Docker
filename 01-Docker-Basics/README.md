
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [1. Lệnh kiểm tra phiên bản Docker](#1-lệnh-kiểm-tra-phiên-bản-docker)
- [2. Lệnh kiểm tra thông tin chi tiết về Docker đã cài đặt](#2-lệnh-kiểm-tra-thông-tin-chi-tiết-về-docker-đã-cài-đặt)
- [3. Cú pháp câu lệnh Docker](#3-cú-pháp-câu-lệnh-docker)
- [4. Ví dụ tạo một Nginx Container](#4-ví-dụ-tạo-một-nginx-container)
- [5. Lệnh Stop một hay nhiều Container đang chạy](#5-lệnh-stop-một-hay-nhiều-container-đang-chạy)
- [6. Lệnh Start một hay nhiều Container đã Stop](#6-lệnh-start-một-hay-nhiều-container-đã-stop)
- [7. Lệnh Remove một hay nhiều Container](#7-lệnh-remove-một-hay-nhiều-container)
- [8. Lệnh hiển thị Logs của Container](#8-lệnh-hiển-thị-logs-của-container)
- [9. Lệnh hiển thị các tiến trình đang chạy trong Container](#9-lệnh-hiển-thị-các-tiến-trình-đang-chạy-trong-container)

<!-- /code_chunk_output -->


## 1. Lệnh kiểm tra phiên bản Docker
- `docker version` hoặc `docker -v`

## 2. Lệnh kiểm tra thông tin chi tiết về Docker đã cài đặt
- `docker info`

## 3. Cú pháp câu lệnh Docker

- `docker [management commands] [commands] [options]`
>
- Ví dụ:
`docker image ls -a` : hiển thị tất cả các images hiện có.
`docker container ls` : hiển thị tất cả các container hiện đang chạy.
`docker container ls -s` : hiển thị tất cả các container hiện có kể cả các containers đã *exited*

## 4. Ví dụ tạo một Nginx Container
- `docker container run -d -p 80:80 --name nginx-server nginx:latest`
>
Phân tích thành phần câu lệnh trên:
- `docker container run` đây là lệnh cơ bản để chạy một container.
>
- `-p 8080:80` tuỳ chọn này sẽ ánh xạ cổng trên máy Host sang cổng trên Container. Trong trường hợp này nó đang ánh xạ cổng 8080 trên máy Host sang cổng 80 trên Container. Điều này có nghĩa ta có thể truy cập vào máy chủ Web Nginx trên Container bằng cách sử dụng cổng 8080 trên máy Host.
>
- `--detach` hoặc `-d` tuỳ chọn này sẽ chạy Container ở chế độ nền (background), tức là Container sẽ vẫn chạy mà không cần giữ màn hình bị khoá bởi quá trình Container. Bạn vẫn có thể tiếp tục làm việc trong dòng lệnh sau khi Container được khởi chạy.
>
- `--name nginx-server` tuỳ chọn đặt tên cho Container thành *nginx-server*. Điều này làm cho việc quản lý Container trở nen dễ dàng hơn bằng cách sử dụng tên tương ứng với Container đó thay vì phải dùng ID của Container.
>
- `nginx:latest` đây là tên của Image và phiên bản của nó mà ta muốn sử dụng để khởi chạy Container.
>
- Tóm lại, câu lệnh trên tạo và chạy 1 Container với Image là Nginx bản mới nhât, ánh xạ cổng 8080 trên máy Host vào cổng 80 trên Container, và Container này chạy ở chế độ nền với tên là nginx-server.

## 5. Lệnh Stop một hay nhiều Container đang chạy
- `docker container stop <container name>` **hoặc** `docker container stop <container ID>` lệnh này sẽ stop một container cụ thể đang chạy.
>
- `docker container stop <container name 1> <container name 2> ... <container name n>` **hoặc** `docker container stop <container ID 1> <container ID 2> ... <container ID n>` lệnh này sẽ stop một loạt các container cụ thể đang chạy.

## 6. Lệnh Start một hay nhiều Container đã Stop
- `docker container start <container name>` **hoặc** `docker container start <container ID>` lệnh này sẽ start một container cụ thể đang trong trạng thái stop.
>
- `docker container start <container name 1> <container name 2> ... <container name n>` **hoặc** `docker container start <container ID 1> <container ID 2> ... <container ID n>` lệnh này sẽ start một loạt các container cụ thể đang trong trạng thái stop.

## 7. Lệnh Remove một hay nhiều Container
- Để có thể loại bỏ (remove) Container đang chạy thì đầu tiên phải Stop nó, rồi sau đó mới thực hiện việc Remove.
>
- `docker container rm <container name>` **hoặc** `docker container rm <container ID>` lệnh này sẽ remove một container cụ thể đang trong trạng thái stop.
>
- `docker container rm <container name 1> <container name 2> ... <container name n>` **hoặc** `docker container rm <container ID 1> <container ID 2> ... <container ID n>` lệnh này sẽ remove một loạt các container cụ thể đang trong trạng thái stop.

## 8. Lệnh hiển thị Logs của Container
- `docker container logs <container name>` **hoặc** `docker container logs <container ID>` lệnh này sẽ liệt kê Logs của Container cụ thể.

## 9. Lệnh hiển thị các tiến trình đang chạy trong Container
- `docker container top <container name>` **hoặc** `docker container top <container ID>` lệnh này sẽ hiển thị các tiến trình bên trong của 1 Container cụ thể.



