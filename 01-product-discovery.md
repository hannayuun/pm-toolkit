# PM 工具手冊（通用版）01 — Product Discovery 產品探索

> 適用任何產業的 PM。內容涵蓋：發想、實驗設計、假設辨識與排序、功能排序、需求分流、使用者訪談、指標儀表板。
> 方法來源為公開的產品管理框架（括號內為框架出處，僅作引用）。所有範例皆為中性示意。

## 總表

| 名稱 | 類型 | 用途 | 何時用 |
|---|---|---|---|
| brainstorm-ideas-existing | Skill | 以 PM / Designer / Engineer 三視角為既有產品發想點子，選出前 5 名 | 既有產品的持續探索、針對已知機會找解法 |
| brainstorm-ideas-new | Skill | 以三視角為新產品發想功能點子，選出前 5 名 | 新產品初期探索、新創點子功能發想 |
| brainstorm-experiments-existing | Skill | 為既有產品設計低成本驗證實驗 | 要驗證假設、在全面開發前便宜地測試功能 |
| brainstorm-experiments-new | Skill | 為新產品寫 XYZ 假設並設計 pretotype 實驗 | 驗證新產品點子、測試市場需求 |
| identify-assumptions-existing | Skill | 用唱反調視角找出既有產品功能在 4 大風險的假設 | 壓力測試功能點子、做風險評估 |
| identify-assumptions-new | Skill | 找出新產品在 8 大風險類別的假設 | 評估新創/新產品風險、建立假設地圖 |
| prioritize-assumptions | Skill | 用 Impact × Risk 矩陣排序假設並建議實驗 | 假設清單太長、要決定先測哪個 |
| prioritize-features | Skill | 依影響、成本、風險、策略契合度排序功能 backlog，選前 5 名 | 排 backlog、做範疇取捨 |
| analyze-feature-requests | Skill | 將客戶需求分主題、評估契合度、選出前 3 名 | 檢視客戶功能需求、分流 backlog |
| opportunity-solution-tree | Skill | 建立 OST：成果 → 機會 → 解法 → 實驗 | 結構化探索工作、決定下一步做什麼 |
| interview-script | Skill | 產出結構化訪談腳本（JTBD 探問 + The Mom Test） | 準備使用者訪談、規劃探索研究 |
| summarize-interview | Skill | 把訪談逐字稿整理成結構化摘要 | 訪談後整理、綜合多場訪談 |
| metrics-dashboard | Skill | 定義指標分層、資料來源、視覺化、警示門檻 | 建指標儀表板、定 KPI、規劃監控 |
| /brainstorm | Command | 依「點子/實驗 × 既有/新產品」四種模式發想 | 想快速發散點子或實驗 |
| /discover | Command | 完整探索循環：發想 → 假設 → 排序 → 實驗 → 探索計畫 | 一次跑完從點子到驗證計畫 |
| /interview | Command | 訪談準備（prep）或訪談摘要（summarize） | 訪談前寫腳本 / 訪談後整理 |
| /setup-metrics | Command | 設計 North Star、輸入、健康、反向指標與警示門檻 | 新功能上線或指標框架需重整 |
| /triage-requests | Command | 將一批功能需求分主題、排序、出分流報告 | 手上累積大量需求要整理成 backlog |

---

## 共用概念速查

- **Product Trio**（Teresa Torres, *Continuous Discovery Habits*）：PM + Designer + Engineer 一起做探索，「好點子常來自工程師」。探索不是線性的，實驗失敗就回頭。
- **Initial Discovery vs Continuous Discovery**：前者著重願景、商業模式、市場驗證（產品該不該存在）；後者與交付並行，在上線產品上持續學習迭代。
- **四大產品風險**（Marty Cagan, *Inspired*；Teresa Torres 在 Continuous Discovery 中沿用）：Value（價值）、Usability（可用性）、Viability（商業可行性）、Feasibility（技術可行性）。
- **Opportunity Score**（Dan Olsen, *The Lean Product Playbook*）：`Opportunity Score = Importance × (1 − Satisfaction)`，Importance 與 Satisfaction 皆正規化到 0–1。高重要性 + 低滿意度 = 最佳機會。排序的對象是「問題（機會）」，不是解法；絕不讓客戶設計解法。
- **ICE**（Sean Ellis）：`Impact × Confidence × Ease`，原始版本三項皆評 1–10。本手冊採用的變體把 `Impact = Opportunity Score × 受影響客戶數`，讓影響力有實際規模。適合快速評分。
- **RICE**（Intercom）：`(Reach × Impact × Confidence) / Effort`，把 Reach 從 Impact 拆出，適合較大團隊。
- **XYZ 假設**：「至少 X% 的 Y 會做 Z」；加上時間 S 即為 XYZ+S（在 S 時間內）。

> 註：本手冊各處提到的排序公式（Opportunity Score / ICE / RICE）都以上方定義為準。

---

## 一、Skills

### brainstorm-ideas-existing
- **用途**：為既有產品做多視角發想，從 PM、Designer、Engineer 三個角度產出點子並選出最佳 5 個。
- **何時用**：產生新功能點子、為已辨識的機會找解法、與 Product Trio 一起發想。
- **需要的輸入**：產品、目標（objective）、目標客群、期望成果；若有研究資料、機會樹、persona 先讀；若提供產品網址可上網了解產品。
- **步驟／流程**：
  1. **理解機會**：確認產品、目標、市場區隔與期望成果；有模糊處先問清楚。
  2. **三視角各發想 5 個點子**：
     - **Product Manager**：商業價值、策略契合、客戶影響
     - **Product Designer**：使用者體驗、易用性、驚喜感（delight）
     - **Software Engineer**：技術可能性、資料運用、可擴展的解法
  3. **跨視角選出前 5 名**，依據：與目標的策略契合度、對期望成果的潛在影響、可行性與所需投入、與現有解法的差異化。
  4. **每個入選點子提供**：清楚名稱 + 一句話描述、入選理由、需驗證的關鍵假設。
