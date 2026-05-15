# 海龜湯題目格式

## 完整題目結構

```yaml
id: P001
difficulty: easy | medium | hard   # easy=3關鍵字 / medium=5 / hard=7
image: [圖片URL或路徑]
image_prompt: |
  [給圖片生成模型的英文描述，精確對應每個關鍵字的視覺元素]
question: |
  [≤50字情境，不含任何線索。一個明確問題？]
answer:
  full: |
    [完整故事答案，包含因果邏輯與所有關鍵字的串接]
  keywords:
    - 關鍵字1
    - 關鍵字2
    - 關鍵字3
    # medium 再加2個，hard 再加4個
```

---

## 規則

### 圖片
- **所有線索與因果要素只能在圖片裡**，文字不能給任何線索
- 圖片必須獨立可解：只看圖片能推出所有關鍵字
- 一題只用一張圖
- 避免圖中出現文字（除非文字本身是線索）
- `image_prompt` 必須精確描述每個關鍵字對應的視覺元素
- 格式參考：`Photorealistic [場景], [元素1], [元素2], no text overlay, cinematic lighting`

### 問題文字（≤50字）
- 只提供最低限度的情境脈絡（不在圖片中的背景資訊）
- 結尾只能有**一個問題**，以「？」結尾
- 不能洩漏任何線索，特別是圖片中才有的資訊
- ❌ 壞：「一名裝義肢的男子在沙灘留下單腳印。為什麼？」← 洩漏線索
- ✅ 好：「沙灘上留下了奇怪的足跡。發生了什麼事？」

### 關鍵字
- 每個關鍵字代表答案中一個**獨立的因果要素**
- 用名詞或短名詞組（≤5字），不用動詞句
- 關鍵字之間不能重複、包含或重疊
- 每個關鍵字必須對應圖片中一個可驗證的視覺元素

| 難度 | 關鍵字數 | 特性 |
|------|----------|------|
| easy | 3 | 圖片表面可見，推理一步 |
| medium | 5 | 需結合多個圖片元素推理 |
| hard | 7 | 需多步推理，關鍵字有因果鏈 |

### 完整答案
- 包含完整故事因果邏輯
- 必須串接所有關鍵字
- 邏輯嚴密，無歧義

### 原創性
- 不使用網路流傳的經典海龜湯題目
- 核心機制不能與知名題目相同
- 禁用機制：矮子電梯、燈塔關燈、鬼故事身份反轉
- 可改編情境，但因果邏輯必須原創

---

## 範例

```yaml
id: P003
difficulty: medium
image: https://example.com/dinner.png
image_prompt: >
  Photorealistic kitchen scene at night: dining table set for two,
  one plate empty and used, one plate untouched with food,
  a chair knocked over, red wine spilled on white tablecloth,
  a cat lying on the floor next to a spilled food bowl,
  no people visible, dim warm lighting, cinematic.
question: |
  週末夜晚警方接獲報案推開公寓門。餐廳裡發生了什麼事？
answer:
  full: |
    夫妻共進晚餐，丈夫用餐到一半突發心臟病倒地。
    妻子慌忙扶丈夫離開送醫，椅子因此打翻，紅酒灑出。
    貓趁亂打翻飼料碗。妻子那側食物未動是因為她還沒吃。
    鄰居聽到聲響報警。
  keywords:
    - 心臟病發作
    - 丈夫倒地
    - 妻子離開送醫
    - 椅子打翻
    - 貓打翻飼料碗
```

---

## 出題自檢清單

- [ ] 圖片包含所有關鍵字對應的視覺元素
- [ ] `image_prompt` 描述了每個關鍵字的視覺呈現
- [ ] 問題文字 ≤50字，只有一個問題
- [ ] 問題文字沒有洩漏任何線索
- [ ] 關鍵字數量符合難度（easy=3 / medium=5 / hard=7）
- [ ] 每個關鍵字獨立、不重疊
- [ ] 完整答案串接了所有關鍵字的因果邏輯
- [ ] 題目原創，核心機制非網路流傳
