# 建筑能耗模拟与节能分析
**Building Energy Modelling · HVAC · Retrofit Analysis**

华中科技大学本科，预计 2027 年 6 月毕业。围绕建筑能耗模拟与节能方案评估开展项目开发，毕业设计也在这一方向。

## 我做了什么

| 项目 | 我的工作 | 成果入口 |
| --- | --- | --- |
| **建筑能耗模拟工具链 · 毕设相关** | 串联建筑参数输入、自动建模、EnergyPlus 模拟、节能措施比较和报告生成 | [工具链介绍与流程](https://tanna-qne.github.io/#toolchain) |
| **医院建筑节能研究** | 基于 DOE／PNNL 医院原型模型，比较基准建筑与设计案，并分析节能收益及回收期 | [阅读案例报告](https://tanna-qne.github.io/building-energy-sensitivity/hospital-energy-study/) |
| **节能措施经济性与敏感度分析** | 比较不同模型与改善情景，分析电价及投资成本变化对简单回收期的影响 | [查看在线分析](https://tanna-qne.github.io/building-energy-sensitivity/) |

**使用的工具：** Python · EnergyPlus · Ladybug Tools · OpenStudio · EnergyPlus-MCP

这个仓库集中展示公开报告和数据。工具链介绍、医院案例与敏感度分析属于同一条研究与开发路线；模拟结果是模型预测，具体假设和限制见各报告。

**[全部项目介绍](https://github.com/Tanna-qne/Tanna-qne.github.io) · [项目网站](https://tanna-qne.github.io/)**

## 公开成果与数据

- [医院建筑案例](hospital-energy-study/index.html)：基准／设计案对比、模拟结果对照、能耗及经济性分析。
- [敏感度分析报告](index.html)：节能措施比较、电价敏感度、投资成本敏感度。
- [模拟结果 CSV](results.csv) · [敏感度 CSV](sensitivity.csv)。

<details>
<summary><strong>展开：原有分析说明、成本假设与运行方式</strong></summary>

## 節能措施回收期與敏感度

線上位址:https://tanna-qne.github.io/building-energy-sensitivity/

## 這是什麼

5 個 EnergyPlus 模型 × 5 個情境(基準、照明 −30%、貼膜 SHGC 0.30、兩者組合、滲風 ×0.5)共 25 次模擬,
把結果換算成年省能源、年省錢與簡單回收期,再做電價與成本的敏感度分析。滲風沒有成本假設,只列省多少、不算回收期。

所有模擬與模型修改都透過 [LBNL EnergyPlus-MCP](https://github.com/LBNL-ETA/EnergyPlus-MCP) 的工具完成。

## 檔案

| 檔案 | 內容 |
|---|---|
| `index.html` | 報告本體(單檔、內嵌 SVG、無外部依賴) |
| `results.csv` | 25 次模擬的原始結果(用電、天然氣、省能源、投資、回收期) |
| `sensitivity.csv` | 15 個措施組合在 7 種電價下的回收期 |

## 成本假設

- 電價 4.5 TWD/kWh;天然氣 1.5 TWD/kWh(約 16 TWD/m³ ÷ 10.5 kWh/m³)
- 貼膜 1,200 TWD/m² 玻璃(面積取自模擬輸出的 `.eio`)
- 照明更新 600 TWD/m² 樓地板(只算有照明的 Zone,不含 plenum)
- 省能源以電 + 天然氣計:照明與貼膜通常會讓暖房多燒天然氣,只看電會高估效益

這些都是假設值,不是當地報價。改假設後重跑會產生完全不同的結論,報告裡的敏感度表就是為此存在。

## 重新產生

```
python sensitivity.py     # 讀 ../scan2/results.csv, 輸出 index.html 與 sensitivity.csv
```

## 限制

只有電費與天然氣費、沒有碳排與維護成本;沒有折現率;措施之間只測了兩兩相加,沒有更複雜的組合。

</details>