- **輸出格式**：結構化清單（三視角各 5 個 → 前 5 名，含名稱/描述/理由/假設）；內容多時存成 markdown。
- **品質檢查**：逐步思考；點子要立基於現有使用者行為與已驗證的問題。

### brainstorm-ideas-new
- **用途**：新產品初期探索時，從三視角發想具體功能點子並選出前 5 名。
- **何時用**：新產品啟動探索、為新創點子找功能、初期發想。
- **需要的輸入**：目標客群、機會、期望成果；若有市場研究、競品分析先讀；必要時上網了解市場。
- **步驟／流程**：
  1. **理解機會**：確認產品概念、目標市場區隔、使用者想達成什麼。
  2. **三視角各發想 5 個具體功能點子**：
     - **Product Manager**：市場契合、價值創造、競爭優勢
     - **Product Designer**：使用者體驗、onboarding、參與度
     - **Software Engineer**：技術創新、API 整合、平台能力
  3. **跨視角選前 5 名**，新產品要重押：核心價值傳遞（是否解決主要問題）、驗證速度（能否快速測試）、差異化潛力。
  4. **每個入選點子**：提供理由與要測試的關鍵假設。
- **輸出格式**：同上；內容多時存 markdown。
- **品質檢查**：此 skill 屬 Initial Discovery（測產品該不該存在），新產品優先處理 desirability（需求）與 feasibility 風險。

### brainstorm-experiments-existing
- **用途**：為既有產品設計低成本實驗，在全面開發前驗證假設。
- **何時用**：驗證假設、便宜測試功能點子、規劃產品實驗。
- **需要的輸入**：功能點子、待驗證假設；若有 PRD、假設清單、設計稿先讀。
- **步驟／流程**：
  1. **釐清點子與假設**：確認團隊想做什麼、需要驗證什麼。
  2. **為每個假設建議實驗**，可考慮：
     - 原型的 first-click 測試或任務完成測試
     - Feature stub / fake door（假門）測試
     - 技術 spike
     - 正式環境 A/B test（附風險緩解）
     - Wizard of Oz（人工在背後模擬功能）
     - 以「行為」為主而非意見的問卷驗證
  3. **原則**：量測實際行為而非使用者意見；負責任地測試，不讓使用者或業務承受風險；正式環境測試（如 A/B）要說明風險緩解策略；以最少投入換最多已驗證學習。
  4. **每個實驗標明**：
     - **Assumption**：我們相信什麼？
     - **Experiment**：具體做什麼來驗證？
     - **Metric**：量測什麼？
     - **Success threshold**：若我們是對的，預期數值是多少？
- **輸出格式**：表格或結構化清單（假設｜實驗｜指標｜成功門檻）；內容多時存 markdown。

### brainstorm-experiments-new
- **用途**：為新產品寫 XYZ 假設並設計 pretotype（預原型）實驗，以最少投入驗證新概念。
- **何時用**：驗證新產品點子、做 pretotype、測市場需求。
- **需要的輸入**：產品概念；若有市場研究、landing page 草圖先讀。
- **步驟／流程**：
  1. **寫 XYZ 假設**：「至少 X% 的 Y 會做 Z」
     - **X%**：預期參與的目標市場比例
     - **Y**：具體的目標市場（例：「中型企業的財務主管」）
     - **Z**：他們會如何與產品互動
  2. **建議 2–3 個 pretotype 實驗**：
     - **Landing Page**：以註冊數或點擊數測興趣
     - **Explainer Video**：以觀看/互動指標測理解度與吸引力
     - **Email Campaign**：以回覆率與點擊率測需求
     - **Pre-Order / Waitlist**：以實際承諾測付費意願
     - **Concierge / Manual MVP**：人工交付服務來測價值
  3. **原則**（Alberto Savoia, *The Right It*）：
     - **Skin-in-the-Game**：測付費意願而非單純興趣；真正的承諾（時間、金錢、名聲）才是可靠訊號。
     - **YODA（Your Own Data）**：用自己實驗收集的資料，而非他人資料（市場報告、類比）。「你點子的市場，不在乎別人點子的市場。」
     - 量測實際行為，而非使用者意見。
  4. **每個實驗標明**：所測假設、方法、指標、成功門檻。
- **輸出格式**：XYZ 假設 + 實驗清單（假設｜方法｜指標｜門檻）；內容多時存 markdown。

### identify-assumptions-existing
- **用途**：以唱反調（devil's advocate）方式，找出既有產品功能點子在四大風險的假設。
- **何時用**：壓力測試功能點子、風險評估、準備假設地圖。
- **需要的輸入**：產品、目標、市場區隔、功能點子；若有設計稿、PRD、研究先讀。
- **步驟／流程**：
  1. **三視角思考「這功能為何會失敗」**：
     - **PM**：商業可行性、市場契合、策略契合
     - **Designer**：易用性、使用者體驗、採用障礙
     - **Engineer**：技術可行性、效能、整合挑戰
  2. **在四大風險找假設**：
     - **Value**：能為客戶創造價值嗎？解決真實問題嗎？
     - **Usability**：使用者會用嗎？學習曲線可接受嗎？
     - **Viability**：行銷、業務、財務、法務能支撐嗎？
     - **Feasibility**：現有技術做得出來嗎？有整合風險嗎？
  3. **每個假設註明**：具體可能出什麼錯、信心程度（High / Medium / Low）、建議的測試方式。
