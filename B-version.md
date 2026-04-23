# Day 16 Submission — Version B
**Nguyễn Quốc Nam - 2A202600201**

---

## Reflection: Điều gì thay đổi từ A → B và tại sao

> **Version A có 3 vấn đề chính:**
>
> 1. **Customer quá rộng** — "Nhà đầu tư bán lẻ Việt Nam" (3M người) không hình dung được. Tôi cần thu hẹp xuống 1 persona cụ thể: ai, bao nhiêu tuổi, đang ở giai đoạn nào của hành trình đầu tư, pain xảy ra lúc nào trong ngày.
>
> 2. **Need là danh sách tính năng** — Version A liệt kê 3 need song song (phân tích nhanh, học cách phân tích, giám sát danh mục) mà không có business consequence thực tế. Version B chọn 1 need duy nhất và gắn nó với hậu quả tài chính cụ thể.
>
> 3. **Moat là cảm giác, không phải cơ chế** — "Domain learning" nghe có vẻ hay nhưng không thể kiểm tra được. Version B thay bằng cơ chế cụ thể: mỗi lần user đánh dấu "cảnh báo này đúng/sai" → model học → detection tốt hơn → user tiếp theo nhận được kết quả tốt hơn.
>
> **Điều tôi giữ nguyên:** Focus vào nhà đầu tư cá nhân — không pivot sang CLB hay tổ chức.

---

## 1. Reframed Idea

**Original Idea:**
> Agent tổng hợp phân tích báo cáo tài chính sau đó đưa ra lựa chọn để đầu tư

**Reframed (Version B):**
> **Công cụ AI phân tích báo cáo tài chính dành riêng cho nhà đầu tư cá nhân Việt Nam đang tự học** — tải lên báo cáo PDF, nhận ngay bản phân tích 1 trang gồm: chỉ số quan trọng, so sánh cùng kỳ, và cảnh báo rủi ro đặc thù Việt Nam trong 15 phút thay vì 3-4 giờ đọc thủ công.

**Tại sao đây là reframe tốt hơn Version A:**

| | Version A | Version B |
|:---|:---|:---|
| **Customer** | Rộng: "nhà đầu tư bán lẻ" | Hẹp: nhân viên văn phòng tự học đầu tư, có danh mục 50-300 triệu VND |
| **Need** | 3 need không phân cấp | 1 need: "đọc báo cáo mà không bỏ lỡ rủi ro" — gắn với hậu quả mất tiền thực tế |
| **Lựa chọn** | Danh sách tính năng A+B+C | Rõ ràng: phân tích báo cáo PDF → output 1 trang |
| **Moat** | "Domain learning" — vague | Data flywheel cụ thể: user feedback → model cải thiện |

---

## 2. Customer / Segment Card

**Segment Name:**
> **Nhân viên văn phòng Việt Nam (25-38 tuổi) đang tự học đầu tư cổ phiếu, có danh mục 50-300 triệu VND, không muốn phụ thuộc vào tips của người khác**

**Operating Context:**
> - **Nghề nghiệp:** Làm việc 9-5 tại văn phòng (IT, kế toán, marketing, kỹ sư) — đầu tư là hoạt động ngoài giờ
> - **Thời gian nghiên cứu:** Tối thứ Sáu, cuối tuần — đặc biệt là mùa báo cáo lợi nhuận (tháng 2, 5, 8, 11)
> - **Danh mục:** 5-15 cổ phiếu, tổng giá trị 50-300 triệu VND — đủ lớn để cảm thấy đau khi mất, đủ nhỏ để không thuê cố vấn
> - **Công cụ hiện tại:** HOSE/HNX app, Cafef.vn, YouTube, PDF báo cáo tài chính, Excel tự làm

**Recurring Workflow (điểm đau xuất hiện ở đâu chính xác?):**

