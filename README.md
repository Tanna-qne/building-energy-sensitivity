# 節能措施回收期與敏感度

線上位址:https://tanna-qne.github.io/building-energy-sensitivity/

## 這是什麼

5 個 EnergyPlus 模型 × 4 個情境(基準、照明 −30%、貼膜 SHGC 0.30、兩者組合)共 20 次模擬,
把結果換算成年省電、年省錢與簡單回收期,再做電價與成本的敏感度分析。

所有模擬與模型修改都透過 [LBNL EnergyPlus-MCP](https://github.com/LBNL-ETA/EnergyPlus-MCP) 的工具完成。

## 檔案

| 檔案 | 內容 |
|---|---|
| `index.html` | 報告本體(單檔、內嵌 SVG、無外部依賴) |
| `results.csv` | 20 次模擬的原始結果(用電、省電、投資、回收期) |
| `sensitivity.csv` | 15 個措施組合在 7 種電價下的回收期 |

## 成本假設

- 電價 4.5 TWD/kWh
- 貼膜 1,200 TWD/m² 玻璃(面積取自模擬輸出的 `.eio`)
- 照明更新 600 TWD/m² 樓地板

這些都是假設值,不是當地報價。改假設後重跑會產生完全不同的結論,報告裡的敏感度表就是為此存在。

## 重新產生

```
python sensitivity.py     # 讀 ../scan2/results.csv, 輸出 index.html 與 sensitivity.csv
```

## 限制

只有電費、沒有碳排與維護成本;沒有折現率;措施之間只測了兩兩相加,沒有更複雜的組合。
