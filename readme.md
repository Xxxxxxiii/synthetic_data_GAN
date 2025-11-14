# ⭐2025/11/14
温度0.1，epochs100
## **合成数据**
🟢 synthetic_data_tau0.1_eps100_v5_251114.xlsx
## **数据条数**
91640 rows × 8 columns
## **模型名称**
gan_tau0.1_eps100.pkl
## **分布概览**
![image](https://github.com/Xxxxxxiii/synthetic_data_GAN/blob/master/result_pics/distribution_v5.png)


# ⭐2025/11/13
温度保持0.2不变，epochs加大25 -> 100
## **合成数据**
🟢 synthetic_data_tau0.1_v4_251113.xlsx
## **数据条数**
90819 rows × 8 columns
## **模型名称**
gan_tau0.2_eps100.pkl
## **分布概览**
![image](https://github.com/Xxxxxxiii/synthetic_data_GAN/blob/master/result_pics/distribution_v4.png)

温度下调 0.2 -> 0.1
## **合成数据**
synthetic_data_tau0.2_eps100_v4_251113.xlsx
## **数据条数**
82340 rows × 8 columns
## **模型名称**
gan_tau0.1.pkl
## **分布概览**
![image](https://github.com/Xxxxxxiii/synthetic_data_GAN/blob/master/result_pics/distribution_v3.png)


# ⭐2025/11/12
提取5%稀有数据
## **合成数据**
🟢 scarce_0.05_cooler_251112.xlsx
## **数据条数**
12134 rows × 8 columns


# ⭐ 2025/11/11
冷却塔模型合成数据
## **合成数据**
🟢 synthetic_data_filtered_v1_251111.xlsx
## **数据条数**
242682 rows × 13 columns
## **字段含义**
### 原物理量字段
**因变量**

temp_out：输出温度

**自变量**

temp_in：输入温度

freq_fan_1：风扇1频率

freq_fan_2：风扇2频率

freq_fan_3：风扇3频率

flow_cow：流量总和

temp_dry_bulb：室外温度

ratio_humidity：室外湿度

### 评估字段

credibility_score：置信度分数，衡量合成数据在原数据分布中的可信度。计算原数据的均值、标准差`μ, σ`，
对每个生成点X计算`z-score = X-μ / σ`，`scores = 1.0 ÷ [1.0 + √(z-score²)]`。最后归一化。

novelty_score_knn：新颖度分数，以knn衡量。即，对于每一个生成样本，找到它在真实数据集中的 K 个最近邻。
然后计算该生成样本到这 K 个最近邻的距离。最后归一化。

novelty_score_lof：新颖度分数，以lof衡量。即，对于生成点 A，计算其局部可达密度（LRD），
这是点 A 到其 K 个邻居的平均可达距离的倒数。再对于点 A，计算其 的局部可达密度与其 K 个邻居的平均局部可达密度的比值（LOF）。最后归一化。

### 计算得到的物理量字段

temp_diff：温差，公式为`temp_diff = temp_in - temp_out`

Q_total：总热量，公式为`Q_total = flow_cow × (temp_in - temp_out) × c_p`，其中`c_p = 4.186`.

## **已满足的约束**

1. `temp_in >= temp_out`
2. `freq_fan_1, freq_fan_2, freq_fan_3, flow_cow >= 0`
3. `temp_out >= 湿球温度`
4. 生成数据中各字段范围不超过原数据中各字段范围

## **分布概览**
![image](https://github.com/Xxxxxxiii/synthetic_data_GAN/blob/master/result_pics/distribution_v1.png)


