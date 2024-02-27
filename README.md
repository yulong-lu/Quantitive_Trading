# Quantitive_Trading
以19年到21年，ETH（以太币）分钟级数据作为数据源，对”布林线“交易策略的回测。  
我们希望解决这样一个问题：100美元，按照双布林通道策略进行交易，最后能够得到多少钱。  
## 简介 
ETH是一个类似于比特币的加密货币，所在链有世界计算机的美誉，除BTC（比特币）之外，ETH市值第一，大概在3700亿美金市值，因此，对ETH的研究是由价值的。  
双布林线策略是一个经典的趋势跟踪策略，关键思想是如果币价反常下跌，有一定可能性会发生黑天鹅事件，也就是会可能会继续暴跌，如果我们做空，就能从中赚取利润。当然，一般来说，反常下跌会很快回到平均值，因此，这是一个平时赔小钱，黑天鹅赚大钱的策略。  
## 策略详情
布林线策略大致如下：  
共有两个参数m、n，3条线，分别是上轨，下轨和中轨。  
中轨:n根收盘价的移动平均线。  
上轨:n根收盘价的移动平均线 + m*n根收盘价的标准查差。  
下轨:n根收盘价的移动平均线 - m*n根收盘价的标准差。  
当前蜡烛的收盘价向上穿过上轨做多，再次向下穿过中轨时候平仓。  
当前蜡烛的收盘价向下穿过下轨做空，再次向上穿过中轨的时候平仓。  
## 数据处理过程
参数假设：m为100，n为2，合约交易倍率为1，开仓手续费和平仓手续费为0，资金费率为0  
数据预处理：数据清洗，整理成所需要的格式  
计算交易信号：根据策略计算产生交易信号的k线，去除假信号  
计算资金曲线：根据交易信号计算仓位，并根据仓位，计算持仓期间的资金变化  
## 文件说明
ETH_1min.zip是源数据，bollinger_bands_generate_signal.py对源数据进行加工，得到带有交易信号的更加规范的data_with_signal.csv数据，equity_curve.py对信号数据文件再次加工，得到资金曲线数据eth_equity_curve.csv  
## 结论：
100美元按照双布林通道策略进行交易，从19年到21年，最终变成了125.588940美元。  
如图所示：  
![63a780bf6928a799c013373c58f8c37](https://github.com/yulong-lu/Quantitive_Trading/assets/57821616/9b22153b-f42f-4979-aaa4-a8c569fc863e)
