# Tasks: [FEATURE NAME]

**Input**: Design documents from `/specs/[###-feature-name]/`
**Prerequisites**: plan.md (required), research.md, data-model.md, contracts/

## Execution Flow (main)

```text
1. Load plan.md from feature directory
   → If not found: ERROR "No implementation plan found"
   → Extract: tech stack, libraries, structure
2. Load optional design documents:
   → data-model.md: Extract entities → model tasks
   → contracts/: Each file → contract test task
   → research.md: Extract decisions → setup tasks
3. Generate tasks by category:
   → Setup: project init, dependencies, linting
   → Tests: contract tests, integration tests
   → Core: models, services, CLI commands
   → Integration: DB, middleware, logging
   → Polish: unit tests, performance, docs
4. Apply task rules:
   → Different files = mark [P] for parallel
   → Same file = sequential (no [P])
   → Tests before implementation (TDD)
5. Number tasks sequentially (T001, T002...)
6. Generate dependency graph
7. Create parallel execution examples
8. Validate task completeness:
   → All contracts have tests?
   → All entities have models?
   → All endpoints implemented?
# 任務清單（Tasks）：[FEATURE NAME]

**輸入**：來自 `/specs/[###-feature-name]/` 的設計文件
**前置條件**：需有 plan.md（必要）、research.md、data-model.md、contracts/

## 執行流程（main）

```text
1. 從功能資料夾載入 plan.md
   → 若找不到：ERROR "No implementation plan found"
   → 從 plan.md 擷取技術棧、套件與結構資訊
2. 載入可選設計文件：
   → data-model.md：擷取實體並產生 model 任務
   → contracts/：每個契約檔案產生契約測試任務
   → research.md：擷取決策並建立相關設定任務
3. 依類別生成任務：
   → 設定（Setup）：專案初始化、相依、lint 設定
   → 測試（Tests）：契約測試、整合測試
   → 核心（Core）：models、services、CLI
   → 整合（Integration）：DB、middleware、日誌
   → 打磨（Polish）：單元測試、效能、文件
4. 套用任務規則：
   → 不同檔案 = 標為 [P]（可平行）
   → 同一檔案 = 順序執行（不可標 [P]）
   → 測試需先於實作（TDD）
5. 為任務編號（T001、T002…）
6. 產生相依圖
7. 建立平行執行範例
8. 驗證任務完整性：
   → 所有契約是否都有測試？
   → 所有實體是否有 model？
   → 所有端點是否覆蓋？
9. 回傳：SUCCESS（任務已準備好執行）
```

## 格式：`[ID] [P?] 說明`

- **[P]**：可平行執行（不同檔案、無相依）

- 任務說明中需包含精確檔案路徑

## 路徑約定

- **單一專案**：`src/`、`tests/` 放在專案根目錄

- **Web 應用**：`backend/src/`、`frontend/src/`

- **Mobile**：`api/src/`、`ios/src/` 或 `android/src/`

## Phase 3.1：設定

- [ ] T001 建立專案結構（依實作計畫）

- [ ] T002 初始化 [language] 專案與 [framework] 相依

- [ ] T003 [P] 設定 lint 與格式化工具

## Phase 3.2：先寫測試（TDD） ⚠ 必須在 3.3 之前完成

重要：測試必須先寫且必須先失敗

- [ ] T004 [P] 契約測試 POST /api/users（tests/contract/test_users_post.py）
- [ ] T005 [P] 契約測試 GET /api/users/{id}（tests/contract/test_users_get.py）
- [ ] T006 [P] 整合測試：使用者註冊（tests/integration/test_registration.py）
- [ ] T007 [P] 整合測試：驗證流程（tests/integration/test_auth.py）

## Phase 3.3：核心實作（僅在測試失敗後）

- [ ] T008 [P] 建立 User model（src/models/user.py）

- [ ] T009 [P] 建立 UserService CRUD（src/services/user_service.py）

- [ ] T010 [P] CLI --create-user（src/cli/user_commands.py）

- [ ] T011 實作 POST /api/users 端點

- [ ] T012 實作 GET /api/users/{id} 端點

- [ ] T013 輸入驗證

- [ ] T014 錯誤處理與日誌

## Phase 3.4：整合

- [ ] T015 將 UserService 連接資料庫

- [ ] T016 身份驗證中介軟體

- [ ] T017 請求/回應日誌

- [ ] T018 CORS 與安全標頭

## Phase 3.5：打磨

- [ ] T019 [P] 單元測試（驗證）

- [ ] T020 效能測試（<200ms）

- [ ] T021 [P] 更新文件（docs/api.md）

- [ ] T022 移除重複

- [ ] T023 執行手動測試清單

## 依賴關係
- 測試（T004-T007）必須在實作（T008-T014）之前
- T008 會阻塞 T009、T015
- T016 會阻塞 T018
- 實作完成後進行打磨（T019-T023）

## 平行執行範例

```text
# 同時啟動 T004-T007：
Task: "契約測試 POST /api/users（tests/contract/test_users_post.py）"
Task: "契約測試 GET /api/users/{id}（tests/contract/test_users_get.py）"
Task: "整合測試：註冊（tests/integration/test_registration.py）"
Task: "整合測試：驗證（tests/integration/test_auth.py）"
```

## 備註

- [P] 任務 = 不同檔案、無相依

- 請先確認測試失敗再開始實作

- 每完成任務後請提交

- 避免：模糊任務或同一檔案的 [P] 任務衝突

## 任務產生規則

（保留原意，已翻譯）

## 驗證檢查表

門檻：由 main() 在回傳前檢查

- [ ] 所有契約均有對應測試
- [ ] 所有實體均有 model 任務
- [ ] 所有測試先於實作
- [ ] 平行任務確實獨立
- [ ] 每個任務指定精確檔案路徑
- [ ] 無兩個 [P] 任務修改相同檔案

> 憲法對齊：產生任務時，請確保包含資料分類、最小權限審查、秘密處理與安全事件的可觀測性/日誌任務。
