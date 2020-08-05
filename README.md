# 基于BP算法的房价预测（成都市）

## 输入参数及数据收集

表1 成都市2009-2019年影响房价各因素及房价

|      | 年份                           | 2009     | 2010     | 2011     | 2012     | 2013     |
| ---- | ------------------------------ | -------- | -------- | -------- | -------- | -------- |
| A1   | 年末总人口(万人)               | 1139.63  | 1149.07  | 1163.28  | 1173.30  | 1187.99  |
| A2   | 城镇人口(万人)                 | 629.38   | 650.91   | 705.66   | 716.72   | 728.71   |
| A3   | 总户数(万户)                   | 417.87   | 430.68   | 439.69   | 446.85   | 455.05   |
| B1   | 地区生产总值(亿元)             | 4503.00  | 5551.30  | 6854.58  | 8138.90  | 9108.89  |
| B2   | 人均地区生产总值(元)           | 35215.00 | 41253.00 | 49438.00 | 57624.00 | 63977.00 |
| B3   | 在岗职工平均工资(元)           | 34195.00 | 38603.00 | 42363.00 | 48302.00 | 56581.00 |
| B4   | 年度平均基准贷款利率(分)       | 5.94     | 6.00     | 6.80     | 6.55     | 6.15     |
| B5   | 城镇居民家庭人均可支配收入(元) | 18659.40 | 20835.34 | 23932.08 | 27193.65 | 29968.00 |
| C1   | 房地产开发投资额(亿元)         | 945.14   | 1278.34  | 1588.22  | 1889.23  | 2111.25  |
| C2   | 商品房销售面积(万平方米)       | 2708.76  | 2559.28  | 2676.04  | 2844.09  | 2950.13  |
| C3   | 住宅用途地价水平值(元/平方米)  | 6810.00  | 6943.00  | 7288.00  | 7206.00  | 8020.00  |
| R0   | 商品房平均销售价格(元/平方米)  | 4925.00  | 5937.00  | 6716.71  | 7288.24  | 7197.00  |

续表

|      | 年份                           | 2014     | 2015     | 2016     | 2017     | 2018     |
| ---- | ------------------------------ | -------- | -------- | -------- | -------- | -------- |
| A1   | 年末总人口(万人)               | 1210.74  | 1228.05  | 1398.90  | 1435.33  | 1476.05  |
| A2   | 城镇人口(万人)                 | 755.77   | 720.62   | 784.60   | 851.17   | 899.50   |
| A3   | 总户数(万户)                   | 467.16   | 475.99   | 536.86   | 550.65   | 563.23   |
| B1   | 地区生产总值(亿元)             | 10056.59 | 10801.16 | 12170.23 | 13889.39 | 15342.77 |
| B2   | 人均地区生产总值(元)           | 70019.00 | 74273.00 | 76960.00 | 86911.00 | 94782.00 |
| B3   | 在岗职工平均工资(元)           | 63201.00 | 69123.00 | 74408.00 | 79292.00 | 88011.00 |
| B4   | 年度平均基准贷款利率(分)       | 6.15     | 5.50     | 4.90     | 4.90     | 4.90     |
| B5   | 城镇居民家庭人均可支配收入(元) | 32665.00 | 33476.00 | 35902.00 | 38917.50 | 42127.85 |
| C1   | 房地产开发投资额(亿元)         | 2215.53  | 2435.25  | 2638.89  | 2492.65  | 2273.16  |
| C2   | 商品房销售面积(万平方米)       | 2951.30  | 2997.43  | 3928.77  | 3925.91  | 3682.52  |
| C3   | 住宅用途地价水平值(元/平方米)  | 7655.00  | 7609.00  | 7983.00  | 8940.00  | 16695.00 |
| R0   | 商品房平均销售价格(元/平方米)  | 7032.00  | 6875.00  | 7504.00  | 8733.00  | 9866.60  |

续表

|      | 年份                           | 2019      |
| ---- | ------------------------------ | --------- |
| A1   | 年末总人口(万人)               | 1500.07   |
| A2   | 城镇人口(万人)                 | 938.14    |
| A3   | 总户数(万户)                   | 576.95    |
| B1   | 地区生产总值(亿元)             | 17012.65  |
| B2   | 人均地区生产总值(元)           | 103386.00 |
| B3   | 在岗职工平均工资(元)           | 97519.00  |
| B4   | 年度平均基准贷款利率(分)       | 4.85      |
| B5   | 城镇居民家庭人均可支配收入(元) | 45878.00  |
| C1   | 房地产开发投资额(亿元)         | 2611.86   |
| C2   | 商品房销售面积(万平方米)       | 3531.40   |
| C3   | 住宅用途地价水平值(元/平方米)  | 18015.00  |
| R0   | 商品房平均销售价格(元/平方米)  | 10943.24  |

数据来源：
国家统计局http://www.stats.gov.cn
成都市统计局http://www.cdstats.chengdu.gov.cn
中国地价检测网 http://www.landvalue.com.cn

## 指标数据预测

|      | 年份                           | 2020      | 2021     | 2022     |
| ---- | ------------------------------ | --------- | -------- | -------- |
| A1   | 年末总人口(万人)               | 1563.1224 | 1594.583 | 1610.59  |
| A2   | 城镇人口(万人)                 | 1047.3355 | 1166.747 | 1315.473 |
| A3   | 总户数(万户)                   | 599.78621 | 613.4148 | 622.4893 |
| B1   | 地区生产总值(亿元)             | 19285.408 | 21842.92 | 24830.53 |
| B2   | 人均地区生产总值(元)           | 114405    | 127612.5 | 143370.9 |
| B3   | 在岗职工平均工资(元)           | 104270.3  | 112584.5 | 121285.6 |
| B4   | 年度平均基准贷款利率(分)       | 4.6309091 | 4.453636 | 4.276364 |
| B5   | 城镇居民家庭人均可支配收入(元) | 49972.669 | 55013.04 | 60964.35 |
| C1   | 房地产开发投资额(亿元)         | 2962.6558 | 3115.833 | 3269.01  |
| C2   | 商品房销售面积(万平方米)       | 3954.4625 | 4086.939 | 4219.416 |
| C3   | 住宅用途地价水平值(元/平方米)  | 20641.2   | 24433.76 | 28668.36 |

## 房价预测结果
![housevalue result](https://raw.githubusercontent.com/chriswang2001/housevalue/master/result.png)

说明：matlab所创建的BP神经网络初始权值是随机赋值，所以每次运行的结果都不相同，可选取测试结果最好的一组进行预测。