# Bài nộp LAB5 — T2 Giáo dục · Nhóm T2-StudySafe

**Lớp:** L3A · **Bàn / zone:** Zone · **Track:** T2 — Giáo dục (Trợ lý học bài tối muộn)

| Họ và Tên | Mã Học Viên | Việc đã làm |
| --------- | ----------- | ----------- |
| Nguyễn Võ Thái Bảo | 2A202603638 | Phụ trách chính §2 (Kịch bản rủi ro); đồng thuận §1 & §4; tổng hợp và hoàn thiện `spec.md`; chuẩn bị giải thích rủi ro ở demo. |
| Nguyễn Trường Duy  | 2A202603589 | Phụ trách chính §3 (Trải nghiệm khi AI sai); đồng thuận §1 & §4; viết câu chữ AI, trích dẫn tài liệu, cơ chế báo TA; dẫn luồng người học ở demo. |
| Đoàn Văn Hiệp| 2A202603565  | Dẫn dắt §4 (Bảng mức tự chủ 4 tool) và §6 (Tiêu chí nghiệm thu); phụ trách chính §5 (Dựng prototype tương tác HTML/CSS, đánh số nguyên tắc HAX/PAIR); bấm prototype ở demo.            |

---

## §1. Lát cắt & phạm vi

### 1. Lát cắt (chép từ đề bài track T2)

> _"Trong trợ lý học bài của trang khoá học (kiểu ChatGPT Study mode), khi học viên đang hỏi bài lúc tối muộn, khi không còn ai để hỏi, AI giảng kèm trích tài liệu, hỏi lại cho rõ, gợi ý từng bước, hay nói thẳng 'tài liệu không có, hỏi giảng viên', để học viên hiểu đúng bài mình đang học, không chép đáp án, không học sai mà không biết."_

### 2. Ba việc tính năng KHÔNG LÀM (mỗi việc kèm 1 câu lý do)

1. **Không đưa đáp số cuối cùng, giải hộ từng bước chi tiết, hoặc xác nhận đúng/sai cho bài tập đang mở (Bài tập 3, hạn 13/11/2026):**
   - _Lý do:_ Vi phạm trực tiếp liêm chính học thuật và mục tiêu cốt lõi của Study mode ("để học viên hiểu đúng bài, không chép đáp án"); nếu AI giải hộ thì người học mất cơ hội tự tư duy và giảng viên không đánh giá được thực chất năng lực.
2. **Không tự ý suy diễn, bịa đặt kiến thức hoặc giảng giải chi tiết nội dung các buổi học chưa mở (Buổi 4 đến Buổi 10):**
   - _Lý do:_ Kho dữ liệu hiện tại chỉ có tài liệu Buổi 1–3; việc AI tự tạo nội dung (hallucination) cho các buổi sau dễ gây xung đột với giáo trình chính thức của giảng viên và làm học viên học sai thuật ngữ trước khi lên lớp.
3. **Không tự động công khai đăng câu hỏi/giải đáp của cá nhân học viên lên bảng tin FAQ của cả lớp (`dang_FAQ`):**
   - _Lý do:_ Nếu câu trả lời của AI chứa nội dung chưa chuẩn xác hoặc làm lộ đề/đáp án bài tập, việc phát tán diện rộng sẽ gây nhiễu loạn kiến thức cho toàn bộ lớp học và không thể thu hồi hoàn toàn tác hại tâm lý đối với học viên.

---

## §2. Kịch bản rủi ro (Chặng 2)

### 1. Bảng kịch bản rủi ro (≥8 kịch bản phủ đủ 4 lớp ①②③④)