- **輸出格式**：依風險類別分組的假設清單（假設｜可能出錯處｜信心｜測試方式）。
- **品質檢查**：徹底但建設性——目的是強化點子而非否決。

### identify-assumptions-new
- **用途**：找出新產品在 8 大風險類別的假設（四大產品風險 + Ethics、Go-to-Market、Strategy & Objectives、Team）。
- **何時用**：評估新創風險、評估新產品概念、為新事業建立假設地圖。
- **需要的輸入**：產品概念、目標客群、功能點子；若有商業計畫、研究先讀。
- **背景**：好的團隊會預設至少四分之三的點子不會如預期表現。
- **步驟／流程**：
  1. **三視角思考「這產品為何會失敗」**：
     - **PM**：市場需求、付費意願、競爭態勢
     - **Designer**：首次使用體驗、onboarding、參與度
     - **Engineer**：自建或外購、可擴展性、技術債
  2. **在 8 大風險類別找假設**（每類的檢查問題）：
     - **Value**：能為客戶創造價值嗎？他們會持續使用嗎？
     - **Usability**：大家會用嗎？能夠夠快 onboard 嗎？會增加認知負荷嗎？
     - **Viability**：能賣/變現/取得資金嗎？值得這成本嗎？能支援客戶並幫他們成功嗎？能擴展嗎？合規嗎？
     - **Feasibility**：現有技術做得到嗎？整合可行嗎？能有效率嗎？能擴展嗎？
     - **Ethics**：該不該做？有倫理考量嗎？會對客戶造成風險嗎？
     - **Go-to-Market**（新產品特別關鍵）：能行銷嗎？有需要的通路嗎？能說服客戶試用嗎？這訊息適合這通路嗎？時機對嗎？上市方式對嗎？
     - **Strategy & Objectives**：我們的假設是什麼？別人能複製我們的策略嗎？考慮過政治、經濟、法律、技術、環境因素嗎？這些是最值得解決的問題嗎？
     - **Team**：團隊合作得好嗎？人對嗎？工具對嗎？整個團隊會待得夠久嗎？
  3. **每個假設**：評信心程度並建議測試方式。
- **輸出格式**：依 8 類分組的假設表；存 markdown。

### prioritize-assumptions
- **用途**：以 Impact × Risk 矩陣分流假設，並為需測試者建議實驗。
- **何時用**：假設清單要分流、決定先測什麼、套用假設排序畫布（Assumption Prioritization Canvas）。
- **需要的輸入**：假設清單；若有假設或研究資料檔先讀。
- **步驟／流程**：
  1. **每個假設評兩個維度**：
     - **Impact**：驗證此假設所創造的價值 × 受影響客戶數（ICE 中：`Impact = Opportunity Score × 客戶數`）
     - **Risk**：`(1 − Confidence) × Effort`（此處 Confidence 用 0–1；若用 1–10 評分，先除以 10）
  2. **依矩陣分類**：

     | | Low Risk | High Risk |
     |---|---|---|
     | **High Impact** | 直接進入實作（低風險高報酬） | **設計實驗測試** |
     | **Low Impact** | 延後測試，先處理更高優先者 | 否決這個點子（不值得投資） |

  3. **對需測試的假設建議實驗**：以最少投入取得最多驗證學習；量測實際行為而非意見；有明確成功指標與門檻。
  4. **呈現**：排序後的矩陣或表格。
- **輸出格式**：表格（假設｜Impact｜Risk｜象限｜建議行動/實驗｜指標｜門檻）；內容多時存 markdown。

### prioritize-features
- **用途**：依影響、投入、風險、策略契合度評估並排序功能 backlog，推薦前 5 名。
- **何時用**：排 backlog、做範疇決策、為產品點子排名。
- **需要的輸入**：產品目標、期望成果、功能點子清單（可為試算表、backlog、機會評估檔）。
- **框架選擇**：評估客戶問題用 **Opportunity Score**；快速為方案評分用 **ICE**；大團隊加 Reach 用 **RICE**（公式見「共用概念速查」）。
- **步驟／流程**：
  1. **理解優先方向**：確認產品目標與成功指標。
  2. **逐一評估每個功能**：
     - **Impact**：對期望成果的推動程度（有客戶資料時可用 Opportunity Score）
     - **Effort**：開發、設計、協調所需投入
     - **Risk**：不確定性多高？有哪些假設要測？
     - **Strategic alignment**：與產品願景、當前目標的契合度
  3. **推薦前 5 名**：明確排名 1–5、每項簡短理由、考量過的關鍵取捨、哪些被降優先及原因。
  4. 合適時以排序表呈現。
- **輸出格式**：排序表（排名｜功能｜Impact｜Effort｜Risk｜Alignment｜理由）+ 取捨說明 + 被降優先清單。

### analyze-feature-requests
- **用途**：把客戶功能需求依主題分類，對照產品目標評估並排序。
- **何時用**：檢視客戶需求、分流 backlog、做排序決策。
- **需要的輸入**：產品目標 + 功能需求清單（試算表、CSV、文件皆可直接讀；結構化資料可做摘要表）。
- **原則**：絕不讓客戶設計解法。排序「機會（問題）」而非功能。以 Opportunity Score 評估客戶回報的問題。
- **步驟／流程**：
  1. **理解目標**：確認引導排序的產品目標與期望成果。
  2. **將需求分主題**：相關需求歸成一組並命名。
  3. **評估策略契合度**：每個主題與目標的契合程度。
  4. **選出前 3 個功能**，依據：Impact（客戶價值與受影響人數）、Effort（開發與設計資源）、Risk（技術與市場不確定性）、Strategic alignment（與願景/目標契合）。
  5. **每個前 3 名提供**：理由（客戶需求、策略契合）、值得考慮的替代解法、高風險假設、如何以最少投入測試這些假設。
