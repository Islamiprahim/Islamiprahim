import numpy as np
import matplotlib.pyplot as plt

# بيانات سعر وهمية
np.random.seed(0)
dates = np.arange(100)
prices = np.random.normal(loc=100, scale=1, size=100).cumsum()

# إعداد نقاط الشراء والبيع
buy_signals = np.where(prices < prices.mean(), prices, np.nan)  # نقاط الشراء
sell_signals = np.where(prices > prices.mean(), prices, np.nan)  # نقاط البيع

# رسم البيانات
plt.figure(figsize=(12, 6))
plt.plot(dates, prices, label='سعر السهم', color='blue')

# إضافة مثلثات الشراء
plt.scatter(dates, buy_signals, marker='^', color='green', s=100, label='نقطة الشراء')
# إضافة مثلثات البيع
plt.scatter(dates, sell_signals, marker='v', color='red', s=100, label='نقطة البيع')

# إعدادات الرسم
plt.title('استراتيجية التداول')
plt.xlabel('التاريخ')
plt.ylabel('السعر')
plt.legend()
plt.grid()
plt.show()
