# Consumer-Provider Handshake

## Thông tin
- **Dependency:** Core Business (B6) → AI Vision (B4)
- **Ngày handshake:** 03/06/2026
- **Môi trường test:** Mock Server (Prism)

## Xác nhận contract

| Hạng mục | Giá trị thống nhất | Source |
|----------|-------------------|--------|
| Base URL | `http://localhost:4011` (mock) | `openapi.yaml` |
| Auth method | Bearer token | `openapi.yaml` |
| Image input | `imageUrl` (string, max 2048 chars) | Issue #1 |
| Response fields | `userId`, `confidence`, `timestamp` | Issue #2 |
| DetectionId format | UUID v4 | Issue #3 |
| Image size limit | 4 MB | Issue #4 |
| Correlation ID | Required header `X-Correlation-Id` | Issue #5 |
| Timeout | 3 seconds | Issue #6 |
| Error format | ProblemDetails (RFC 7807) | `openapi.yaml` |

## Kết quả test trên mock

| Endpoint | Status | Test result |
|----------|--------|-------------|
| `GET /health` | 200 | ✅ PASS |
| `POST /vision/face-match` | 200 | ✅ PASS |
| `GET /vision/detections/{id}` | 200 | ✅ PASS |
| `GET /vision/results/recent` | 200 | ✅ PASS |
| Auth (no token) | 401 | ✅ PASS |
| Negative (missing field) | 422 | ✅ PASS |

## Xác nhận của hai bên

| Vai trò | Tên | Chữ ký | Ngày |
|---------|-----|--------|------|
| **Provider (AI Vision)** | [Tên bạn] | Đã đồng ý | 03/06/2026 |
| **Consumer (Core Business)** | [Tên bạn] | Đã đồng ý | 03/06/2026 |

## Kết luận
Hợp đồng API giữa Core Business và AI Vision đã được kiểm thử thành công trên mock server. Hai bên đồng ý chuyển sang giai đoạn phát triển service thật.