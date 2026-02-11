---
config:
  layout: elk
---
flowchart LR

%% =========================
%% ROOT
%% =========================
A["PHÂN TÍCH DỮ LIỆU ĐÁNH GIÁ OJS<br/>(Tác giả – Phản biện – AI)"]:::root

%% =========================
%% STAGE 0: DATA PREP
%% =========================
A --> P["TIỀN XỬ LÝ DỮ LIỆU<br/>(Clean & Code)"]:::gray
P --> P1["Chuẩn hoá mã biến: A_ / R_ (không trùng)"]:::gray
P --> P2["Likert 1–5 → Numeric; Missing → NA"]:::gray
P --> P3["Multiple response → tách biến nhị phân (0/1)"]:::gray
P --> P4["Kiểm tra dữ liệu: thiếu, ngoại lệ, kiểu biến (Scale/Ordinal/Nominal)"]:::gray

%% =========================
%% BRANCH 1: AUTHOR
%% =========================
P --> AU["NHÁNH 1: TÁC GIẢ (AUTHOR)"]:::author
AU --> AU1["Kiểm định độ tin cậy thang đo (Cronbach’s α)"]:::author
AU --> AU2["Thống kê mô tả các biến A_* (Mean/Median/SD/IQR/Min–Max)"]:::author
AU --> AU3["Tạo chỉ số A_SI (Satisfaction Index)"]:::author
AU --> AU4["Phân tích câu hỏi mở: A_PainPoints_Text, A_Suggestions_Text"]:::author
AU --> AU5["Tần suất đa phản hồi: A_FeatureWish (tách 0/1; % chọn)"]:::author

%% =========================
%% BRANCH 2: REVIEWER
%% =========================
P --> RV["NHÁNH 2: PHẢN BIỆN (REVIEWER)"]:::reviewer
RV --> RV1["Kiểm định độ tin cậy thang đo (Cronbach’s α)"]:::reviewer
RV --> RV2["Xử lý biến nghịch chiều (nếu có): kiểm tra item-rest corr; loại khỏi chỉ số nếu cần"]:::reviewer
RV --> RV3["Thống kê mô tả các biến R_* (Mean/Median/SD/IQR/Min–Max)"]:::reviewer
RV --> RV4["Tạo chỉ số R_SI (Satisfaction Index)"]:::reviewer
RV --> RV5["Phân tích câu hỏi mở: R_PP (Pain points), R_RS (Suggestions)"]:::reviewer

%% =========================
%% BRANCH 3: AI (reviewer-focused)
%% =========================
P --> AI["NHÁNH 3: AI TRONG PHẢN BIỆN"]:::ai
AI --> AI1["Mức độ sử dụng AI: R_AU (Ordinal 1–5)"]:::ai
AI --> AI2["Công cụ AI sử dụng: R_AT (Text → nhóm thủ công)"]:::ai
AI --> AI3["AI Multiple (đa lựa chọn) → tách 6 biến 0/1: R_AI_Q1 … R_AI_Q6"]:::ai
AI --> AI4["Tính chỉ số: R_AI_Benefit_Count (Q1,Q3,Q6) & R_AI_Risk_Count (Q2,Q4,Q5)"]:::ai
AI --> AI5["Thống kê % chọn từng phát biểu AI + mô tả Benefit/Risk"]:::ai

%% =========================
%% CROSS-BRANCH: GROUP COMPARISON
%% =========================
AU3 --> COMP["SO SÁNH NHÓM"]:::green
RV4 --> COMP
COMP --> COMP1["Mann–Whitney U: so sánh A_SI vs R_SI<br/>(U, Z, p; effect size r)"]:::green

%% =========================
%% OPTIONAL EXTENSIONS
%% =========================
COMP --> EXT["PHÂN TÍCH MỞ RỘNG (tuỳ chọn)"]:::purple
EXT --> EXT1["Tương quan (Spearman): R_AU với R_AI_Benefit/Risk"]:::purple
EXT --> EXT2["So sánh theo nhóm tuổi/kinh nghiệm (nếu đủ mẫu)"]:::purple

%% =========================
%% STYLES
%% =========================
classDef root fill:#f5f5f5,stroke:#607d8b,stroke-width:2px,color:#37474f,font-weight:bold;
classDef gray fill:#ffffff,stroke:#90a4ae,stroke-width:1.5px,color:#37474f;
classDef author fill:#E3F2FD,stroke:#1565C0,stroke-width:2px,color:#0D47A1;
classDef reviewer fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px,color:#1B5E20;
classDef ai fill:#FFF8E1,stroke:#FF8F00,stroke-width:2px,color:#E65100;
classDef green fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px,color:#1B5E20,font-weight:bold;
classDef purple fill:#F3E5F5,stroke:#7B1FA2,stroke-width:2px,color:#4A148C;
