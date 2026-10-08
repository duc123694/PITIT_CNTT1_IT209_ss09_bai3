# Bài 3: Đóng gói trang Web HTML tĩnh bằng Dockerfile

Đóng gói trang `index.html` đơn giản vào image Nginx (Alpine).

## Cấu trúc

| Tệp | Mô tả |
|-----|-------|
| `index.html` | Trang web tĩnh: `<h1>Hello Docker Session 09!</h1>` |
| `Dockerfile` | Dựa trên `nginx:alpine`, copy `index.html` vào thư mục web của Nginx |

## Dockerfile

```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
```

## Cách chạy

```bash
# 1. Build image
docker build -t my-html-app:v1 .

# 2. Chạy container, map cổng 8081 (host) -> 80 (container)
docker run -d -p 8081:80 --name html-app my-html-app:v1

# 3. Kiểm tra
curl http://localhost:8081
```

## Kết quả mong đợi

```
<h1>Hello Docker Session 09!</h1>
```

## Dọn dẹp

```bash
docker rm -f html-app
```