```
Tháng 5 — Mùa báo cáo Q1
    ↓
Thứ Sáu tối, sau 21h, mở laptop
    ↓
Tải PDF báo cáo tài chính của VHM / MSN / HPG (40-80 trang)
    ↓
Đọc → gặp chú thích tiếng Anh kỹ thuật → bỏ qua
    ↓
Tìm chỉ số P/E, ROE, nợ/vốn → cần tính tay từ số liệu
    ↓
So sánh với quý trước → mở thêm file PDF cũ → mất thêm 1 giờ
    ↓
Tổng: 3-4 giờ cho 1 công ty. Danh sách watchlist còn 7 công ty nữa.
    ↓
Quyết định: hoặc bỏ bớt → phân tích thiếu
    hoặc dành cả cuối tuần → kiệt sức
```

**Pain Moment (cơn đau cụ thể nhất):**
> Tối Chủ Nhật, đọc báo cáo được 2 tiếng, mệt, mắt mờ. Bỏ qua phần "giao dịch với bên liên quan" ở trang 47 vì dài và khó hiểu. Hai tuần sau, cổ phiếu giảm 18% vì scandal related-party transaction vừa bị SSC điều tra — thứ đã được ghi trong báo cáo từ đầu.
>
> **Business consequence thực tế:** Mất tiền không phải vì thị trường xấu mà vì **không đọc kịp thứ đã được công khai**. Đây không phải FOMO AI — đây là lỗ hổng thông tin có thể vá được.

**Why Now:**
> - **Fact (nguồn UBCKNN 2024):** 7.1M tài khoản chứng khoán tại VN — tăng gấp đôi từ 2021
> - **Fact (quan sát):** 100% báo cáo tài chính niêm yết trên HOSE/HNX là PDF công khai, miễn phí
> - **Fact (quan sát):** AI đọc + tóm tắt PDF tiếng Việt đã hoạt động tốt từ 2023 (Claude, GPT-4)
> - **Giả định chưa kiểm tra:** ~15-20% trong 7.1M tài khoản là "tự phân tích" thay vì chỉ nghe tips → cần xác minh
> - **Giả định chưa kiểm tra:** Họ sẵn sàng trả tiền cho công cụ phân tích → cần phỏng vấn

**Access Path:**
> 1. **Tinh Tế / StockTalk:** Nơi nhà đầu tư tự học hay đặt câu hỏi "báo cáo X có vấn đề gì không?" — đây là signal tìm kiếm công cụ
> 2. **YouTube finance channels:** Nguồn học tập số 1 của nhóm này — có thể hợp tác content
> 3. **Facebook groups:** "Đầu tư chứng khoán Việt Nam", "Cổ phiếu giá trị" — 50K-200K thành viên mỗi nhóm
> 4. **Broker apps (SSI, VNDirect):** Có thể white-label hoặc in-app integration sau khi có traction

**One-Sentence Description:**
> "Nhân viên văn phòng 28 tuổi, có danh mục cổ phiếu 150 triệu VND, dành 3-4 giờ cuối tuần để đọc báo cáo tài chính thủ công, thường xuyên bỏ lỡ cảnh báo rủi ro vì không đủ thời gian đọc hết — và đã từng mất tiền vì lý do đó."

---

## 3. Need Map

### Need #1 (Priority — lý do duy nhất để build MVP)

**Job to Be Done:**
> Khi tôi cần quyết định mua, giữ, hay bán 1 cổ phiếu sau mùa báo cáo lợi nhuận, tôi muốn nắm được các chỉ số quan trọng + những thay đổi bất thường trong báo cáo chỉ trong 15 phút, để không phải chọn giữa "đọc kỹ 1 công ty" và "đọc sơ 10 công ty".

**Current Workaround:**
> - Đọc báo cáo PDF thủ công (3-4 giờ/công ty, dễ bỏ sót)
> - Xem YouTube analyst (chỉ cover VN30, không có mid/small-cap)
> - Hỏi cộng đồng StockTalk (chờ 1-2 ngày, chất lượng không đồng đều)
> - Dùng tóm tắt broker (quá chung chung, không có risk flags)
> - **Compromise thực tế:** Đọc 2-3 trang đầu rồi đoán — bỏ qua phần footnotes là nơi rủi ro thường ẩn

