# Áp dụng profile cho navtuan12

## Các file cần đưa lên GitHub

- `README.md` đặt ở gốc repo **[navtuan12/navtuan12](https://github.com/navtuan12/navtuan12)**.
- `assets/banner-dark.svg` và `assets/banner-light.svg` là banner tự thiết kế.
- `assets/skills-dark.svg`, `assets/skills-light.svg`, `assets/NOTICE.md` và `assets/licenses/skill-icons-MIT.txt` là icon cùng ghi nhận nguồn và giấy phép.
- `assets/impact-{dark,light}.svg` là thẻ thành tích lấy từ CV.
- `assets/metrics-{dark,light}.svg` là dashboard Metrics dùng dữ liệu GitHub thật.
- `.github/workflows/metrics.yml` tự cập nhật dashboard mỗi ngày.
- `docs/` là ghi chú nghiên cứu và hướng dẫn, không hiển thị trực tiếp trên profile.

Repo profile phải công khai, có tên trùng username, và có README không rỗng ở nhánh mặc định. Bạn đã có đúng repo; sau khi cập nhật README và assets vào nhánh mặc định, GitHub sẽ hiển thị trên trang cá nhân. Xem [hướng dẫn GitHub](https://docs.github.com/en/account-and-profile/how-tos/profile-customization/managing-your-profile-readme).

Nếu có PR đi kèm, mở tab **Files changed** để xem nội dung và banner; khi ưng ý thì chuyển PR sang Ready for review và merge. PR chưa merge sẽ chưa thay đổi profile đang hiển thị.

## Dashboard Metrics

Workflow dùng [lowlighter/metrics](https://github.com/lowlighter/metrics), qua giao diện Docker chính thức, pin image stable 3.34.0 bằng digest `sha256:257392f90340f916cb8b815026f259399f6b246d3eb7de38b58bfe7a07bd5b65` (mã nguồn tương ứng revision `65836723097537a54cd8eb90f61839426b4266b6`), gồm:

- **Overview:** hoạt động và số liệu cộng đồng GitHub.
- **Isocalendar:** lịch contribution dạng 3D trong một năm.
- **Languages:** tối đa 6 ngôn ngữ, hiển thị phần trăm; loại fork, không clone repo để phân tích sâu.

Actions secret **`METRICS_TOKEN`** là token classic không chọn scope để chỉ đọc dữ liệu công khai, theo [hướng dẫn upstream](https://github.com/lowlighter/metrics/blob/master/.github/readme/partials/documentation/setup/action.md). Không cần quyền `repo`. `GITHUB_TOKEN` chỉ dùng để ghi file SVG về repo, với `contents: write`.

Secret `METRICS_TOKEN` đã được cấu hình qua ô nhập bí mật. Sau khi merge, GitHub đăng ký workflow và lần push cấu hình vào `main` kích hoạt render đầu tiên; có thể chạy lại bằng **Actions → Profile metrics → Run workflow**. Các SVG kèm PR đã được sinh thử bằng đúng image và token này. Workflow có lịch **01:23 UTC / 08:23 Việt Nam** hàng ngày; lịch chỉ chạy từ nhánh mặc định. Push thay đổi cấu hình vào `main` cũng kích hoạt render. Workflow không dùng `pull_request_target` hoặc chạy trên nội dung từ fork.

Hai biến thể chạy tuần tự để tránh xung đột khi commit. Nếu GitHub không cho Actions ghi vào nhánh được bảo vệ, điều chỉnh quy tắc nhánh hoặc chuyển sang cơ chế PR. Nếu một plugin lỗi, workflow thất bại và giữ SVG cũ để không xuất bản dashboard chứa lỗi. Giới hạn thời gian là 20 phút mỗi biến thể.

## Thông tin trong Edit profile

Các mục dưới đây cần cập nhật riêng qua **Edit profile** trên GitHub, không tự thay đổi khi merge README.

**Name**

```text
Nguyen Van Anh Tuan
```

**Bio**

```text
DevOps Engineer | AWS · Kubernetes · Infrastructure as Code · CI/CD · Observability · DevSecOps | HCMC, Vietnam
```

**Company:** `FPT Software`<br>
**Location:** `Ho Chi Minh City, Vietnam`<br>
**Public email:** `anhtuan.mmt@gmail.com` nếu muốn dùng cùng email liên hệ trong README.

CV không có LinkedIn hay website cá nhân nên bản này không thêm các đường dẫn đó.

## Repo nên ghim

Trong **Customize your pins**, ưu tiên thứ tự:

1. **K8sMultiMasterDeploy** — bằng chứng về IaC và Kubernetes.
2. **Monitoring-K8s** — bổ sung observability và EKS.
3. **KLTN** — thể hiện nghiên cứu LLM, search và khả năng đánh giá hệ thống.
4. **Job-Seeker** — thể hiện hiểu biết ứng dụng và quy trình đóng gói/chạy dịch vụ.

GitHub cho ghim tối đa 6 repo/gist; 4 repo có mô tả tốt là đủ. Nên bổ sung README gốc cho `KLTN`; sửa URL `yourusername` và kiểm tra các lệnh Helm cũ trong README `K8sMultiMasterDeploy` trước khi dùng nó như hướng dẫn triển khai. Đây là các cải thiện đề xuất cho repo dự án, chưa nằm trong thay đổi profile.

Gợi ý description cho các repo:

| Repo | Description |
| :--- | :--- |
| `navtuan12` | DevOps engineer building cloud-native infrastructure, reliable delivery pipelines, and secure platforms. |
| `K8sMultiMasterDeploy` | Kubernetes multi-master deployment on AWS with Terraform, Ansible, and CI/CD configuration. |
| `Monitoring-K8s` | AWS EKS infrastructure and Kubernetes monitoring with Prometheus, Grafana, and Netdata. |
| `KLTN` | Bachelor's thesis: LLM-assisted query rewriting and retrieval evaluation for e-commerce search. |
| `Job-Seeker` | Job search application built with Spring Boot, React, MongoDB, and Docker Compose. |

## Cập nhật về sau

- Sửa nội dung trong `README.md` khi đổi công việc hoặc có kết quả mới; giữ rõ các dấu `~` / `approximately` cho số liệu ước lượng.
- Hai banner hỗ trợ giao diện GitHub sáng và tối bằng thẻ `<picture>`. Có thể chỉnh trực tiếp SVG bằng text editor.
- Icon được lưu sẵn nên không cần workflow, hosting, hoặc secret. URL tạo và giấy phép nằm trong `assets/NOTICE.md`.
- Bản profile công khai dùng tên, thành phố và email liên hệ từ CV. File PDF gốc không được đưa vào repo; profile không chứa số điện thoại hoặc ngày sinh.
- Các lựa chọn stats, snake, typing effect và đánh giá mức phù hợp nằm trong [RESEARCH.vi.md](RESEARCH.vi.md).
