# 附 D - KaTeX 单位（转pt）

| KaTeX 单位  | 值               | KaTeX 单位  | 值               |
| ---------- | ---------------- | ---------- | ------------------- |
| em         | CSS em           | bp         | $\frac{1}{72}\text{inch}\times F \times G=\frac{72.27}{72}\text{pt}$ |
| ex         | CSS ex           | pc         | $12\text{ pt}$ |
| mu         | $\dfrac{1}{18}$ CSS em | dd         | $\dfrac{1238}{1157}\text{pt}$ |
| pt         | $\frac{1}{72.27} \text{inch}\times F \times G\Rightarrow1\text{ inch}=\frac{72.27\text{ pt}}{F\times G}$ | cc         | $\dfrac{14856}{1157}\text{pt}$ |
| mm         | $1\text{mm}\times F \times G=\dfrac{1}{100}\text{cm}=\dfrac{7227}{25400}\text{pt}$ | nd         | $\dfrac{685}{642}\text{pt}$ |
| cm         | $1\text{ cm}\times F \times G=\dfrac{7227}{254}\text{ pt}\quad(1\text{ cm}=\dfrac{1}{2.54}\text{inch})$ | nc         | $\dfrac{1370}{107}\text{pt}$ |
| in         | $1\text{ inch}\times F \times G=72.27\text{ pt}$ | sp         | $\dfrac{1}{65536}\text{pt}$ |

!!! note "附注"
    未找到 px 的官方说明，但实际测试表明其应与 bp 等价。

    $\tt 20px: \rule{20px}{20px}\quad 20bp: \rule{20bp}{20bp}$