**Pain Signal (gắn với hậu quả kinh tế):**
> - **Thời gian:** 3-4 giờ × 10 công ty = 30-40 giờ/quý chỉ để đọc báo cáo
> - **Miss rate cao:** Footnotes về related-party, dự phòng, thay đổi kiểm toán viên — những thứ thường báo hiệu vấn đề — nằm ở cuối báo cáo, thường bị bỏ qua
> - **Hậu quả tài chính trực tiếp:** Mất 10-25% vốn trên 1 cổ phiếu vì rủi ro đã công khai mà không đọc được

**Evidence / Proxy Evidence:**

| Loại bằng chứng | Nội dung | Nguồn | Độ tin cậy |
|:---|:---|:---|:---|
| **Fact** | 7.1M tài khoản CK tại VN (2024) | UBCKNN | Cao |
| **Fact** | 100% BCTC HOSE/HNX là PDF công khai | Quan sát trực tiếp | Cao |
| **Proxy** | Từ khóa "cách đọc báo cáo tài chính" — 40K+ lượt tìm/tháng tại VN | Google Keyword Planner (có thể xác minh) | Trung bình |
| **Proxy** | 90%+ bài viết trên StockTalk là "cổ phiếu X có tốt không?" → signal không tự phân tích được | Quan sát trực tiếp | Trung bình |
| **Giả định** | 3-4 giờ/công ty là thời gian đọc báo cáo trung bình | Dựa trên 3 cuộc trò chuyện cá nhân | Thấp — cần phỏng vấn thêm |
| **Giả định** | Nhà đầu tư cá nhân sẵn sàng trả $30-50/tháng | Chưa kiểm tra | Rất thấp |

**Why Underserved:**
> - **CapitalIQ, Refinitiv:** $10K+/năm — chỉ dành cho tổ chức
> - **Broker summaries:** Chỉ cover VN30, quá chung chung, không có Vietnam-specific risk flags
> - **ChatGPT:** Tóm tắt được nhưng: (1) không được fine-tune cho VN accounting standards, (2) không phát hiện được related-party patterns cụ thể VN, (3) không lưu lịch sử để so sánh
> - **Gap thực sự:** Không có công cụ nào vừa nhanh (15 phút), vừa phát hiện rủi ro đặc thù VN, vừa để giá cá nhân có thể trả được

---

### Need #2 (Secondary — Build sau khi Need #1 được validate)

**Job to Be Done:**
> Khi tôi đã đầu tư vào 1 cổ phiếu, tôi muốn biết liệu luận điểm đầu tư của mình có còn đúng sau mỗi quý báo cáo, để quyết định giữ hay thoát — không phải vì giá lên/xuống mà vì fundamental thay đổi.

**Why Lower Priority:**
> Need #1 xảy ra trước khi mua. Need #2 xảy ra sau khi mua. Nếu người dùng không vượt qua được Need #1, họ không có danh mục để monitor. Giải quyết #1 trước.

---

### Need #3 (Không build trong 12 tháng đầu)

**Job to Be Done:**
> Học cách phân tích tài chính từ đầu — hiểu tại sao P/E quan trọng, ROE có nghĩa là gì.

**Tại sao để sau:**
> YouTube và các khóa học miễn phí đã phục vụ nhu cầu này đủ tốt. Đây không phải gap — không nên cạnh tranh ở đây.

---

## 4. Strategy Statement

**For** nhân viên văn phòng Việt Nam (25-38 tuổi) đang tự đầu tư cổ phiếu với danh mục 50-300 triệu VND
who struggle with **mất 3-4 giờ để đọc 1 báo cáo tài chính và vẫn thường xuyên bỏ lỡ cảnh báo rủi ro ẩn trong footnotes**,

**our product** helps them **nhận bản phân tích 1 trang — chỉ số quan trọng + bất thường đáng chú ý + Vietnam-specific risk flags — trong 15 phút sau khi tải lên PDF**,

