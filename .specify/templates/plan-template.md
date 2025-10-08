# Implementation Plan: [FEATURE]

**Branch**: `[###-feature-name]` | **Date**: [DATE] | **Spec**: [link]
**Input**: Feature specification from `/specs/[###-feature-name]/spec.md`

## Execution Flow (/plan command scope)

```text
1. Load feature spec from Input path
   → If not found: ERROR "No feature spec at {path}"
2. Fill Technical Context (scan for NEEDS CLARIFICATION)
   → Detect Project Type from file system structure or context (web=frontend+backend, mobile=app+api)
   → Set Structure Decision based on project type
# 實作計畫（Implementation Plan）：[FEATURE]

**分支**：`[###-feature-name]` | **日期**： [DATE] | **規格**： [link]
**輸入**：來自 `/specs/[###-feature-name]/spec.md` 的功能規格

## 執行流程（/plan 指令範圍）

```text
1. 從輸入路徑載入功能規格
   → 若未找到：ERROR "No feature spec at {path}"
2. 填寫技術脈絡（檢查是否存在 NEEDS CLARIFICATION）
   → 從檔案系統結構或上下文判定專案類型（web = frontend + backend、mobile = app + api）
   → 根據專案類型決定結構方案
3. 根據憲法檔案內容填寫「憲法檢查」章節。
4. 評估下方的憲法檢查
   → 若存在違規：記錄於 Complexity Tracking
   → 若無法合理說明：ERROR "Simplify approach first"
   → 更新進度追蹤：Initial Constitution Check
5. 執行 Phase 0 → research.md
   → 若仍有 NEEDS CLARIFICATION：ERROR "Resolve unknowns"
6. 執行 Phase 1 → contracts、data-model.md、quickstart.md、以及 agent 專用檔（例如 `CLAUDE.md`、`.github/copilot-instructions.md`、`GEMINI.md`、`QWEN.md` 或 `AGENTS.md`）
7. 重新評估憲法檢查
   → 若出現新違規：回到 Phase 1 重新設計
   → 更新進度追蹤：Post-Design Constitution Check
8. 規劃 Phase 2 → 描述任務產生方式（請勿在 /plan 內建立 tasks.md）
9. 停止（STOP）— 準備執行 /tasks 指令
```

**重要**：/plan 指令在第 7 步停止。Phase 2-4 由其他指令執行：

- Phase 2：/tasks 會建立 tasks.md

- Phase 3-4：實作執行（手動或工具）

## 摘要

[從功能規格擷取：主要需求與研究後的技術方法]

## 技術脈絡

**語言/版本**：例如 Python 3.11、Swift 5.9、Rust 1.75 或 NEEDS CLARIFICATION
**主要相依**：例如 FastAPI、UIKit、LLVM 或 NEEDS CLARIFICATION
**儲存**：視情況（例如 PostgreSQL、CoreData、檔案或 N/A）
**測試**：例如 pytest、XCTest、cargo test 或 NEEDS CLARIFICATION
**目標平台**：例如 Linux server、iOS 15+、WASM 或 NEEDS CLARIFICATION
**專案類型**：single / web / mobile（決定原始碼結構）
**效能目標**：例如 1000 req/s、10k lines/sec、60 fps 或 NEEDS CLARIFICATION
**限制條件**：例如 <200ms p95、<100MB 記憶體、離線能力或 NEEDS CLARIFICATION
**規模/範圍**：例如 10k 使用者、1M LOC、50 個畫面或 NEEDS CLARIFICATION

## 憲法檢查

*門檻（GATE）：必須在 Phase 0 研究前通過；Phase 1 設計後再複查。*

[以憲法文件決定的門檻]

憲法檢查（以資安為主）：
- 驗證是否宣告資料分類（public/internal/confidential）。
- 驗證是否描述所需的加密與秘密管理。
- 驗證是否考量自動化或服務帳號的存取控制 / 最小權限。
- 驗證是否包含對安全敏感事件的可觀測性需求。

## 專案結構

### 文件（此功能）

```text
specs/[###-feature]/
├── plan.md              # 此檔（/plan 指令輸出）
├── research.md          # Phase 0 輸出（/plan 指令）
├── data-model.md        # Phase 1 輸出（/plan 指令）
├── quickstart.md        # Phase 1 輸出（/plan 指令）
├── contracts/
└── tasks.md             # Phase 2 輸出（/tasks 指令 — /plan 不建立）
```

### 程式碼（專案根目錄）

<!--
  動作：請用此專案的實際結構取代下列範例，刪除未使用的選項，並以實際路徑替換。
-->

```text
# 選項 1：單一專案（預設）
src/
  ├── models/
  ├── services/
  ├── cli/
  └── lib/

tests/
  ├── contract/
  ├── integration/
  └── unit/

# 選項 2：Web 應用（當偵測到 frontend + backend）
backend/
  └── src/
      ├── models/
      ├── services/
      └── api/
frontend/
  └── src/
      ├── components/
      ├── pages/
      └── services/

# 選項 3：Mobile + API（當偵測到 iOS/Android）
api/
  (同 backend 結構)
ios/ 或 android/
  (平台相關結構：feature modules、UI flows、platform tests)
```

**結構決策**：請描述選擇的結構並指出實際路徑。

## Phase 0：大綱與研究

1. 從技術脈絡擷取未知項目：
   - 對每個 NEEDS CLARIFICATION 建立 research 任務
   - 對每個相依建立最佳實務研究任務
   - 對每個整合建立 patterns 任務

2. 指派研究代理：

```text
   對於每個技術未知項：
      任務:"為 {feature context} 研究 {unknown}"
   對於每個技術選擇：
      任務:"尋找 {tech} 在 {domain} 的最佳實務"
```

3. 將研究結果彙整於 `research.md`：

   - 決策：選擇內容
   - 理由：為何選擇
   - 待考量方案：其他被評估的選擇
   - 決策：選擇內容
   - 理由：為何選擇
   - 待考量方案：其他被評估的選擇

輸出：research.md（解決所有 NEEDS CLARIFICATION）

## Phase 1：設計與契約

### 前提

research.md 完成

1. 從規格擷取實體（entities）→ data-model.md：

   1. 實體名稱、欄位、關聯
   2. 由需求衍生的驗證規則
   3. 若適用，紀錄狀態轉換

2. 從功能需求產生 API 契約：
   - 每個使用者動作對應一個端點
   - 使用標準 REST/GraphQL 模式
   - 輸出 OpenAPI/GraphQL schema 至 `/contracts/`

3. 從契約產生契約測試：
   - 每個端點一個測試檔
   - 驗證 request/response schema
   - 測試必須先失敗（尚未實作）

（其餘內容保留原意，文字已翻譯）
   
   Run `.specify/scripts/powershell/update-agent-context.ps1 -AgentType copilot`
  