- **輸出格式**：主題表 + 前 3 名詳述；存 markdown 或結構化文件。

### opportunity-solution-tree
- **用途**：建立 Opportunity Solution Tree（OST，Teresa Torres），把期望成果連到客戶機會、可能解法與驗證實驗。
- **何時用**：結構化探索工作、對應機會與解法、決定下一步做什麼。
- **需要的輸入**：要改善的期望成果或業務指標；客戶研究資料（訪談、問卷、分析、回饋）；可選：已有的機會或解法點子。
- **樹的四層結構**：
  1. **Desired Outcome（頂層）**：團隊追求的單一可量測成果（例：「7 日留存提升到 40%」），來自 OKR 或產品策略。
  2. **Opportunities（第二層）**：研究發現的客戶需求、痛點、渴望——值得解決的問題，不是功能。以客戶口吻描述：「我很難……」「我希望可以……」。用 Opportunity Score 排序。
  3. **Solutions（第三層）**：每個機會的多種可能解法，不要只押第一個點子；由 Product Trio 一起發想。
  4. **Experiments（底層）**：快速、便宜地驗證解法是否真的解決機會；用四大風險做假設測試；優先選 skin-in-the-game 型實驗，而非意見型驗證。
- **關鍵原則**：
  - **一次一個成果**：樹只聚焦單一期望成果。
  - **機會而非功能**：不讓客戶設計解法。
  - **比較與對照**：每個機會至少產生 3 個解法再選，避免「第一個點子」陷阱。
  - **探索不是線性的**：實驗失敗就回頭，砍掉沒驗證的解法，探索新分支。
  - **持續而非定期**：每週依訪談、數據、實驗更新樹。
- **步驟／流程**：
  1. 定義期望成果（單一、可量測）。
  2. 從研究中找出 3–7 個客戶機會，相關者分組，以客戶視角描述。
  3. 用 Opportunity Score 或質性評估排序，聚焦前 2–3 個。
  4. 每個優先機會從 PM / Designer / Engineer 視角發想 3 個以上解法。
  5. 對最有潛力的解法各建議 1–2 個快速實驗：假設、方法、指標、成功門檻。
  6. 以清楚的階層格式呈現整棵樹。
- **輸出格式**：階層樹（成果 → 機會 → 解法 → 實驗），例如：
  ```
  成果：[單一可量測指標]
  ├── 機會 1：「我很難……」（Opportunity Score: x）
  │   ├── 解法 1a → 實驗：[假設｜方法｜指標｜門檻]
  │   ├── 解法 1b
  │   └── 解法 1c
  └── 機會 2 ……
  ```

### interview-script
- **用途**：產出結構化的客戶訪談腳本，挖出真實洞察而非意見，遵循 The Mom Test 原則。
- **何時用**：準備使用者訪談、製作訪談指引、規劃探索研究。
- **背景**：客戶訪談是持續探索 Stage 1（Explore）的其中一個來源，其他來源包括利害關係人訪談、使用數據、資料分析、問卷、市場趨勢、SEO/SEM 分析。PM 需要「不經轉手」直接接觸使用者、利害關係人、工程師與設計師；探索應由 Product Trio 一起做。
- **需要的輸入**：研究主題；若有 persona、假設清單、產品簡介、過往訪談筆記先讀。
- **步驟／流程**：
  1. **釐清研究目標**：團隊需要回答什麼問題？研究要支援哪些決策？哪些假設需要驗證？
  2. **建立腳本**（各段落與問題）：
     - **Opening（2–3 分鐘）**：自我介紹並說明目的（是學習不是推銷）；設定期待：「沒有對錯答案，我們想從你的經驗學習。」；徵求錄音同意（如適用）；確認可用時間。
     - **Warm-Up：情境與背景（5 分鐘）**：「談談你的角色，以及典型的一天/一週？」「你做〔與產品相關的活動〕多久了？」目的：建立關係、理解情境。
     - **Core Exploration：Jobs to Be Done（15–20 分鐘）**
       - *現況與行為*（過去式、具體實例）：「帶我走一遍你上一次〔做那件事〕的經過，發生了什麼？」「用了哪些工具或方法？」「花多久時間？還有誰參與？」
       - *痛點與挫折*（觀察，不引導）：「最難的部分是什麼？」「如果能揮魔杖，你會改變什麼？」「你試過什麼方法解決？結果如何？」
       - *期望成果*（用他們的話）：「在這方面『好』是什麼樣子？」「你怎麼知道它運作得好？」
       - *付費意願 / 優先度*（skin in the game）：「你目前在這上面花多少時間/金錢？」「你找過更好的解法嗎？找到什麼？」「為了解決它你願意放棄什麼？」
     - **Probing Techniques（追問技巧）**：「多說一點」——打開任何話題；「為什麼？」（溫和地問 2–3 次）——找根因；「能舉個具體例子嗎？」——從意見轉到事實；「接下來發生什麼？」——跟著故事走；「那讓你有什麼感覺？」——捕捉情緒強度。
     - **The Mom Test 規則**（Rob Fitzpatrick）：問**他們的生活**而非你的點子；問**過去**而非未來（「你會用 X 嗎？」沒有用）；**少說多聽**（約 80/20）；訪談中**絕不推銷**；留意**強烈情緒**（代表真實痛點或驚喜）；**稱讚是雜訊**（「聽起來很酷！」沒告訴你任何事）。
     - **Wrap-Up（3–5 分鐘）**：「有什麼我沒問但你覺得重要的嗎？」「我還該找誰聊這個？」致謝；說明後續（如有）。
  3. **客製化**：依產品領域、persona、研究目標調整問題；依訪談長度增刪段落。
  4. **附筆記模板**。
