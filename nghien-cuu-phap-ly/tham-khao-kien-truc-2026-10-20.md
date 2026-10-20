# Nghiên cứu mã nguồn tham khảo – Hệ thống pháp lý dự án
Ngày kiểm tra: 20/10/2026.

## Nguồn tham khảo
1. [quytrinhctctdt](https://github.com/anhtuantkht-cmd/quytrinhctctdt): Public, có `index.html`, `README.md`, `.nojekyll`. Phiên bản đã kiểm tra: [70a4622c95491f9436de1eb622b73c467723b702](https://github.com/anhtuantkht-cmd/quytrinhctctdt/commit/70a4622c95491f9436de1eb622b73c467723b702).
2. [quytrinhquyhoach](https://github.com/anhtuantkht-cmd/quytrinhquyhoach): Public nhưng kho trống tại ngày kiểm tra, chưa thể phân tích mã nguồn.

## Kết quả đối với quytrinhctctdt
- Kiến trúc website tĩnh, gần như tất cả nằm trong `index.html` (1.560 dòng): giao diện HTML, CSS, bốn sơ đồ SVG, JavaScript và dữ liệu thủ tục.
- 5 tab nội dung: Tổng quan & căn cứ; Cơ quan lập hồ sơ; Trình tự thủ tục; Cơ chế phối hợp; Checklist theo Sở.
- JavaScript: `switchTab`, `switchSubtab`, `toggleChk`, `togglePhieu`, `exportPhieuWord`, `renderSharpAvatar`.
- Dữ liệu biểu mẫu tại `PHIEU_DATA`, gồm 11 nhóm cơ quan, 69 dòng tiêu chí.
- Không phát hiện kết nối API, máy chủ xử lý hoặc lưu trạng thái checklist.
- Xuất Word theo cách tải một tệp HTML có phần mở rộng `.doc`, không phải `.docx` thực.
- Có ID trùng trong SVG; hàm đổi tab dựa vào biến sự kiện toàn cục `event` và không tách riêng mô hình dữ liệu.
- `README.md` nhắc thư mục `classic/`, nhưng nhánh `main` tại thời điểm kiểm tra không chứa thư mục này.

## Kế thừa và cải tiến
**Kế thừa nguyên lý:** điều hướng tab, sơ đồ quyết định, sơ đồ quy trình, checklist theo cơ quan, xuất biểu mẫu.

**Không kế thừa kiến trúc một tệp:** Cần tách dữ liệu pháp luật khỏi giao diện, chuẩn hóa điều–khoản–điểm, thời điểm hiệu lực, điều khoản chuyển tiếp, luồng kiểm chứng và lịch sử cập nhật. Checklist phải lưu tiến độ theo dự án; mẫu Word phải sinh từ trạng thái đã lưu.

**MVP đề xuất:** Chuyên đề 'Chấp thuận chủ trương đầu tư và lựa chọn nhà đầu tư' với sơ đồ điều kiện, checklist, nguồn chính thức, ghi rõ phạm vi địa phương và thời điểm áp dụng.

## Nguyên tắc bản quyền và lưu trữ
Chưa thấy tệp LICENSE trong kho gốc. GitHub xác nhận mã nguồn công khai thiếu giấy phép vẫn được bảo hộ quyền tác giả: https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository

Tài liệu này chỉ ghi nhận kết quả nghiên cứu và tham chiếu đường dẫn phiên bản; **không sao chép mã của tác giả**. Nếu cần bảo tồn nguyên mã, ưu tiên Fork trên GitHub và kiểm tra quyền sử dụng trước khi tái sử dụng hoặc phát hành sản phẩm phái sinh.

Nguồn mã tại phiên bản cố định:
- [index.html](https://github.com/anhtuantkht-cmd/quytrinhctctdt/blob/70a4622c95491f9436de1eb622b73c467723b702/index.html)
- [README.md](https://github.com/anhtuantkht-cmd/quytrinhctctdt/blob/70a4622c95491f9436de1eb622b73c467723b702/README.md)

**Phạm vi kiểm tra:** phân tích mã nguồn tĩnh; chưa kiểm thử đa trình duyệt, chưa rà soát hiệu lực từng căn cứ pháp luật.