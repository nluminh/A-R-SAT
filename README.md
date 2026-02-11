flowchart TB
  %% =========================================
  %% A-R-AI: OJS DATA ANALYSIS MAP (Academic)
  %% =========================================

  classDef title fill:#0B1F3B,color:#ffffff,stroke:#0B1F3B,stroke-width:1px;
  classDef step fill:#F7F9FC,color:#0B1F3B,stroke:#B8C7E0,stroke-width:1px;
  classDef author fill:#EEF5FF,color:#0B1F3B,stroke:#6B8EF2,stroke-width:1px;
  classDef reviewer fill:#ECFDF5,color:#0B1F3B,stroke:#10B981,stroke-width:1px;
  classDef ai fill:#FFF7ED,color:#0B1F3B,stroke:#FB923C,stroke-width:1px;
  classDef out fill:#FFFFFF,color:#0B1F3B,stroke:#94A3B8,stroke-width:1px,stroke-dasharray: 4 3;

  T["BẢN ĐỒ PHÂN TÍCH DỮ LIỆU KHẢO SÁT OJS<br/>(AUTHOR – REVIEWER – AI)"]:::title

  %% ---------- STAGE 1 ----------
  S1["Bước 1. Tiền xử lý dữ liệu (Clean & Code)"]:::step
  S1a["Chuẩn hoá mã biến: A_ / R_ (không trùng)"]:::out
  S1b["Likert 1–5 → Numeric; Missing → NA"]:::out
  S1c["Multiple response → tách biến nhị phân 0/1"]:::out
  S1d["Kiểm tra dữ liệu: missing, kiểu biến (Scale/Ordinal/Nominal)"]:::out

  %% ---------- STAGE 2 ----------
  S2["Bước 2. Kiểm định độ tin cậy thang đo"]:::step
  S2a["Cronbach’s Alpha (A_ thang đo tác giả)"]:::out
  S2b["Cronbach’s Alpha (R_ thang đo phản biện)"]:::out
  S2c["Xử lý biến lệch chiều (nếu có): loại khỏi chỉ số hài lòng và báo cáo riêng"]:::out

  %% ---------- STAGE 3 ----------
  S3["Bước 3. Tạo chỉ số tổng hợp"]:::step
  S3a["A_SI = mean(A_EU, A_LC, A_SC, A_IG, A_RO, A_RE, A_AE, A_PT)"]:::out
  S3b["R_SI = mean(các biến Likert cốt lõi của phản biện; loại biến nghịch chiều nếu cần)"]:::out

  %% ---------- STAGE 4 ----------
  S4["Bước 4. Thống kê mô tả & Báo cáo"]:::step
  S4a["Mean, SD, Median, Min–Max cho từng biến & chỉ số (A_SI / R_SI)"]:::out
  S4b["Frequencies (%) cho biến nền (tuổi, tần suất, giới tính, v.v.)"]:::out

  %% ---------- STAGE 5 ----------
  S5["Bước 5. So sánh nhóm & Diễn giải"]:::step
  S5a["Mann–Whitney U: so sánh A_SI vs R_SI (U, p, effect size)"]:::out
  S5b["Diễn giải theo bối cảnh vận hành OJS + đối chiếu dữ liệu hệ thống (log)"]:::out

  %% ---------- BRANCH: AUTHOR ----------
  subgraph AUTHOR["NHÁNH A — TÁC GIẢ (Author)"]:::author
    A1["Thang đo trải nghiệm sử dụng (Likert 1–5)"]:::author
    A1a["Usability: A_EU, A_LC, A_SC, A_IG"]:::author
    A1b["Review Quality: A_RO, A_RE"]:::author
    A1c["System Efficiency: A_AE, A_PT"]:::author
    A2["Biến đối chiếu: A_OS (Overall Satisfaction)"]:::author
    A3["Câu hỏi mở: A_PP (Pain points), A_SG (Suggestions)"]:::author
    A4["Nhiều lựa chọn: A_FW (Feature wish) → tách 0/1 theo từng lựa chọn"]:::author
  end

  %% ---------- BRANCH: REVIEWER ----------
  subgraph REVIEWER["NHÁNH R — PHẢN BIỆN (Reviewer)"]:::reviewer
    R1["Quy trình mời & tiếp nhận (Likert 1–5)"]:::reviewer
    R1a["R_IQ, R_MF, R_DT, R_IR, R_RR"]:::reviewer
    R2["Usability khi phản biện (Likert 1–5)"]:::reviewer
    R2a["R_LA, R_IU, R_FH"]:::reviewer
    R3["Hỗ trợ phản biện (Likert 1–5)"]:::reviewer
    R3a["R_FC, R_AN, R_DR"]:::reviewer
    R4["Liên lạc (Likert 1–5)"]:::reviewer
    R4a["R_EC"]:::reviewer
    R5["Chỉ báo quy trình: R_RD (nếu nghịch chiều → báo cáo riêng)"]:::reviewer
    R6["Câu hỏi mở: R_PP (vướng mắc), R_RS (đề xuất)"]:::reviewer
  end

  %% ---------- BRANCH: AI ----------
  subgraph AISEC["NHÁNH AI — ỨNG DỤNG AI TRONG PHẢN BIỆN"]:::ai
    AI1["Mức độ dùng AI: R_AU (Ordinal 1–5)"]:::ai
    AI2["Công cụ AI: R_AT (Text) → phân nhóm thủ công (ChatGPT, Gemini, Copilot...)"]:::ai
    AI3["Quan điểm AI dạng chọn nhiều: R_AP (Multiple response)"]:::ai
    AI3a["Tách 6 biến nhị phân 0/1: R_AI_Q1…R_AI_Q6"]:::ai
    AI3b["Chỉ số phụ: Benefit_Count (Q1,Q3,Q6) & Risk_Count (Q2,Q4,Q5)"]:::ai
    AI4["Thống kê: Frequencies (%) cho từng lựa chọn 0/1"]:::ai
  end

  %% ---------- FLOW ----------
  T --> S1 --> S2 --> S3 --> S4 --> S5
  S1 --> AUTHOR
  S1 --> REVIEWER
  S1 --> AISEC
  S3 --> AUTHOR
  S3 --> REVIEWER
  S4 --> AISEC
