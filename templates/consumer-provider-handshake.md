# Consumer–Provider Handshake — Pair 02

## Thông tin chung

- **Lab**: FIT4110 Lab 03
- **Ngày**: 03-06-2026
- **Provider team**: team-vision (AI Vision - Đại diện: Nguyễn Minh Mạnh)
- **Consumer team**: team-core (Core Business - Đại diện: Nguyễn Văn Hưởng)
- **Provider service**: AI Vision
- **Consumer service**: Core Business

## Contract

- **Contract file**: `contracts/ai-vision.openapi.yaml`
- **Mock base URL**: `http://localhost:4011`
- **Auth method**: Bearer Token
- **Endpoint được test**: `POST /detect` (Nhận diện đối tượng trong ảnh)

## Smoke test

### Request

```http
POST /detect
Authorization: Bearer lab-token
Content-Type: application/json
```

```json
{
  "camera_id": "CAM01",
  "image_url": "https://example.com/frame.jpg"
}
```

### Expected response

```json
{
  "detection_id": "DET001",
  "camera_id": "CAM01",
  "label": "person",
  "confidence": 0.91,
  "risk_level": "medium"
}
```

## Kết quả

- [x] Consumer gọi mock thành công.
- [x] Consumer parse được field cần dùng (nhận diện được `detection_id`, `label` và `confidence` để chạy Policy Engine).
- [x] Consumer hiểu lỗi 4xx/5xx provider trả về (sử dụng định dạng lỗi chuẩn hóa `ProblemDetails`).
- [x] Có Newman report hoặc screenshot đính kèm làm bằng chứng.

## Ghi chú thay đổi hợp đồng

| Nội dung | Trước | Sau | Người đồng ý |
|---|---|---|---|
| Tiền tố đường dẫn | `/vision/detect` | `/detect` | Nguyễn Văn Hưởng & Nguyễn Minh Mạnh |
| Định dạng trường | camelCase (`cameraId`) | snake_case (`camera_id`) | Nguyễn Văn Hưởng & Nguyễn Minh Mạnh |

## Xác nhận

- **Provider representative**: Nguyễn Minh Mạnh
- **Consumer representative**: Nguyễn Văn Hưởng