- **輸出格式**：腳本 + 筆記模板，存 markdown：
  ```
  Participant: [姓名 / 編號]
  Date: [日期]
  Key Jobs: [他們想完成什麼]
  Current Solution: [目前使用什麼]
  Biggest Pain: [最大挫折]
  Desired Outcome: [成功的樣子]
  Willingness to Pay: [目前投入多少 / 願意投入多少]
  Surprise Finding: [意外發現]
  Follow-up: [後續步驟]
  ```

### summarize-interview
- **用途**：把訪談逐字稿轉成以 JTBD、滿意度、行動項目為核心的結構化摘要。
- **何時用**：處理訪談錄音/逐字稿、綜合探索訪談、建立訪談摘要。
- **需要的輸入**：逐字稿（附檔：文字、PDF、語音轉文字，或直接貼上），先讀附檔。
- **步驟／流程**：
  1. 完整讀完逐字稿再摘要。
  2. 填寫下方模板；資訊不足填「-」；數值可改為質性描述（例：「不滿意」）。
  3. 用清楚簡單的語言——小學畢業生也看得懂。
- **輸出格式**（存 markdown）：
  ```
  **Date**: [訪談日期與時間]
  **Participants**: [姓名與角色]
  **Background**: [客戶背景]

  **Current Solution**: [目前使用的解法]

  **What They Like About Current Solution**:
  - [Job to be done、期望成果、重要度、滿意度]

  **Problems With Current Solution**:
  - [Job to be done、期望成果、重要度、滿意度]

  **Key Insights**:
  - [意外發現或值得注意的引述]

  **Action Items**:
  - [日期, 負責人, 行動 —— 例：「2025-01-15, PM 小陳, 與客戶追蹤定價問題」]
  ```

### metrics-dashboard
- **用途**：設計產品指標儀表板：選對指標、視覺化方式與警示門檻。
- **何時用**：建立指標儀表板、定義 KPI、建置產品分析、規劃資料監控。
- **需要的輸入**：產品/功能；若有既有儀表板、分析資料、OKR、策略文件先讀。
- **背景知識**：
  - **Metrics vs KPIs vs NSM**：Metrics＝所有可量測的東西；KPIs＝少數長期追蹤的關鍵量化指標；North Star Metric＝單一、以客戶為中心、作為業務成功領先指標的 KPI。
  - **好指標的 4 個條件**（Alistair Croll & Benjamin Yoskovitz, *Lean Analytics*）：(1) **可理解**——建立共同語言；(2) **可比較**——跨時間比較而非快照；(3) **比率或比例**——比絕對數字更能說明問題；(4) **能改變行為**——黃金法則：「如果一個指標不會改變你的行為，它就是壞指標。」
  - **8 種指標類型（4 組對照）**：Vanity vs Actionable（只有可行動指標會改變行為）；Qualitative vs Quantitative（WHAT vs WHY，兩者都需要，永遠別停止和客戶對話）；Exploratory vs Reporting（探索資料以發現意外洞察）；Lagging vs Leading（領先指標讓學習循環更快，例如客訴可預測流失）。
  - **5 個行動步驟**：(1) 用 4 條件稽核現有指標；(2) 更新儀表板，確保關鍵指標都是好指標；(3) 找出虛榮指標，謹慎使用；(4) 把指標分為領先/落後；(5) 挑一個問題深挖資料。
- **步驟／流程**：
  1. **指標分層**：
     - **North Star Metric**：最能代表核心價值傳遞的單一指標
     - **Input Metrics（3–5 個）**：驅動 North Star 的槓桿
     - **Health Metrics**：確保整體產品健康的護欄
     - **Business Metrics**：營收、成本、單位經濟
  2. **每個指標定義**：

     | Metric | Definition | Data Source | Visualization | Target | Alert Threshold |
     |---|---|---|---|---|---|
     | [名稱] | [精確算法：分子/分母、時間窗] | [資料來源] | [折線/長條/數字/漏斗] | [目標值] | [何時觸發警示] |

  3. **儀表板版面**：
     ```
     ┌─────────────────────────────────────────────┐
     │  NORTH STAR: [指標] — [目前值]               │
     │  Trend: [↑/↓ X% vs 上期]                     │
     ├──────────────────┬──────────────────────────┤
     │  Input Metric 1  │  Input Metric 2          │
     │  [Sparkline]     │  [Sparkline]             │
     ├──────────────────┼──────────────────────────┤
     │  Input Metric 3  │  Input Metric 4          │
     │  [Sparkline]     │  [Sparkline]             │
     ├──────────────────┴──────────────────────────┤
     │  HEALTH: [延遲] [錯誤率] [NPS]               │
     ├─────────────────────────────────────────────┤
     │  BUSINESS: [MRR] [CAC] [LTV] [Churn]        │
     └─────────────────────────────────────────────┘
     ```
  4. **檢視節奏**：每日——營運健康（錯誤、延遲、關鍵流程）；每週——輸入指標與參與趨勢；每月——North Star、業務指標、OKR 進度；每季——策略檢視與指標重新校準。
  5. **定義警示**：哪些門檻觸發調查？誰收到警示、透過什麼管道？預期回應時間？
  6. **依使用者情境推薦工具類別**：產品分析工具（事件/漏斗/留存分析）、SQL 型 BI 儀表板工具、營運/系統監控工具。
- **輸出格式**：儀表板規格書（指標分層 + 定義表 + 版面 + 節奏 + 警示），存 markdown。

---

## 二、Commands（工作流）