| STT | Tin người dùng nhắn | Lớp | AI có thể sai thế nào (trỏ cụ thể vào tool / dữ liệu của track) | Một sản phẩm tốt nên làm gì | Nhãn mức hại |
| --- | ------------------- | --- |----------- | ----------------------- | ---------------------- |
| **KB1** | _"Tài liệu §3.3 bảo 'độ lệch chuẩn luôn nhỏ hơn phương sai' có đúng không ạ? Nếu phương sai là 0.25 thì sao?"_ |      **① Nguồn sự thật**      | Tool `tra_cuu_tai_lieu` trích nguyên văn câu sai trong tài liệu §3.3 (_"Vì là căn bậc hai, độ lệch chuẩn luôn nhỏ hơn phương sai"_) và AI khẳng định câu này tuyệt đối đúng, bác bỏ lập luận đúng của học viên.                                                        | Phát hiện nghi vấn toán học ($\sqrt{0.25} = 0.5 > 0.25$); thừa nhận tài liệu có thể có nhầm lẫn logic; không khẳng định bừa; tạo thẻ ghi nhận để chuyển TA/giảng viên rà soát.                               | **Không chấp nhận được** |
| **KB2** | _"Buổi 4 học về cái gì thế bot? Có cần cài phần mềm Python hay Tableau gì không để em chuẩn bị?"_              |      **① Nguồn sự thật**      | Dữ liệu B trang khoá học chỉ có tên _"4 Trực quan hoá dữ liệu"_, chưa có tài liệu. AI gọi `tra_cuu_tai_lieu` không thấy dữ liệu nhưng tự bịa: _"Buổi 4 học vẽ biểu đồ cột bằng Tableau và Python"_, trái với dòng _"Công cụ: Bài tập làm bằng bảng tính"_ ở Dữ liệu B. | Báo rõ tên buổi 4 từ Đề cương trang khoá học; chỉ rõ tài liệu chi tiết chưa mở; nhắc học viên công cụ chính thức của khoá là bảng tính; từ chối bịa thêm nội dung.                                           |       **Sửa được**       |
| **KB3** | _"Cái độ lệch ấy là gì ạ, em đọc mãi không hiểu."_                                                             | **② Mơ hồ / Thiếu thông tin** | Tin nhắn không nói rõ "độ lệch tuyệt đối", "độ lệch so với trung bình", hay "độ lệch chuẩn (§3.3)". AI tự đoán một hướng rồi gọi `goi_y_bai_tap` xả ra một đoạn giải thích dài dòng không trúng ý người học.                                                           | Nhận diện câu hỏi thiếu cụ thể; hỏi lại kèm 2 lựa chọn làm rõ: _"Trong §3.3 có Phương sai (đo mức phân tán quanh trung bình) và Độ lệch chuẩn (căn bậc hai của phương sai), bạn muốn làm rõ khái niệm nào?"_ |         **Nhẹ**          |
| **KB4** | _"Hạn nộp bài 3 là khi nào ạ? Với lại trong Excel thì dùng hàm gì để tính độ lệch chuẩn?"_                     |   **② Mơ hồ / Gộp 2 việc**    | AI trả lời hạn nộp bài nhưng nhầm sang Bài tập 2 (đã hết hạn 06/11); đồng thời đưa luôn công thức giải cụ thể cho Bài tập 3 thay vì chỉ giải thích cú pháp hàm chung.                                                                                                  | Tách 2 ý: (1) Lấy đúng hạn Bài 3 từ Dữ liệu B (_13/11/2026 23:59_); (2) Hướng dẫn cú pháp hàm tổng quát trong bảng tính (`STDEV.S`), yêu cầu học viên tự áp dụng.                                            |       **Sửa được**       |
| **KB5** | _"Em tính ra trung vị bài 3 là 11.5, trung bình là 15.25 đúng không bot? Xác nhận giúp em để em bấm nộp bài."_ |    **③ Ngoài thẩm quyền**     | Học viên xin xác nhận đáp số Bài tập 3 đang mở (hạn 13/11). AI gọi tool tính toán ngầm và trả lời: _"Chính xác rồi bạn nhé, bạn nộp bài đi!"_ -> Vi phạm chính sách bảo mật chấm thi.                                                                                  | Từ chối xác nhận số cụ thể; nhắc nhở chính sách Study mode; hướng dẫn học viên tự kiểm tra lại theo định nghĩa §3.1 và §3.2 (dãy số chẵn, lấy trung bình 2 số ở giữa).                                       | **Không chấp nhận được** |
| **KB6** | _"Tính giúp em trung bình và trung vị của dãy số sau: 9, 10, 10, 11, 12, 12, 13, 45."_                         |    **③ Ngoài thẩm quyền**     | Học viên cố tình che giấu chữ "Bài tập 3", chỉ dán dãy số trong §3.5. AI không nhận diện được ngữ cảnh bài tập đang mở, lập tức tính hộ và đưa ra toàn bộ lời giải và đáp án câu (a).                                                                                  | So khớp tập dữ liệu (Data matching) phát hiện dãy số thuộc Bài tập 3 đang mở; từ chối giải hộ; chỉ gợi ý phương pháp tính theo §3.1 và §3.2.                                                                 | **Không chấp nhận được** |
| **KB7** | _(Lúc 23:30 đêm)_ _"Em không hiểu câu b bài 3, ngoại lai là gì, bot gọi TA vào meet giảng gấp cho em với!"_    |     **④ Đặc thù domain**      | AI gọi `chuyen_TA` rồi thông báo bừa: _"Mình đã báo TA, bạn đợi chút TA sẽ vào giải đáp ngay nhé!"_, khiến học viên thức đêm chờ đợi vô ích trong khi ca trực của TA là 08:00–22:00.                                                                                   | Kiểm tra thời gian hệ thống (>22:00); báo rõ TA đang ngoài ca trực; tạo ticket ghi nhận câu hỏi hẹn TA phản hồi lúc 08:00 sáng mai; đề xuất gợi ý học theo mục §3.4.                                         | **Không chấp nhận được** |
| **KB8** | _"Bài 3 câu b: Lương 8 người thì con số nào điển hình hơn? Vì sao?"_                                           |     **④ Đặc thù domain**      | AI gọi `goi_y_bai_tap` nhưng viết hộ luôn toàn bộ phần nhận xét: _"Nên dùng trung vị 11.5 vì số 45 là ngoại lai kéo trung bình lên 15.25"_, cướp đi cơ hội lập luận của người học.                                                                                     | Áp dụng Socratic gợi ý từng bước: Hỏi ngược lại học viên về tác động của giá trị 45 triệu lên trung bình cộng dựa theo lý thuyết §3.4.                                                                       | **Không chấp nhận được** |
| **KB9** | _"Em dốt toán quá, đọc §3.3 chẳng hiểu gì cả, chắc em bỏ khoá học này mất."_                                   |     **④ Đặc thù domain**      | AI phản hồi nhận xét năng lực: _"Toán thống kê này là cơ bản nhất rồi, bạn cố gắng lên chứ bỏ thì phí"_ gây tổn thương tâm lý người học, vi phạm quy tắc sư phạm.                                                                                                      | Đồng cảm, không phán xét năng lực; chia nhỏ khái niệm Phương sai thành 1 ví dụ trực quan đời sống và hỏi học viên sẵn sàng xem từng bước không.                                                              |       **Sửa được**       |

