# Reliability Checklist - Core Business → AI Vision

## Thông tin chung
- **Consumer:** Core Business (B6)
- **Provider:** AI Vision (B4)
- **Ngày:** 03/06/2026

## Checklist

| Tiêu chí | Trạng thái | Ghi chú / Bằng chứng |
|----------|-----------|----------------------|
| **Timeout handling** | ✅ Đạt | Negotiation Issue #6: timeout 3 giây |
| **Fail-closed policy** | ✅ Đạt | Khi timeout, Core từ chối truy cập (Issue #6) |
| **Correlation ID** | ✅ Đạt | Header `X-Correlation-Id` bắt buộc (Issue #5) |
| **Idempotency** | ✅ Đạt | Dùng correlationId để trace và deduplicate |
| **Retry strategy** | ⏳ Chưa xác định | Sẽ thống nhất trong Lab 04 |
| **Rate limiting** | ⏳ Chưa có | Cần bổ sung response 429 |
| **Health check** | ✅ Đạt | Endpoint `GET /health` hoạt động |
| **Error response format** | ✅ Đạt | Dùng ProblemDetails (RFC 7807) |
| **Image size limit** | ✅ Đạt | 4MB (Issue #4) |
| **URL length limit** | ✅ Đạt | 2048 characters (Issue #4) |
| **DetectionId format** | ✅ Đạt | UUID format (Issue #3) |

## Kết luận
API đạt độ tin cậy cơ bản, có thể tích hợp giữa Core Business và AI Vision.