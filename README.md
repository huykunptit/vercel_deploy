# ESP32-CAM API

⚠️ **Lưu ý quan trọng**: 

Code detection với OpenCV và YOLO **KHÔNG THỂ** chạy trên Vercel serverless functions vì:

1. **Giới hạn kích thước**: OpenCV và YOLO quá lớn (>500MB)
2. **Giới hạn thời gian**: Vercel free tier chỉ cho 10 giây execution time
3. **Không hỗ trợ GUI**: OpenCV cần display, Vercel không có

## Giải pháp thay thế:

### Option 1: Chạy local hoặc trên server riêng
- Chạy script Python trực tiếp trên máy tính hoặc server
- Sử dụng `fake_esp32_smart_object_detector_test.py` (đã bị xóa, cần tạo lại)

### Option 2: Sử dụng dịch vụ cloud khác
- **Google Cloud Run**: Hỗ trợ container, có thể chạy OpenCV
- **AWS Lambda với container**: Hỗ trợ package lớn hơn
- **Railway/Render**: Platform hỗ trợ Python apps với dependencies nặng

### Option 3: Tách biệt API và Detection
- API trên Vercel chỉ làm proxy/relay
- Detection chạy trên server riêng hoặc local
- API gọi đến detection service

## Cách chạy local:

```bash
# Cài đặt dependencies
pip install -r requirements.txt

# Chạy detection script
python api/main.py
```

