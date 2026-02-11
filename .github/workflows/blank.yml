flowchart TB
  %% =========================
  %% A-R-SAT: OJS Analysis Map
  %% =========================
  classDef title fill:#111827,color:#fff,stroke:#111827,stroke-width:1px;
  classDef block fill:#F8FAFC,stroke:#CBD5E1,stroke-width:1px,color:#0F172A;
  classDef author fill:#EEF2FF,stroke:#6366F1,stroke-width:1px,color:#0F172A;
  classDef reviewer fill:#ECFDF5,stroke:#10B981,stroke-width:1px,color:#0F172A;
  classDef ai fill:#FFF7ED,stroke:#F59E0B,stroke-width:1px,color:#0F172A;
  classDef stat fill:#FFFFFF,stroke:#94A3B8,stroke-width:1px,color:#0F172A,stroke-dasharray: 4 3;

  T["BẢN ĐỒ PHÂN TÍCH DỮ LIỆU KHẢO SÁT OJS (A–R–AI)"]:::title

  T --> P1["BƯỚC 1. Tiền xử lý dữ liệu (Clean & Code)"]:::block
  P1 --> P1a["Chuẩn hoá biến: A_ / R_ (không trùng mã)"]:::stat
  P1 --> P1b["Likert 1–5 → Numeric; Missing → NA"]:::stat
  P1 --> P1c["Multiple response → tách biến nhị phân (0/1)"]:::stat
  P1 --> P1d["Kiểm tra dữ liệu: missing, outliers, kiểu biến (Scale/Ordinal/Nominal)"]:::stat

  T --> P2["BƯỚC 2. Kiểm định thang đo (Reliability)"]:::block
  P2 --> P2a["Cronbach’s Alpha (α) cho từng thang đo"]:::stat
  P2 --> P2b["Item-rest correlation; α if item dropped"]:::stat
  P2 --> P2c["Xử lý biến lệch chiều / tương quan âm (tách riêng hoặc đảo chiều nếu cần)"]:::stat

  T --> P3["BƯỚC 3. Thống kê mô tả & Chỉ số hài lòng (Descriptives & Index)"]:::block
  P3 --> P3a["Mean, Median, SD, Min–Max, Valid/Missing"]:::stat
  P3 --> P3b["Tạo chỉ số hài lòng: A_SI và R_SI (mean các biến Likert lõi)"]:::stat
  P3 --> P3c["Phân tích câu hỏi mở: nhóm chủ đề (themes) + trích dẫn minh hoạ"]:::stat

  T --> P4["BƯỚC 4. So sánh nhóm (Inferential)"]:::block
  P4 --> P4a["Mann–Whitney U: so sánh A_SI vs R_SI"]:::stat
  P4 --> P4b["Báo cáo: U, p, effect size (rank-biserial r) + descriptives theo nhóm"]:::stat

  %% =========================
  %% AUTHOR BRANCH
  %% =========================
  T --> A0["NHÁNH A — TÁC GIẢ (Author)"]:::author
  A0 --> A1["Biến nền (không đưa vào SI)"]:::author
  A1 --> A1a["A_Institution (Nominal)"]:::author
  A1 --> A1b["A_Submit_Freq (Ordinal)"]:::author

  A0 --> A2["Thang đo Likert 1–5 (đưa vào A_SI)"]:::author
  A2 --> A2a["Usability: A_EaseUse, A_LoginConv, A_SubmitClarity, A_UI_GuideSat"]:::author
  A2 --> A2b["Review quality: A_RevObj, A_RevEff"]:::author
  A2 --> A2c["System efficiency: A_AutoEmail, A_ProcTime"]:::author

  A0 --> A3["Biến đối chiếu (không trộn vào SI)"]:::author
  A3 --> A3a["A_OverallSat (Likert 1–5)"]:::author

  A0 --> A4["Câu hỏi mở / nhiều lựa chọn"]:::author
  A4 --> A4a["A_PainPoints_Text (Text)"]:::author
  A4 --> A4b["A_Suggestions_Text (Text)"]:::author
  A4 --> A4c["A_FeatureWish_MR (Multiple response) → 0/1 theo lựa chọn"]:::author

  %% =========================
  %% REVIEWER BRANCH
  %% =========================
  T --> R0["NHÁNH R — PHẢN BIỆN (Reviewer)"]:::reviewer
  R0 --> R1["Biến nền"]:::reviewer
  R1 --> R1a["R_Freq, R_Age (Ordinal); R_Gen (Nominal)"]:::reviewer

  R0 --> R2["Thang đo Likert 1–5 (đưa vào R_SI)"]:::reviewer
  R2 --> R2a["Invite process: R_IQ, R_MF, R_DT, R_IR, R_RR"]:::reviewer
  R2 --> R2b["Usability: R_LA, R_IU, R_FH"]:::reviewer
  R2 --> R2c["Review support: R_FC, R_AN, R_DR"]:::reviewer
  R2 --> R2d["Editorial comm.: R_EC"]:::reviewer

  R0 --> R3["Biến quy trình có thể phân tích riêng"]:::reviewer
  R3 --> R3a["R_RD (ReviewDuration) — nếu tương quan âm: tách riêng, không gộp R_SI"]:::reviewer

  R0 --> R4["Câu hỏi mở"]:::reviewer
  R4 --> R4a["R_PP (PainPoints_Text)"]:::reviewer
  R4 --> R4b["R_RS (Suggestions_Text)"]:::reviewer

  %% =========================
  %% AI BRANCH (Reviewer)
  %% =========================
  T --> AI0["NHÁNH AI — ỨNG DỤNG AI TRONG PHẢN BIỆN"]:::ai
  AI0 --> AI1["Mức độ sử dụng AI (Ordinal)"]:::ai
  AI1 --> AI1a["R_AU: 0%–25%–50%–75%–100% (mã 1–5)"]:::ai

  AI0 --> AI2["Công cụ AI (Text)"]:::ai
  AI2 --> AI2a["R_AT: tên công cụ + phân nhóm thủ công (ChatGPT, Gemini, Copilot...)"]:::ai

  AI0 --> AI3["Nhận định AI dạng chọn nhiều (Multiple response)"]:::ai
  AI3 --> AI3a["Tách 6 biến nhị phân 0/1: R_AI_Q1...R_AI_Q6"]:::ai
  AI3 --> AI3b["Tạo chỉ số: Benefit_Count (Q1,Q3,Q6) & Risk_Count (Q2,Q4,Q5)"]:::ai

  AI0 --> AI4["Phân tích AI"]:::ai
  AI4 --> AI4a["Frequencies (%) cho từng lựa chọn 0/1"]:::ai
  AI4 --> AI4b["Liên hệ: R_AU với Benefit/Risk (Spearman/Descriptives)"]:::ai
