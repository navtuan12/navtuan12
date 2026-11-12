# Nghiên cứu công cụ làm GitHub profile

Khảo sát ngày **12/11/2026**, dựa trên GitHub API, README và hướng dẫn chính thức của từng repo. Cả 11 repo bên dưới đều có `archived: false` tại thời điểm kiểm tra; điều này không bảo đảm endpoint công khai luôn hoạt động.

## Đề xuất cho navtuan12

Profile nên tập trung vào **DevOps / Platform Engineering**, với bằng chứng từ công việc: tự động hóa AWS, Kubernetes HA, CI/CD cho hơn 100 dịch vụ, observability và DevSecOps. Chọn phong cách gọn, có nhận diện riêng, hỗ trợ giao diện sáng/tối.

Bản hiện tại dùng banner SVG tự thiết kế và icon của **Skill Icons**, lưu trực tiếp trong repo. README có thể hiển thị mà không gọi dịch vụ tạo ảnh bên ngoài. Các chỉ số trong mục Selected impact lấy từ CV, không phải số đo trực tiếp từ GitHub.

## Các repo đã khảo sát

| Repository | Công dụng | Cách dùng / giới hạn | Đề xuất |
| :--- | :--- | :--- | :--- |
| [awesome-github-profile-readme](https://github.com/abhisheknaiidu/awesome-github-profile-readme) | Bộ sưu tập profile mẫu theo phong cách | Dùng để tham khảo bố cục; không phải công cụ render | Tham khảo cách trình bày, điều chỉnh theo CV |
| [github-profile-readme-generator](https://github.com/rahuldkjain/github-profile-readme-generator) | Form sinh Markdown, social links, skills và widget | Nhanh để tạo khung; nội dung mặc định cần biên tập | Hợp cho bản đầu; bản này được viết riêng |
| [skill-icons](https://github.com/tandpfun/skill-icons) | Icon công nghệ đồng bộ, có theme sáng/tối | Endpoint `skillicons.dev`; có thể lưu SVG về repo | **Đã dùng** cho 12 công nghệ có trong CV |
| [shields](https://github.com/badges/shields) | Badge cho email, stack, trạng thái build và dữ liệu repo | Badge động phụ thuộc dịch vụ và nguồn dữ liệu | Hữu ích cho repo dự án; profile hiện dùng liên kết chữ gọn hơn |
| [capsule-render](https://github.com/kyechan99/capsule-render) | Header/footer dạng wave, gradient, text | README dự án khuyến nghị deploy riêng để dùng ổn định | Thay thế nhanh nếu muốn đổi banner; bản này có SVG riêng |
| [readme-typing-svg](https://github.com/DenverCoder1/readme-typing-svg) | Dòng chữ có hiệu ứng gõ | SVG động từ endpoint; hỗ trợ tự host | Tùy chọn nếu thích animation; nội dung tĩnh dễ đọc hơn trên mobile |
| [github-readme-stats](https://github.com/anuraghazra/github-readme-stats) | Stats, top languages, pin cards | Public endpoint là best-effort; upstream khuyến nghị Actions sinh SVG hoặc self-host | Lựa chọn đầu tiên nếu bổ sung một card thống kê |
| [metrics](https://github.com/lowlighter/metrics) | Dashboard SVG với nhiều plugin về hoạt động, ngôn ngữ, repo | Actions / Docker / self-host; quyền token tùy plugin, cấu hình nhiều hơn | Hợp nếu muốn dashboard sâu; chọn ít plugin có ích |
| [snk](https://github.com/Platane/snk) | Animation rắn ăn contribution graph | GitHub Action sinh SVG/GIF, có palette sáng/tối; cần bước lưu output | Một animation ở cuối profile là đủ nếu muốn cá tính hơn |
| [github-readme-streak-stats](https://github.com/DenverCoder1/github-readme-streak-stats) | Card chuỗi ngày đóng góp | Có endpoint, Actions và self-host; upstream khuyên tự host để ổn định | Tùy chọn; không đại diện đầy đủ cho công việc tại doanh nghiệp |
| [github-profile-trophy](https://github.com/ryo-ma/github-profile-trophy) | Trophy dựa trên chỉ số GitHub | Dịch vụ sinh SVG theo tài khoản | Ít ưu tiên với profile tuyển dụng DevOps; dễ làm bố cục dài |

## Nếu bổ sung widget sau này

Ưu tiên **một card github-readme-stats được sinh thành SVG bằng GitHub Actions** và lưu trong repo, thay vì nhúng nhiều endpoint động. Hướng dẫn upstream: [GitHub Actions setup](https://github.com/anuraghazra/github-readme-stats#github-actions).

Stats công khai có thể dùng `GITHUB_TOKEN` theo hướng dẫn upstream. Dữ liệu private cần token và cấu hình phù hợp. Không cần bổ sung token để dùng README hiện tại. Trước khi bật workflow, kiểm tra quyền ghi `contents`, nhánh được bảo vệ và phiên bản action; nên pin action bằng commit SHA đã kiểm tra.

Nếu muốn animation, [Platane/snk](https://github.com/Platane/snk#github-action) có biến thể `svg-only` và hỗ trợ hai theme. Chỉ thêm ảnh vào README sau khi workflow đã tạo và lưu output thành công.

Top languages tính từ mã nguồn repo không thể hiện đầy đủ năng lực DevOps hoặc stack làm việc trong repo công ty. Phần kinh nghiệm và dự án thực tế nên đứng trước các widget.

## Đối chiếu CV và GitHub

- CV có 3 trang, ghi ngày 08/09/2026. Giữ mốc công việc và các số liệu gần đúng đúng như CV.
- `navtuan12/navtuan12` đã tồn tại và README công khai đang trống khi khảo sát.
- `K8sMultiMasterDeploy` mô tả hạ tầng **AWS**. Dự án Kubernetes **vSphere tại DXFutureTech** trong CV là một mục kinh nghiệm riêng, không gán nhầm thành cùng dự án.
- `Monitoring-K8s` dùng nhánh mặc định `backup`; link trong profile trỏ thẳng vào nhánh này. Cây mã nguồn có Terraform cho EKS và cấu hình Prometheus/Grafana/Netdata.
- `KLTN` có mã nguồn và tài liệu ở thư mục con nhưng thiếu README gốc. Nội dung giới thiệu nghiên cứu đối chiếu CV và cây mã nguồn; link bản luận văn lấy từ PDF.
- `Job-Seeker` có README mô tả Spring Boot, React, MongoDB, JWT và Docker Compose.
- Link luận văn được giữ đúng theo CV. Máy thực hiện khảo sát không kết nối được tới `ir.vnulib.edu.vn`, nên chưa xác minh độc lập trang đích.
- Không đưa fork như `opengrep`, `agentops`, `platform` vào danh sách dự án tự xây dựng chỉ vì chúng có trong tài khoản.

## Nguồn chính thức

- [GitHub: Managing your profile README](https://docs.github.com/en/account-and-profile/how-tos/profile-customization/managing-your-profile-readme)
- [GitHub: Pinning items to your profile](https://docs.github.com/en/account-and-profile/how-tos/profile-customization/pinning-items-to-your-profile)
- [GitHub: Theme-specific images](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#specifying-the-theme-an-image-is-shown-to)
- [Skill Icons: supported icons and themes](https://github.com/tandpfun/skill-icons#specifying-icons)
- [GitHub Readme Stats: endpoint reliability notice](https://github.com/anuraghazra/github-readme-stats#important-notices)
- [Metrics: setup options](https://github.com/lowlighter/metrics#-setup)

Thời điểm cập nhật ghi nhận từ API, chỉ để tham chiếu: awesome-profile 11/09/2026; generator 28/10/2025; skill-icons 27/02/2026; shields 12/11/2026; capsule-render 11/11/2026; typing-svg 09/11/2026; stats 01/10/2026; metrics 29/05/2026; snk 18/10/2026; streak-stats 09/11/2026; trophy 27/10/2026. `pushed_at` không đồng nghĩa với ngày phát hành hoặc thay đổi mã nguồn gần nhất.