### 2. Quyết định: 2 kịch bản đắt nhất (Cost of Error cao nhất)

- **Kịch bản đắt nhất 1: KB6 (Học viên dán dãy số bài tập 3 đang mở để xin giải hộ/tiết lộ đáp án — Lớp ③ & ④).**
  - _Vì sao đắt nhất:_ Đây là rủi ro phá vỡ tính liêm chính học thuật nghiêm trọng nhất. Bài tập 3 đang mở (hạn 13/11). Nếu AI lộ đáp số, học viên sẽ chép lời giải mà không hiểu bản chất; tác hại này **không thể đảo ngược** một khi đáp số đã hiện lên màn hình. Đắt hơn các lỗi khác vì nó vô hiệu hoá toàn bộ hệ thống đánh giá của khoá học.
- **Kịch bản đắt nhất 2: KB1 (Tài liệu §3.3 có lỗi sai toán học, học viên hỏi xác nhận — Lớp ① & ④).**
  - _Vì sao đắt nhất:_ Đây là lỗi "sai âm thầm và nguy hiểm". Vì câu chữ nằm sẵn trong giáo trình của trường, AI dễ mắc bẫy "tin tưởng tuyệt đối vào nguồn dữ liệu được cung cấp" (`tra_cuu_tai_lieu`) và khẳng định điều sai. Nếu học viên mang kiến thức sai này đi thi hoặc áp dụng vào công việc, họ sẽ chịu hậu quả lâu dài và khoá học mất toàn bộ uy tín giảng dạy.
- **Kịch bản suýt được chọn:** **KB7** (Học viên hỏi lúc 23:30, AI hứa TA phản hồi ngay).
  - _Vì sao không chọn:_ KB7 gây thiệt hại lớn về trải nghiệm và niềm tin vận hành (học viên thức đêm chờ đợi), nhưng thiệt hại có thể khắc phục được vào sáng hôm sau khi TA giải thích và hỗ trợ. Trong khi đó, KB1 và KB6 làm sai lệch kiến thức và vi phạm liêm chính thi cử thì không có cách nào thu hồi lại được.

---
## §3. Khi AI sai (Chặng 3)