through **PDF parsing + AI extraction + Vietnam-specific risk pattern matching (related-party, kiểm toán đổi, dự phòng bất thường)**,

unlike **broker summaries (chỉ VN30, không có risk), ChatGPT (không fine-tune cho VN, không lưu lịch sử), đọc thủ công (3-4 giờ)**,

because we can leverage **toàn bộ BCTC niêm yết VN là dữ liệu công khai + AI phân tích PDF tiếng Việt đã hoạt động đủ tốt + không ai đang build đúng use case này cho nhà đầu tư cá nhân VN**.

**Lựa chọn rõ ràng — Version B KHÔNG làm những thứ này:**
> - ❌ Không tự động gợi ý mua/bán
> - ❌ Không build real-time market data
> - ❌ Không target tổ chức hay quỹ đầu tư
> - ❌ Không build social/community features trong MVP
> - ✅ Duy nhất 1 workflow: PDF báo cáo vào → phân tích 1 trang ra

---

## 5. Moat Hypothesis

**Moat Mechanism: Vietnam Risk Pattern Library + Personal Analysis History**

**Cơ chế cụ thể (không phải cảm giác):**

```
Vòng 1 — Data flywheel:
User tải báo cáo VHM Q1 2024
    ↓
AI phát hiện: "Related-party transaction tăng 340% so với Q4 2023"
    ↓
User đánh dấu: "Đúng — đây là vấn đề, giá giảm 15% sau đó"
    ↓
Model học: pattern này ở ngành BĐS = signal quan trọng
    ↓
Lần sau khi phân tích báo cáo BĐS khác → detection tốt hơn
    ↓
User tiếp theo nhận kết quả tốt hơn → trust cao hơn → dùng nhiều hơn → feedback thêm
```

```
Vòng 2 — Switching cost:
User dùng 6 tháng
    ↓
Hệ thống lưu: lịch sử phân tích 20 báo cáo của user này
    ↓
Lịch sử này dùng để: so sánh "báo cáo này vs 6 tháng trước", track thesis
    ↓
Nếu user chuyển sang ChatGPT → mất toàn bộ lịch sử
    ↓
Switching cost tăng dần theo thời gian dùng
```

**Nếu có 1,000 users dùng trong 12 tháng, những thứ sau sẽ tốt hơn:**
1. **Vietnam Risk Library** — có đủ feedback để biết pattern nào thực sự báo hiệu vấn đề ở từng ngành (BĐS, ngân hàng, bán lẻ)
2. **False positive rate giảm** — ít cảnh báo nhầm hơn → user tin tưởng hơn → dùng lâu hơn
3. **Benchmark ngành** — với 1,000 báo cáo đã phân tích, có thể nói "ROE của công ty này thấp hơn 70% peer trong ngành" thay vì chỉ nêu con số

**Tại sao khó sao chép:**
> - **ChatGPT/Gemini:** Có thể copy feature nhưng không có Vietnam risk pattern library được feedback bởi người dùng thực tế — phải build từ đầu
> - **Broker apps:** Không có incentive để surface risk flags mạnh (ảnh hưởng đến doanh thu giao dịch của họ)
> - **Startup khác:** Barrier thực sự là data quality — phải có đủ feedback theo thời gian, không mua được

**Điều tôi chưa chắc về moat này:**
> Nếu Gemini/Claude 3.5 tiếp tục cải thiện nhanh, khoảng cách về accuracy có thể thu hẹp. Moat thực sự có thể là personal history + workflow integration hơn là model accuracy.

---

## 6. TAM / SAM / SOM

**Nguyên tắc:** Tôi tách rõ **điều tôi biết (fact)** vs **điều tôi giả định (assumption)** trong mỗi ước tính.