### /brainstorm — 多視角發想
- **用途**：從 PM、Designer、Engineer 三視角發想產品點子或實驗設計，依既有/新產品調整。
- **何時用**：需要快速發散點子，或為假設設計驗證實驗。
- **串接的 skills**：依模式擇一 → `brainstorm-ideas-existing` / `brainstorm-ideas-new` / `brainstorm-experiments-existing` / `brainstorm-experiments-new`；之後可接 `identify-assumptions-*`、`prioritize-features`。
- **需要的輸入**：兩個維度——(1) 要發想 **ideas**（做什麼）或 **experiments**（怎麼驗證）；(2) **existing**（持續探索）或 **new**（初期探索）。缺任一就問。
- **步驟／流程**：
  1. **決定模式**：解析兩個維度；都缺時問：「你要發想『要做什麼的點子』還是『驗證假設的實驗』？」「這是既有產品還是新產品概念？」
  2. **收集情境**（對話式，先問最關鍵的）：
     - 既有產品：產品是什麼？現有使用者是誰？探索哪個機會/問題空間？限制（技術債、平台限制、團隊產能）？之前試過什麼？
     - 新產品：概念是什麼？解決什麼問題？目標使用者是誰？他們目前的替代方案？目前階段（餐巾紙草圖、問題已驗證、早期原型）？最高風險假設？
     - 可接受上傳檔（PRD、研究文件、策略簡報）、貼文字或對話。
  3. **產出**：
     - **點子模式**：三視角發想（PM：使用者價值/商業影響；Designer：UX/驚喜/無障礙；Engineer：技術創新/平台槓桿/擴展性）；每個點子含名稱、描述、目標使用者影響、可行性評估；排出前 5 名並附理由；標出 quick win 與 strategic bet。
     - **實驗模式**：既有產品建議 A/B test、原型、fake door、wizard-of-oz、concierge、spike；新產品寫 XYZ+S 假設並建議 pretotype（landing page、explainer video、預購、concierge MVP）；每個實驗含假設、方法、成功標準、投入估計、預期時程；依「學習量 / 投入」比排序。
  4. **深化迭代**，提供選項：把點子細化成較完整規格？找出前幾名點子背後的假設（接 `identify-assumptions-*`）？設計實驗驗證（切到實驗模式）？與現有 backlog 一起排序（接 `prioritize-features`）？
- **輸出格式**：
  ```
  ## Brainstorm: [產品/功能領域]
  **Mode**: Ideas for [existing/new] product
  **Context**: [1–2 句摘要]

  ### PM Perspective
  1. **[點子名]** — [描述] | Impact: [H/M/L] | Effort: [H/M/L]
  ### Designer Perspective
  1. ...
  ### Engineer Perspective
  1. ...

  ### Top 5 Recommendations
  | Rank | Idea | Why | Quick Win? |

  ### Next Steps
  ```
  ```
  ## Experiment Design: [產品/功能領域]
  **Mode**: Experiments for [existing/new] product

  ### Hypotheses
  1. **[假設]** — XYZ 格式：[X]% 的 [Y] 會在 [S 時間] 內 [Z]

  ### Recommended Experiments
  | # | Experiment | Tests Hypothesis | Method | Effort | Timeline |

  ### Experiment Details
  [每個實驗：設置、成功標準、風險、能學到什麼]
  ```
- **注意事項**：既有產品要立基於現有使用者行為與已驗證問題；新產品先處理 desirability 與 feasibility 風險；若有研究文件或逐字稿，先萃取洞察再發想；先求廣度再求深度——先產出大量點子再評估。

### /discover — 完整探索循環
- **用途**：一條龍探索流程，從發散思考走到聚焦驗證，最後產出探索計畫。
- **何時用**：要對一個產品點子/功能領域/機會空間做完整探索，並據此做「做/不做、排序、轉向」決策。約需 15–30 分鐘，開頭先告知使用者。
- **串接的 skills（順序）**：`brainstorm-ideas-existing|new` → `identify-assumptions-existing|new` → `prioritize-assumptions` → `brainstorm-experiments-existing|new` → 彙整探索計畫。
- **步驟／流程**：
  1. **理解探索情境**：判斷是既有產品（有真實使用者的持續探索）還是新產品（尚無已驗證需求的初期探索）。問：在探索什麼？已知什麼（過往研究、客戶回饋、數據）？這次探索要支援什麼決策（做/砍、排序、轉向）？可接受上傳檔、連結、對話。
  2. **發想（發散階段）**：三視角發想，列出前 10 個點子與簡短理由，請使用者選 3–5 個往下走（或全部帶走）。
     - **Checkpoint**：「這是 10 個點子，要壓力測試哪些？選 3–5 個，或我全部帶下去。」
  3. **找假設（批判思考階段）**：對每個入選點子在以下風險類別找假設——Value（使用者要嗎？）、Usability（會用嗎？）、Feasibility（做得出來嗎？）、Viability（商業成立嗎？）、Go-to-Market（僅新產品：能觸及並轉換使用者嗎？）；採唱反調多視角分析；彙整成所有點子的假設總表。
  4. **排序假設（聚焦階段）**：放到 Impact × Risk 矩陣；找出「leap of faith」假設（高影響、高不確定）；依測試優先序排名；把可一起測的相關假設分組。
     - **Checkpoint**：「這些是最高風險的假設，你覺得哪些最需要先驗證？」
  5. **設計實驗（驗證階段）**：每個關鍵假設設計 1–2 個實驗。既有產品：A/B test、fake door、原型、使用者測試、數據分析；新產品：XYZ 假設、pretotype、landing page、concierge MVP。每個含成功標準、時程、投入；依相依性與投入排序。
  6. **產出探索計畫**（存 markdown 到使用者工作區）。
  7. **後續選項**：為首選點子寫 PRD？設計訪談腳本補充實驗？設定指標追蹤實驗？估算工作量並寫 MVP 的 user story？
