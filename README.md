# PM 工具手冊（繁體中文通用版）

給任何產業 PM / PO 用的方法參考手冊：產品探索、產品策略、backlog item 訪談與策略提案對練、商業提案寫法。全部範例都是中性情境（SaaS、電商等）。

## 內容

| 檔案 | 內容 | 來源 |
|---|---|---|
| [01-product-discovery.md](01-product-discovery.md) | 發想、假設辨識與排序、實驗設計、功能優先序、需求分流、Opportunity Solution Tree、訪談腳本與摘要、指標儀表板 | 改寫自 [phuryn/pm-skills](https://github.com/phuryn/pm-skills)（MIT） |
| [02-product-strategy.md](02-product-strategy.md) | 產品願景、Strategy Canvas、Startup / Lean / Business Model Canvas、價值主張、變現與定價、SWOT、PESTLE、五力、Ansoff | 改寫自 [phuryn/pm-skills](https://github.com/phuryn/pm-skills)（MIT） |
| [03-po-interview-and-sparring.md](03-po-interview-and-sparring.md) | 五題 backlog item 訪談與一致性檢查；策略提案對練的 6 個階段、數字檢查清單、主管提問題庫與模板 | 整理自作者任職公司對外開放的 PO 工具方法 |
| [04-business-proposal.md](04-business-proposal.md) | 商業提案寫法、可複製的模板、商業模式圖、數字估算、簡報結構與送出前的自我檢查 | 整理自公開框架（原創整理） |

## 建議使用順序

1. **探索問題**：01 的 discover、interview → opportunity-solution-tree
2. **定方向**：02 的 strategy、market-scan；03 的 Direction Sparring
3. **寫提案**：04 的模板與逐節教學；用 01 的 identify-assumptions 找出未驗證的假設
4. **寫 item**：03 的 Item Interview
5. **追蹤成效**：01 的 metrics-dashboard

## 想在 Claude Code 直接使用 skill？

01、02 是原 skill 的中文參考手冊，不是可安裝的 plugin。文中的 `/discover`、`/strategy` 等指令，要安裝原版 skill 才能執行：

```
/plugin marketplace add phuryn/pm-skills
```

沒有安裝的話，把每一節當成流程與檢查清單閱讀即可。

## 出處與授權

- 01、02 改寫自 Pawel Huryn 的 [pm-skills](https://github.com/phuryn/pm-skills)（MIT License）。修改內容：翻譯為繁體中文、改寫為手冊格式、範例改為中性情境、移除品牌範例與外部連結。
- 03 整理自作者任職公司對外開放的 PO 工具方法，**不在本 repo 的 MIT 授權範圍內**，轉載請保留出處。
- 04 為作者依公開框架整理的原創內容，引用出處列於該檔文末。
- 文中提到的框架名稱與作者（例如 Marty Cagan 的四大產品風險、Teresa Torres 的 Opportunity Solution Tree、Osterwalder 的 Business Model Canvas、Ash Maurya 的 Lean Canvas）僅作出處引用。Business Model Canvas 與 Lean Canvas 本身以 CC BY-SA 授權，使用其畫布時請標示原作者。
- 除 03 外，本 repo 以 MIT License 釋出，詳見 [LICENSE](LICENSE)。