| Layer | Estimate | Cách tính | Fact vs Assumption | Confidence |
|:---|:---|:---|:---|:---|
| **TAM** | $70-140M/năm | 7.1M tài khoản (fact) × 15% "tự phân tích" (assumption) = 1.07M người × $65-130/năm (assumption) = $70-140M | Số tài khoản: fact. 15%: chưa xác minh. Giá $65: hoàn toàn là assumption. | **Thấp** |
| **SAM** | $5-20M/năm | Nhà đầu tư "tích cực" có danh mục 50M+ VND (assumption: ~200-500K người) × $25-40/năm = $5-20M | Số 200-500K: assumption. Giá $25: assumption. | **Rất thấp** |
| **SOM (12 tháng)** | $20-80K | Target 1,000-3,000 users trả tiền × $20-27/năm (freemium, ~5% conversion) = $20-80K | 1,000 users trong 12 tháng: ambitious nhưng possible nếu có 1-2 kênh tốt. Giá: chưa tested. | **Trung bình** |

**Judgment thành thật:**
> TAM/SAM của tôi là ước tính lỏng vì phần lớn là assumptions chưa kiểm tra. Tuy nhiên SOM $20-80K là con số có thể đạt được trong 12 tháng nếu willingness to pay được confirm qua phỏng vấn. Thị trường không cần lớn để validate — chỉ cần đủ để biết người ta có trả tiền không.

### Top 3 Unknowns — theo thứ tự ưu tiên:

**Unknown #1 — Phải biết trước khi viết 1 dòng code:**
> Nhà đầu tư cá nhân có sẵn sàng trả $3-5/tháng (freemium) hay $20-30/tháng (premium) không?
> - **Cách kiểm tra:** Phỏng vấn 10 người, hỏi thẳng: "Bạn đang trả tiền cho tool đầu tư nào? Bạn sẽ trả bao nhiêu để giảm 3 giờ đọc báo cáo xuống 15 phút?"
> - **Signal cần tìm:** Nếu 6+/10 nói có, proceed. Nếu không, pricing model cần rethink.

**Unknown #2 — Ảnh hưởng đến accuracy của product:**
> Related-party transactions và các risk patterns đặc thù VN — AI hiện tại có phát hiện được không, hay cần fine-tuning riêng?
> - **Cách kiểm tra:** Test với 10 báo cáo thực tế, tự đánh giá accuracy trước khi ra mắt

**Unknown #3 — Ảnh hưởng đến distribution:**
> Nhà đầu tư cá nhân tìm và trust công cụ mới qua kênh nào?
> - **Cách kiểm tra:** Trong phỏng vấn, hỏi: "Lần cuối bạn dùng tool đầu tư mới, bạn biết đến nó qua đâu?"

### Decision:
- [ ] Worth pursuing now
- [x] **Worth pursuing — validate Unknown #1 trong 1 tuần trước khi build**
- [ ] Not worth pursuing as currently framed

---

## 7. Positioning Note

**What We Are:**
> Công cụ phân tích báo cáo tài chính AI đầu tiên được tối ưu cho nhà đầu tư cá nhân Việt Nam: tải PDF báo cáo lên, nhận bản phân tích 1 trang với chỉ số quan trọng và cảnh báo rủi ro đặc thù VN trong 15 phút — không phải chatbot, không phải stock screener, không phải robo-advisor.

**What We Are Not / Not Yet:**
> Chúng tôi không đưa ra khuyến nghị mua/bán cụ thể (chúng tôi cung cấp dữ liệu để người dùng tự quyết định), chưa có real-time data feed, và chưa tích hợp vào broker apps — đó là roadmap sau khi có traction từ 1,000 users đầu tiên.

---

## 8. Self-Assessment Before Day 17

### Confidence Assessment Across 6 Links