- **輸出格式**：
  ```
  ## Discovery Plan: [主題]
  **Date**: [今天]
  **Product Stage**: [existing/new]
  **Discovery Question**: [要學到什麼]

  ### Ideas Explored
  ### Selected Ideas for Validation   [3–5 個 + 理由]
  ### Critical Assumptions
  | # | Assumption | Category | Impact | Uncertainty | Priority |
  ### Validation Experiments
  | # | Tests Assumption | Method | Success Criteria | Effort | Timeline |
  ### Experiment Details   [每個：假設、設置、量測、決策標準]
  ### Discovery Timeline
  Week 1: [實驗] / Week 2: [實驗] / Week 3: [分析與決策]
  ### Decision Framework
  - 若 [實驗] 成功 → 進行 [下一步]
  - 若 [實驗] 失敗 → [轉向 / 砍掉 / 再調查]
  ```
- **注意事項**：每個 checkpoint 使用者都可改方向、跳過或深入；有研究資料先萃取洞察再發想；探索計畫是活文件，實驗進行中可更新；新產品先驗證 desirability 再 feasibility；既有產品先確認有沒有使用數據可支撐假設判斷。

### /interview — 訪談準備與摘要
- **用途**：兩種模式——**prep** 在訪談前產出腳本；**summarize** 在訪談後萃取洞察。
- **何時用**：準備客戶訪談，或手上有逐字稿/筆記要整理。
- **串接的 skills**：prep → `interview-script`；summarize → `summarize-interview`。
- **Prep 模式流程**：
  1. **理解研究目標**：想學到什麼（具體研究問題）？訪談誰（區隔、角色、與產品的關係）？有多少時間（15 / 30 / 60 分鐘）？研究要支援什麼決策？
  2. **產出腳本**：遵循 The Mom Test——問他們的生活不問你的點子；不引導、不推銷，聚焦過去行為與真實情境。
     ```
     ## Interview Script: [研究主題]
     **Research Question** / **Target Participant** / **Duration**
     ### Warm-up (3–5 min)          建立關係、了解角色與情境
     ### Core Exploration (15–40 min) JTBD 探問、過去行為、現行流程、痛點
       - 每題：問題 + 為什麼問 + 追問提示
     ### Specific Topics (5–10 min)   針對特定功能或概念（如需要）
     ### Wrap-up (3–5 min)           開放收尾、請推薦受訪者、後續
     ### Note-Taking Template        訪談中記錄洞察的模板
     ### Red Flags to Watch For      對話偏離、或受訪者只是客套而非誠實的徵兆
     ```
  3. **客製與審查**：依時段調整題數；為使用者想測的特定假設加追問；標出可能引導受訪者的題目；提供可列印版本（markdown）。
- **Summarize 模式流程**：
  1. **接收逐字稿**：貼上文字、上傳檔（文件、文字檔、會議紀錄匯出）、或口述內容摘要。若只是粗略筆記，照可用資訊處理並註明限制。
  2. **萃取與結構化**：受訪者輪廓（角色、經驗、區隔、情境）；Jobs to Be Done；現行流程；痛點（挫折、變通做法、耗時處）；滿意訊號（好用處、驚喜時刻）；引述（逐字、有時間戳就附）；意外發現（與假設矛盾處）；功能反應（若有討論特定功能/概念）。
  3. **產出摘要**：
     ```
     ## Interview Summary
     **Participant**: [匿名化輪廓] / **Date** / **Duration** / **Interviewer**
     ### Key Insights        1. **[洞察]** — [佐證/引述]
     ### Jobs to Be Done     Primary JTBD: [When I…, I want to…, so I can…] / Related JTBDs
     ### Current Workflow    [逐步描述]
     ### Pain Points         | Pain Point | Severity | Quote |
     ### Satisfaction Signals | What Works | Why | Quote |
     ### Notable Quotes      > "[引述]" — 關於 [主題]
     ### Assumptions Validated / Invalidated | Assumption | Status | Evidence |
     ### Action Items        - [ ] 後續行動 / - [ ] 待深入的研究問題
     ### Raw Notes           [必要時附註解重點段落]
     ```
  4. **連結更廣的研究**：與其他訪談摘要比較？依受訪者說法更新假設？從多場訪談萃取 persona？
- **注意事項**：prep 模式一定附上「為什麼問」註記，幫訪談者不偏題；summarize 模式要區分受訪者「說了什麼」與「做了什麼」（行為 > 陳述）；標出同一場訪談內的矛盾（說一套、描述的做法是另一套）；逐字稿提到競品時記錄競爭情報；提供多份逐字稿時，跨受訪者綜合模式。

