# TIME in Python
- **datetime:** 关注日期时间/数学运算/日期格式化输出及其属性
- **time:** 提供日期和时间转换
- **calendar:** 提供日历相关的函数

## datetime

```python
from datetime import datetime, timedelta
```

### 获取当前时间

```python
# 初始化
datetime.now()
datetime(2018, 12, 31, 23, 59, 59, 999999)
# 获取年月日时分秒
datetime.now().year  # month / day / hour / minute / second / microsecond
# 获取星期几
datetime.now().weekday()
# 获取当天是一年中的第几天
datetime.now().timetuple().tm_yday
# 获取当天是一周中的第几天
datetime.now().isoweekday()
# 获取当天是一月中的第几天
datetime.now().timetuple().tm_mday
# 获取当天是一年中的第几周
datetime.now().isocalendar()[1]
# 【ATTN】isocalendar(): 返回一个元组，包含ISO 8601年份、ISO 8601周号和ISO 8601星期几
```

### datetime中的格式转换

```python

# datetime转字符串
datetime.now().strftime('%Y-%m-%d %H:%M:%S')
# 字符串转datetime
datetime.strptime('2018-01-01 00:00:00', '%Y-%m-%d %H:%M:%S')

# datetime转时间戳
datetime.now().timestamp()
# 时间戳转datetime
datetime.fromtimestamp(1546272000.0)
```

### datetime中的时间计算

```python

current_time = datetime.now()
# 3秒前
current_time - timedelta(seconds=3)
# 5分钟后
current_time + timedelta(minutes=5)
# 2小时前
current_time - timedelta(hours=2)
# 1天后
current_time + timedelta(days=1)
# 4周前
current_time - timedelta(weeks=4)
```

## time

```python
import time
```

### 获取当前时间

```python
# 获取当前时间戳
timestamp = time.time()
# 获取当前时间
currenttime = time.localtime()
# time.localtime(time.time())  # 等价于上一行，获得时间元组
# 【OUT】：time.struct_time(tm_year=2018, tm_mon=12, tm_mday=31, tm_hour=23, tm_min=59, tm_sec=59, tm_wday=0, tm_yday=365, tm_isdst=0)
# 获取时间元组的具体元素
currenttime.tm_year  # 获取年份 / month / tm_mday / tm_hour / tm_min / tm_sec / tm_wday(0是周一) / tm_yday / tm_isdst(是否夏令时)
# 获取当前时间
time.strftime('%Y-%m-%d %H:%M:%S', time.localtime())
time.strftime('%Y-%m-%d %H:%M:%S', time.localtime(time.time())) # 时间戳格式化（需要先转为时间元组）
```

### 程序暂停

```python

cur_time = time.time()
print("开始睡眠3秒: {} ".format(time.strftime("%Y-%m-%d %H:%M:%S")))
# 程序暂停3秒
time.sleep(3)
print("睡眠结束: {} ".format(time.strftime("%Y-%m-%d %H:%M:%S")))
end_time = time.time()
print("程序运行时间: {} ".format(end_time - cur_time))
```


## calendar

```python
import calendar
```

### 获取当前日历

```python
# 获取当前日历
calendar.month(2018, 12)
# 【OUT】：'    December 2018\nMo Tu We Th Fr Sa Su\n                1  2\n 3  4  5  6  7  8  9\n10 11 12 13 14 15 16\n17 18 19 20 21 22 23\n24 25 26 27 28 29 30\n31\n'
```

### 判断

```python
# 判断是星期几
calendar.weekday(2018, 12, 31) # 【OUT】：0~6
# 判断是一年中的第几周
calendar.week(2018, 12, 31) # 【OUT】：1~53
# 判断是一月中的第几天
calendar.monthrange(2018, 12) # 【OUT】：(5, 31)  # 5是周六，31是天数
# 判断是否是闰年
calendar.isleap(2018) # 【OUT】：False
```
