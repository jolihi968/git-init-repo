# Feature Specification: [FEATURE NAME]

**Feature Branch**: `[###-feature-name]`  
**Created**: [DATE]  
**Status**: Draft  
**Input**: User description: "$ARGUMENTS"

## Execution Flow (main)

```text
1. Parse user description from Input
   → If empty: ERROR "No feature description provided"
2. Extract key concepts from description
   → Identify: actors, actions, data, constraints
3. For each unclear aspect:
   → Mark with [NEEDS CLARIFICATION: specific question]
4. Fill User Scenarios & Testing section
   → If no clear user flow: ERROR "Cannot determine user scenarios"
5. Generate Functional Requirements
   → Each requirement must be testable
   → Mark ambiguous requirements
6. Identify Key Entities (if data involved)
7. Run Review Checklist
   → If any [NEEDS CLARIFICATION]: WARN "Spec has uncertainties"
   → If implementation details found: ERROR "Remove tech details"
# 功能規格（Feature Specification）：[FEATURE NAME]

**功能分支**：`[###-feature-name]`  
**建立時間**： [DATE]  
**狀態**：草案（Draft）  
**輸入**：使用者描述："$ARGUMENTS"

## 執行流程（main）

```text
1. 解析輸入中的使用者描述
   → 若為空：ERROR "No feature description provided"
2. 擷取描述中的關鍵概念
   → 辨識：actors、actions、data、constraints
3. 對於每個不明確的面向：
   → 標記為 [NEEDS CLARIFICATION: specific question]
4. 填寫使用者情境與測試章節
   → 若無明確使用者流程：ERROR "Cannot determine user scenarios"
5. 產生功能性需求
   → 每一項需求必須可測試
   → 標示含糊的需求
6. 若有資料相關，辨識主要實體（Key Entities）
7. 執行審查檢查表
   → 若仍有 [NEEDS CLARIFICATION]：WARN "Spec has uncertainties"
   → 若包含實作細節：ERROR "Remove tech details"
8. 回傳：SUCCESS（規格可進入規劃）
```

---

## ⚡ 快速指引

- ✅ 專注於使用者需要的 WHAT 與 WHY

- ❌ 避免 HOW 層面的實作細節（例如語言、框架、API 結構）

- 👥 文件面向業務或非技術利害關係人

### 章節要求

- **必填章節**：每個功能規格都必須完成

- **選填章節**：僅在相關時包含

- 若某章節不適用，請直接移除（不要留下 "N/A"）

> 憲法對齊：請確保規格聲明資料分類、最小權限考量，並包含對安全事件之可觀測性/日誌需求。
### AI 生成建議

當由使用者提示產生此規格時：

1. **標示所有模糊處**：使用 [NEEDS CLARIFICATION: specific question]

2. **避免臆測**：若提示未說明（例如未指定驗證方式），應標記而非假設

3. **以測試者角度思考**：每一個模糊的需求都應該不通過「可測試與明確」檢查

4. **常見未指定項目**：

   - 使用者類型與權限

   - 資料保留 / 刪除政策

   - 效能與規模目標

   - 錯誤處理行為

   - 整合需求

   - 安全 / 合規需求

---

[## 使用者情境與測試（必填）

### 主要使用者故事
[以自然語言描述主要使用者流程]

### 驗收情境

1. **Given** [初始狀態], **When** [操作], **Then** [預期結果]

2. **Given** [初始狀態], **When** [操作], **Then** [預期結果]

### 邊界情境

- 當 [邊界條件] 發生時系統如何處理？

- 系統如何處理 [錯誤情境]？

## 需求（必填）

### 功能性需求

- **FR-001**：系統必須 [例如：允許使用者建立帳號]

- **FR-002**：系統必須 [例如：驗證電子郵件]

- **FR-003**：使用者必須能 [例如：重置密碼]

- **FR-004**：系統必須 [例如：儲存使用者偏好]

- **FR-005**：系統必須 [例如：記錄所有安全相關事件]

*若需標示不清楚的需求：*

- **FR-006**：系統必須使用何種驗證方式 [NEEDS CLARIFICATION: email/password、SSO、OAuth?]

- **FR-007**：系統應保留使用者資料多久 [NEEDS CLARIFICATION: 保留期間未指定]

### 主要實體（若功能牽涉資料）

- **[Entity 1]**：代表什麼，主要屬性（不含實作）

- **[Entity 2]**：代表什麼，與其他實體的關係

---

## 審查與驗收檢查表

門檻（GATE）：於 main() 執行期間自動檢查

### 內容品質

- [ ] 無實作細節（不包含語言、框架、API）

- [ ] 聚焦使用者價值與業務需求

- [ ] 以非技術利害關係人為撰寫對象

- [ ] 所有必填章節已完成

### 需求完整性

- [ ] 無 [NEEDS CLARIFICATION] 標示

- [ ] 需求可測試且明確

- [ ] 成功標準可量化

- [ ] 範圍明確

- [ ] 相依與假設已列出

---

## 執行狀態

(於 main() 執行時更新)

- [ ] 已解析使用者描述
- [ ] 已擷取關鍵概念
- [ ] 已標示模糊處
- [ ] 已定義使用者情境
- [ ] 已產生需求
- [ ] 已辨識實體
- [ ] 已通過審查檢查表

---