| Link | Confidence | Tại sao? | Nghi ngờ lớn nhất |
|:---|:---|:---|:---|
| **Idea** | ★★★★☆ | Use case cụ thể, không phải cảm giác | Có ai đang build cái này cho VN market mà tôi chưa biết? |
| **Customer** | ★★★★☆ | Persona rõ (nhân viên VP, 25-38, 50-300M VND) — hình dung được | Chưa phỏng vấn đủ 10 người để confirm |
| **Need** | ★★★★☆ | 1 need duy nhất với hậu quả tài chính rõ ràng (mất tiền vì bỏ lỡ red flags) | Có phải pain đủ lớn để trả tiền không, hay họ chấp nhận sống với nó? |
| **Strategy** | ★★★★☆ | Lựa chọn rõ: PDF in → phân tích 1 trang out. Biết không làm gì. | Tại sao người dùng không chỉ dùng ChatGPT free? |
| **Moat** | ★★★☆☆ | Cơ chế cụ thể (data flywheel + switching cost) nhưng chưa được kiểm tra | Switching cost có đủ cao sau 6 tháng không? |
| **Market Size** | ★★☆☆☆ | Thành thật: TAM/SAM là assumptions. SOM là số duy nhất tôi tin. | Willingness to pay — đây là unknown quan trọng nhất |

### Strongest Link:
> **Strategy** — Version B lần đầu tiên có lựa chọn thực sự rõ ràng: 1 workflow, 1 output, danh sách không làm gì. Đây là cải thiện lớn nhất so với Version A.

### Weakest Link:
> **Market Size** — Phần lớn là assumptions. Tôi chưa biết nhà đầu tư cá nhân VN có sẵn sàng trả tiền cho công cụ phân tích không.

### Honest Reflection về thay đổi từ A → B:
> Version A của tôi mắc lỗi phổ biến: customer rộng → strategy không có lựa chọn → moat là cảm giác. Version B cải thiện bằng cách thu hẹp customer xuống 1 persona cụ thể (nhân viên VP, 25-38 tuổi, 50-300M danh mục) và để story chạy từ đó.
>
> Điều tôi vẫn chưa tự tin nhất: liệu pain này có đủ mạnh để người dùng trả tiền không, hay họ nghĩ "ChatGPT free là đủ rồi"? Đây là câu hỏi chỉ phỏng vấn mới trả lời được — không có cách nào đoán đúng từ bàn.

---

## Open Questions for Day 17

### Must Answer (theo thứ tự ưu tiên ảnh hưởng đến build/no-build):

1. **Willingness to pay** — Phỏng vấn 10 nhà đầu tư cá nhân:
   - "Bạn đang trả tiền cho tool đầu tư nào không?"
   - "Bạn sẽ trả bao nhiêu để giảm 3 giờ đọc báo cáo xuống 15 phút?"
   - **Decision gate:** 6+/10 nói có → proceed to MVP

2. **Pain intensity** — Trong phỏng vấn:
   - "Bạn đã bao giờ mua cổ phiếu rồi sau đó phát hiện rủi ro đã được ghi trong báo cáo từ đầu không?"
   - **Signal tìm kiếm:** "Có, và tôi mất tiền vì lý do đó" → pain đủ lớn

3. **Competitor check** — Search: "AI phân tích báo cáo tài chính Việt Nam", "financial report analyzer Vietnam"
   - Nếu có competitor đang build → cần differentiate rõ hơn

### Good to Know:

4. Nhà đầu tư cá nhân discover tools mới qua đâu? (→ distribution strategy)
5. Họ đang dùng ChatGPT để phân tích không? Feedback của họ là gì? (→ differentiation)
6. Báo cáo nào họ hay đọc nhất? (→ ưu tiên loại báo cáo nào để test accuracy)

---

## Next Steps Before Day 17

- [ ] **Phỏng vấn 10 nhà đầu tư cá nhân** (20 phút mỗi người) — focus vào Unknown #1
- [ ] **Test accuracy thủ công:** Lấy 5 báo cáo BCTC thực tế, dùng Claude API phân tích, tự đánh giá kết quả
- [ ] **Competitor research:** Search kỹ trước khi tiếp tục
- [ ] **Decision:** Nếu 6/10 confirm WTP → build MVP. Nếu không → rethink pricing hoặc pivot use case.
