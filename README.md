import numpy as np
import matplotlib.pyplot as plt

np.random.seed(0)
dates = np.arange(100)
prices = np.random.normal(loc=100, scale=1, size=100).cumsum()
buy_signals = np.where(prices < prices.mean(), prices, np.nan) 
sell_signals = np.where(prices > prices.mean(), prices, np.nan) 
plt.figure(figsize=(12, 6))
plt.plot(dates, prices, label='سعر السهم', color='blue')

plt.scatter(dates, buy_signals, marker='^', color='green', s=100, label='نقطة الشراء')
plt.scatter(dates, sell_signals, marker='v', color='red', s=100, label='نقطة البيع')
plt.title('استراتيجية التداول')
plt.xlabel('التاريخ')
plt.ylabel('السعر')
plt.legend()
plt.grid()
plt.show()