### /setup-metrics — 指標儀表板設計
- **用途**：設計完整的指標框架——從選對 North Star 到定義能及早抓到問題的警示門檻。
- **何時用**：為產品或新上線功能建立指標；既有指標缺漏或失準時。
- **串接的 skills**：`metrics-dashboard`。
- **步驟／流程**：
  1. **理解要量測什麼**：哪個產品/功能？階段（上線前、剛上線、成熟）？目前業務目標或 OKR？已有哪些指標、缺什麼或壞了什麼？用什麼分析工具（以便給實作建議）？
  2. **定義指標框架**：
     - **North Star Metric**：最能代表產品為使用者傳遞價值的單一指標；用三個條件驗證——衡量價值傳遞、是領先指標、可行動；精確定義（公式、資料來源、時間窗）。
     - **Input Metrics（3–5）**：驅動 North Star 的槓桿，每個都要能被某個團隊直接影響；畫出因果鏈：Input → North Star → Business Outcome。
     - **Health Metrics（3–5）**：應保持穩定、退化代表出問題的指標（例：錯誤率、延遲、客服工單量、NPS、流失率）；定義「健康」區間與退化門檻。
     - **Counter-Metrics（1–2）**：顯示你可能在錯誤方向優化的指標（例：North Star 是日活躍使用者，counter-metric 就是 session 品質，避免空洞的參與）。
  3. **設計警示門檻**：

     | Metric | Green | Yellow | Red | Check Frequency |
     |---|---|---|---|---|
     | [指標] | [健康區間] | [警告] | [危急] | [每日/每週] |
     - **Yellow**：調查——可能有狀況；**Red**：立即行動——呼叫值班或升級。
  4. **產出儀表板規格**：
     ```
     ## Metrics Dashboard: [產品/功能]
     **North Star**: [名稱] / **Definition**: [公式] / **Current value** / **Target**
     ### Input Metrics    | Metric | Definition | Owner | Target | Current |
     ### Health Metrics   | Metric | Healthy Range | Yellow Threshold | Red Threshold |
     ### Counter-Metrics  | Metric | Why It Matters | Watch For |
     ### Metrics Tree
     North Star: [指標]
     ├── Input: [指標 1] → 由 [團隊/行動] 驅動
     ├── Input: [指標 2] → 由 [團隊/行動] 驅動
     ├── Input: [指標 3] → 由 [團隊/行動] 驅動
     └── Counter: [指標] → 留意 [退化訊號]
     ### Implementation Notes  資料來源 / 更新頻率（即時/每小時/每日）/ 工具建議（依使用者現有工具）
     ### Review Cadence
     - Daily：看一眼 North Star 與健康指標
     - Weekly：檢視輸入指標趨勢，在團隊站會討論
     - Monthly：深入——輸入指標是否如預期驅動 North Star？
     - Quarterly：重新評估指標框架本身
     ```
     存 markdown。
  5. **後續選項**：寫 SQL 計算這些指標？依此框架訂 OKR？做 cohort 分析建立合理基準？建立每週指標檢視模板？
- **注意事項**：好的 North Star 很少見，多數團隊選了虛榮指標——堅持選能代表「傳遞給使用者的價值」而非只是參與度的指標；Input Metrics 對 North Star 的解釋應 MECE（互斥且完整）；上線前就定義指標，但註明上線後要校準基準；Counter-metric 用來防範 Goodhart's Law（指標一旦成為目標，就不再是好指標）；寧可少量、埋點完善的指標，也不要沒人看的龐大儀表板。

### /triage-requests — 功能需求分流
- **用途**：把來自客服工單、業務通話、問卷、內部通訊頻道的一堆功能需求，轉成排序過、可執行的 backlog。
- **何時用**：手上累積一批需求（貼上清單或上傳 CSV/試算表）。
- **串接的 skills（順序）**：`analyze-feature-requests`（分類分析）→ `prioritize-features`（排序）→ 分流報告。
- **步驟／流程**：
  1. **接收需求**：貼上文字（一行或一段一則）、上傳檔（CSV、Excel、文字檔）、結構化資料（有欄位如提出者、需求、日期時要保留）。沒給就請使用者提供。解析每則需求：核心訴求（使用者要什麼）、情境（誰、何時、為何——如有）、頻率訊號（多少人要求類似的東西）。
  2. **收集排序情境**（對話式，不要一次全問）：產品是什麼、在什麼階段？目前策略目標或 OKR（用來評契合度）？限制（團隊規模、技術債、即將到來的期限）？哪些區隔的需求權重較高（企業客戶、即將流失者、重度使用者）？
  3. **分類分析**：
     - **主題分群**：把類似需求歸為主題（例：「報表與分析」「協作」「行動版體驗」）
     - **各主題需求數**：對應到每個主題的獨立需求數
     - **策略契合度**：每個主題對照目標評 High / Medium / Low / None
     - **區隔分析**：哪些使用者區隔在推動哪些主題
     - **情緒訊號**：需求是否伴隨挫折、流失威脅或驚喜？
  4. **排序**：對每個主題（及主題內最重要的個別需求）評估：

     | Factor | Assessment |
     |---|---|
     | **Impact** | 影響多少使用者？多嚴重？ |
     | **Strategic alignment** | 是否服務當前目標？ |
     | **Effort estimate** | T-shirt size（S/M/L/XL） |
     | **Risk** | 不做會怎樣？ |
     | **Revenue signal** | 是否與成交、留存、擴充營收相關？ |

     為主題排名、產出排序清單。
  5. **產出分流報告**（存 markdown）。
  6. **後續選項**：為最高優先項寫 user story？為某些主題發想解法？設計實驗在開發前驗證需求？起草利害關係人更新？
- **輸出格式**：
  ```
  ## Feature Request Triage Report
  **Date** / **Requests analyzed** / **Themes identified**

  ### Theme Summary
  | # | Theme | Requests | Top Ask | Alignment | Impact | Effort | Priority |

  ### Priority 1: Act Now       近期規劃要納入
  - **[主題]**: [X] 則需求 — [為何緊急]
    - Top requests: [清單]
    - Recommended action: [build / prototype / investigate]
  ### Priority 2: Plan Next     值得規劃但不急
  ### Priority 3: Collect More Signal  有潛力但證據不足
  ### Priority 4: Decline or Defer     與策略不符（附理由）
  ### Notable Individual Requests       沒歸入主題但高價值的單一需求
  ### Patterns and Insights
  - 使用者在告訴你的關鍵洞察
  - 區隔特有的模式
  - 使用者「要求的東西」與「底層需求」之間的落差
  ```
- **注意事項**：輸入是有欄位的 CSV 時，保留資料結構並加欄位豐富它，並輸出可下載的 CSV；找出需求背後的需要——「加深色模式」可能其實是「長時間使用時減少眼睛疲勞」；標出互相衝突的需求（例：「簡化介面」vs「增加更多設定選項」）；需求量大（50 則以上）時先摘要主題，再依需要深入特定主題。