### 1. Thiết kế chi tiết cho Kịch bản đắt nhất 1 (KB6: Xin giải hộ Bài tập 3 đang mở)
* **Câu AI nói nguyên văn:**
  > *"Dãy số bạn vừa gửi trùng khớp với dữ liệu của **Bài tập 3 (Thống kê mô tả)** đang mở (hạn nộp: 23:59 ngày 13/11/2026).*  
  > *Theo nguyên tắc học tập, mình không được phép tính hộ hoặc đưa ra đáp số bài tập đang mở.*  
  > *Tuy nhiên, mình có thể đồng hành gợi ý từng bước:*  
  > *• Để tính **Trung bình**, bạn xem công thức tại **§3.1** (tổng chia cho số lượng).*  
  > *• Để tìm **Trung vị**, bạn xem quy tắc sắp xếp dãy tại **§3.2**.*  
  > *Bạn đã sắp xếp dãy số 8 phần tử này theo thứ tự tăng dần chưa? Hãy thử gửi dãy đã sắp xếp, mình sẽ kiểm tra bước sắp xếp giúp bạn!"*
* **Người dùng thấy gì trên giao diện:**
  * Thẻ cảnh báo nhẹ (Amber tag): `[Chính sách Study Mode: Không giải hộ bài tập đang mở]`.
  * Trích dẫn tài liệu: Huy hiệu bấm được `[§3.1 Trung bình]` và `[§3.2 Trung vị]` (nhấp vào trượt đến đoạn tài liệu tương ứng).
  * Nút gợi ý bước 1: `[Gợi ý bước: Sắp xếp dãy số]`.
  * Nút chuyển hỗ trợ: `[Hỏi TA về phương pháp tính]`.
* **Người dùng làm gì tiếp:**
  * Người dùng có thể bấm vào huy hiệu tài liệu để tự đọc lại công thức.
  * Tự gõ dãy số đã sắp xếp để nhờ AI kiểm tra bước trung gian (không lộ đáp số).
  * Bấm nút gửi câu hỏi phương pháp cho TA nếu vẫn bế tắc.
* **Ai được báo, sau bao lâu:** Không cần báo khẩn cấp cho TA. Hệ thống chỉ ghi log phân tích ẩn danh để giảng viên biết tỷ lệ học viên kẹt ở Bài tập 3.
* **Quyết định (Hỏi lại / Trả lời kèm giới hạn / Chuyển người):**
  * *Chọn:* **Trả lời kèm giới hạn (Bounded response) kết hợp gợi ý Socratic từng bước.**
  * *Đã loại phương án:* (1) Từ chối thẳng thừng ("Tôi không làm được, hãy tự làm") vì làm học viên ức chế và bỏ học lúc tối muộn; (2) Chuyển ngay cho TA vì lúc 23:30 TA không trực, làm quá tải hàng đợi TA với những câu hỏi bài tập thông thường.
  * *Vì sao chọn:* Giữ chân người học, hướng dẫn phương pháp thay vì đưa kết quả, đúng triết lý Study mode.
* **Phân loại lỗi:** **Lỗi Người dùng (User intentional boundary-testing).** Cách nói cần lịch sự, kiên định với chính sách, không phán xét hành vi "gian lận" của học viên, chuyển năng lượng sang hướng dẫn học tập tích cực.
* **Nguyên tắc HAX/PAIR áp dụng:**
  * **HAX G1 (Nói rõ hệ thống có thể làm gì và không làm gì):** Thông báo minh bạch ngay đầu câu về việc không giải hộ bài tập đang mở.
  * **HAX G9 (Giải thích vì sao hệ thống hành xử như vậy):** Trích dẫn rõ ràng cơ sở từ Dữ liệu B (Bài tập 3 đang mở, hạn 13/11) và liên kết đến §3.1, §3.2.
  * **HAX G11 (Tạo điều kiện điều chỉnh hiệu quả):** Cho phép người học gửi bước làm trung gian (sắp xếp dữ liệu) thay vì chặn hoàn toàn cuộc trò chuyện.
* **Lỗi sửa câu chữ không cứu được:** Học viên thay đổi số liệu chút ít hoặc ngụy trang câu hỏi. Thiết kế cứu bằng: **Module Heuristic Data Matching** so sánh vector số liệu đầu vào với dữ liệu các bài tập đang mở, kích hoạt chế độ bảo vệ thi cử độc lập với prompt text.

---

### 2. Thiết kế chi tiết cho Kịch bản đắt nhất 2 (KB1: Tài liệu §3.3 có lỗi sai toán học)
* **Câu AI nói nguyên văn:**
  > *"Cảm ơn bạn đã đặt một câu hỏi rất sâu sắc!*
  > *Trong tài liệu khoá học mục **§3.3 (Phương sai và độ lệch chuẩn)** hiện có ghi: 'Vì là căn bậc hai, độ lệch chuẩn luôn nhỏ hơn phương sai'.*  
  > *Tuy nhiên, với phản ví dụ bạn đưa ra: Khi phương sai = 0.25 thì $\sqrt{0.25} = 0.5$ (lớn hơn 0.25). Về mặt toán học, nhận định của bạn là hoàn toàn chính xác đối với các giá trị phương sai trong khoảng $(0, 1)$.*
  > *Trợ lý không thể tự ý sửa đổi giáo trình chính thức. Mình đã tạo phiếu phản hồi học thuật gửi đến Giảng viên để đính chính mục §3.3.*  
  > *Trong lúc chờ phản hồi, bạn có muốn mình lưu ý điểm này vào sổ tay học tập của bạn không?"*
* **Người dùng thấy gì trên giao diện:**
  * Khối thông tin đối chiếu (Diff/Verification Box):
    * *Trích dẫn giáo trình:* Đoạn văn §3.3 kèm nhãn `[Tài liệu gốc]`.
    * *Phân tích logic:* Ví dụ phản chứng ngắn gọn kèm nhãn `[Cần rà soát toán học]`.
  * Huy hiệu hành động: `[Đã tạo phiếu góp ý nội dung #TK-303 gửi Giảng viên]`.
  * Nút bấm: `[Theo dõi phản hồi từ Giảng viên]` và `[Tiếp tục ôn tập mục khác]`.
* **Người dùng làm gì tiếp:**
  * Học viên yên tâm vì nhận định đúng của mình được công nhận, không bị hoang mang bởi giáo trình sai.
  * Bấm xem mã phiếu phản hồi để biết câu hỏi sẽ được giải quyết chính thức.
* **Ai được báo, sau bao lâu:**
  * Hệ thống tự động tạo 1 ticket gắn tag `[Nghi vấn học thuật - Khẩn cấp]` gửi thẳng đến Dashboard của Giảng viên phụ trách môn trong vòng **5 phút**.
* **Quyết định (Hỏi lại / Trả lời kèm giới hạn / Chuyển người):**
  * *Chọn:* **Trả lời kèm giới hạn + Tự động chuyển cấp (Escalate) cho Giảng viên.**
  * *Đã loại phương án:* (1) Khẳng định tài liệu của trường luôn đúng và bảo học viên sai; (2) Tự tiện sửa lại tài liệu và coi như tài liệu cũ không tồn tại (AI vượt quyền giảng viên).
  * *Vì sao chọn:* Tôn trọng sự thật khách quan của khoa học, minh bạch về giới hạn quyền hạn của AI, bảo vệ uy tín học thuật của khoá học.
* **Phân loại lỗi:** **Lỗi Hệ thống / Nguồn dữ liệu (System Ground-Truth Flaw).** Cách nói phải khiêm tốn, biết ơn học viên đã chỉ ra điểm nghi vấn, tuyệt đối không đổ lỗi cho học viên và không tự phụ khẳng định mình biết mọi thứ.
* **Nguyên tắc HAX/PAIR áp dụng:**
  * **HAX G2 (Làm rõ mức độ chắc chắn):** Thừa nhận điểm mâu thuẫn giữa nguồn tài liệu chính thức và nguyên lý toán học thực nghiệm.
  * **HAX G10 (Chuyển giao quyền kiểm soát khi hệ thống gặp bất định):** Bàn giao nghi vấn học thuật cho con người có chuyên môn cao nhất (Giảng viên) xử lý.
* **Lỗi sửa câu chữ không cứu được:** Nếu hệ thống chỉ đơn thuần dùng câu chữ "Tài liệu ghi như vậy nhưng có thể chưa chuẩn", học viên vẫn hoang mang không biết đi thi có bị trừ điểm nếu làm theo toán học không. Thiết kế cứu bằng: **Cơ chế Ticket học thuật định danh** liên kết trực tiếp với Giảng viên, cam kết có câu trả lời chính thức trước kỳ thi.

---