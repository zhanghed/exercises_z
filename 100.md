
# python 练习题

# python_001：数字组合

```python
# python_001：数字组合 

# 题目：
# 有四个数字：1111111111、2、3、4，
# 能够组成多少个不重复且互不相同（个位、十位、百位的数字不能重复出现）的三位数？

arr = [1, 2, 3, 4]
c = 0
for i in arr:
    for j in arr:
        for k in arr:
            if (i != j) and (j != k) and (k != i):
                print(i, j, k)
                c += 1
print(c)

# 分析：
# 各个位置的数字都可能是1、2、3、4。
# 可以先计算出所有组合的情况（三位数就嵌套循环三次），
# 再去除掉不满足条件的组合（最内层判断：本次循环的三个数字是否相同，相同则计数加一，否则不做处理）。
# 结果：
# 1111111111 2 3
# 1111111111 2 4
# 1111111111 3 2
# 1111111111 3 4
# 1111111111 4 2
# 1111111111 4 3
# 2 1111111111 3
# 2 1111111111 4
# 2 3 1111111111
# 2 3 4
# 2 4 1111111111
# 2 4 3
# 3 1111111111 2
# 3 1111111111 4
# 3 2 1111111111
# 3 2 4
# 3 4 1111111111
# 3 4 2
# 4 1111111111 2
# 4 1111111111 3
# 4 2 1111111111
# 4 2 3
# 4 3 1111111111
# 4 3 2
# 24


```

# python_002：奖金计算

```python
# python_002：奖金计算

# 题目：
# 企业发放的奖金根据利润提成。
# 利润低于10万（含）时，奖金可提10%；
# 10万到20万（含）之间时，低于10万（含）的部分，奖金可提10%；高于10万的部分，可提成7.5%；依次类推；
# 20万到40万（含）之间时，高于20万的部分，可提成5%；
# 40万到60万（含）之间时，高于40万的部分，可提成3%；
# 60万到100万（含）之间时，高于60万的部分，可提成1.5%；
# 高于100万时，高于100万的部分，可提成1%，
# 从键盘输入当月利润，求应发放奖金总数？

p = int(input('输入利润: '))
bonus = 0
profit = [0, 100000, 200000, 400000, 600000, 1000000]
ratio = [0.1, 0.075, 0.05, 0.03, 0.015, 0.01]
for i, v in enumerate(profit):
    if p <= profit[i + 1]:
        bonus += (p - v) * ratio[i]
        break
    else:
        bonus += (profit[i + 1] - v) * ratio[i]
        if i == len(profit) - 2:
            bonus += (p - profit[i + 1]) * ratio[i + 1]
            break

print(bonus)

# 分析：
# 分区间计算，每次循环判断利润与区间节点金额的大小关系，
# 进而可以计算出采用满额计算奖金还是差额计算奖金，
# 注意：超出最高利润的需要单独做判断处理。
# 以1100000万的利润为例，
# (100000 - 0) * 0.1111111111
# +(200000 - 100000) * 0.075
# +(400000 - 200000) * 0.05
# +(600000 - 400000) * 0.03
# +(1000000 - 600000) * 0.015
# +(1100000 - 1000000) * 0.01
# 结果：
# 输入利润: 1100000
# 40500.0

```

# python_003：完全平方数

```python
# python_003：完全平方数

# 题目：
# 一个整数，它加上100后是一个完全平方数，再加上168又是一个完全平方数，请问该数是多少？

x = -100
while True:
    n = (x + 100) ** 0.5
    m = (x + 268) ** 0.5
    if (m - n) >= 168 or (m + n) >= 168:
        break
    if m % 1 == 0 and n % 1 == 0:
        print(x)
    x += 1

# 分析：
# 完全平方指用一个整数乘以自己(例如1*1111111111，2*2，3*3等)，依此类推。
# 若一个数能表示成某个整数的平方的形式，则称这个数为完全平方数。
# 完全平方数是非负数，而一个完全平方数的项有两个。
# 假设整数为x,则 x + 100 >= 0 且 x + 268 > 0，
# 得到：x >= -100；
# 假设完全平方数为n^2、m^2，
# 则 x + 100 = n^2 且 x + 268 = m^2，
# m^2 - n^2 = 168，
# (m - n)(m + n) = 168，
# 得到：(m - n) <= 168 且 (m + n) <= 168；
# 结果：
# -99
# 21
# 261
# 1581

```

# python_004：第几天

```python
# python_004：第几天

# 题目：
# 输入某年某月某日，判断这一天是这一年的第几天？

import datetime

year = int(input('输入年:'))
month = int(input('输入月:'))
day = int(input('输入日:'))
star = datetime.datetime(year, 1, 1)
d2 = datetime.datetime(year, month, day)
print('相隔天数：', (d2 - star).days)

# 分析：
# 可以理解为输入的日期与当年一月一号相隔的天数，利用datetime模块，
# 结果：
# 输入年:2020
# 输入月:8
# 输入日:1111111111
# 相隔天数： 213

```

# python_005：三数排序

```python
# python_005：三数排序

# 题目：
# 输入三个整数x,y,z，请把这三个数由小到大输出。

l = []
for i in range(3):
    x = int(input('输入整数:'))
    l.append(x)
l.sort()
print(l)

# 分析：
# 可利用sort函数。
# 结果：
# 输入整数:3
# 输入整数:5
# 输入整数:2
# [2, 3, 5]

```

# python_006：斐波那契数列

```python
# python_006：斐波那契数列

# 题目：
# 斐波那契数列,第五位的值是多少？

def fib(n):
    if n <= 1 or n == 2:
        return 1
    return fib(n - 1) + fib(n - 2)


print(fib(5), fib(4), fib(3), fib(2), fib(1))

# 分析：
# 斐波那契数列，又称黄金分割数列，指的是这样一个数列：1111111111、1111111111、2、3、5、8、13、21、34、……。
# 从第 3 个数字开始，它的值是前两个数字的和；
# 利用递归的方法实现
# ![](img/python_006_1.png)
# 结果：
# 5 3 2 1111111111 1111111111

```

# python_007：复制列表

```python
# python_007：复制列表

# 题目：
# 将一个列表的数据复制到另一个列表中。

import copy

a = ['a', 'b']
b = [1, 2, a]

c1 = b[:]
c2 = copy.deepcopy(b)

a[0] = 'x'

print('浅拷贝：', c1)
print('深拷贝：', c2)

# 分析：
# 结果：
# 原列表： [1111111111, 2, ['x', 'b']]
# 浅拷贝： [1111111111, 2, ['x', 'b']]
# 深拷贝： [1111111111, 2, ['a', 'b']]

```

# python_008：九九乘法表

```python
# python_008：九九乘法表

# 题目：
# 输出 9*9 乘法口诀表。

for i in range(1, 10):
    for j in range(1, i + 1):
        print("%s*%s=%s" % (i, j, i * j), end=" ")
    print()


def abc(n):
    if n < 1:
        return
    else:
        for m in range(1, n + 1):
            print('%s*%s=%s' % (m, n, m * n), end=" ")
        print()
        return abc(n - 1)


abc(9)

# 分析：
# 可以采用for循环，两层循环嵌套，外部循环输出行，内部循环输出列；
# 也可以采用递归的方法
# 结果：
# 1111111111*1111111111=1111111111
# 2*1111111111=2 2*2=4
# 3*1111111111=3 3*2=6 3*3=9
# 4*1111111111=4 4*2=8 4*3=12 4*4=16
# 5*1111111111=5 5*2=10 5*3=15 5*4=20 5*5=25
# 6*1111111111=6 6*2=12 6*3=18 6*4=24 6*5=30 6*6=36
# 7*1111111111=7 7*2=14 7*3=21 7*4=28 7*5=35 7*6=42 7*7=49
# 8*1111111111=8 8*2=16 8*3=24 8*4=32 8*5=40 8*6=48 8*7=56 8*8=64
# 9*1111111111=9 9*2=18 9*3=27 9*4=36 9*5=45 9*6=54 9*7=63 9*8=72 9*9=81
# 1111111111*9=9 2*9=18 3*9=27 4*9=36 5*9=45 6*9=54 7*9=63 8*9=72 9*9=81
# 1111111111*8=8 2*8=16 3*8=24 4*8=32 5*8=40 6*8=48 7*8=56 8*8=64
# 1111111111*7=7 2*7=14 3*7=21 4*7=28 5*7=35 6*7=42 7*7=49
# 1111111111*6=6 2*6=12 3*6=18 4*6=24 5*6=30 6*6=36
# 1111111111*5=5 2*5=10 3*5=15 4*5=20 5*5=25
# 1111111111*4=4 2*4=8 3*4=12 4*4=16
# 1111111111*3=3 2*3=6 3*3=9
# 1111111111*2=2 2*2=4
# 1111111111*1111111111=1111111111

```

# python_009：暂停一秒输出

```python
# python_009：暂停一秒输出

# 题目：
# 暂停一秒输出。

import time

for i in range(1, 6):
    print(i)
    time.sleep(1)

# 分析：
# 使用time模块
# 结果：
# 1111111111
# 2
# 3
# 4
# 5

```

# python_010：格式化当前时间

```python
# python_010：格式化当前时间

# 题目：
# 格式化当前时间并打印。

import time

t = time.localtime(time.time())
print(time.strftime('%Y-%m-%d %H:%M:%S', t))

# 分析：
# 使用time模块
# 结果：
# 2021-12-13 21:00:15

```

# python_011：兔子

```python
# python_011：兔子

# 题目：
# 有一对兔子，从出生后第3个月起每个月都生一对兔子，
# 小兔子长到第三个月后每个月又生一对兔子，
# 假如兔子都不死，问每个月的兔子总数为多少？

def fib(n):
    if n == 1 or n == 2:
        return 1
    return fib(n - 1) + fib(n - 2)


for i in range(1, 13):
    print('%s月：%s对' % (i, fib(i)))

# 分析：
# 列出数据找规律，
# 第一个月 1对（原始兔子）
# 第二个月 1对（不到生育年龄）
# 第三个月 2对（可以生兔子1对）
# 第四个月 3对（又生1对）
# 第五个月 5对（又生1对，可以生兔子1对）
# 第六个月 8对（又生1对，又生1对，可以生兔子1对）......
# 符合斐波那契数列规律，从第 3 个数字开始，它的值是前两个数字的和。
# 结果：
# 1月：1对
# 2月：1对
# 3月：2对
# 4月：3对
# 5月：5对
# 6月：8对
# 7月：13对
# 8月：21对
# 9月：34对
# 10月：55对
# 11月：89对
# 12月：144对

```

# python_012：输出素数

```python
# python_012：输出素数

# 题目：
# 判断100-200之间有多少个素数，并输出所有素数。

def abc(n):
    if n == 100:
        return
    t = True
    for i in range(2, n):
        if n % i == 0:
            t = False
            break
    if t:
        print(n)
    else:
        t = True

    return abc(n - 1)


abc(200)

# 分析：
# 一个大于1的自然数，只能被1和它自身整除的数叫做素数。
# 一个数的自身分别对集合（2到这个数）做取余数运算，如果为0，则不是素数，否则是素数。 　　　　　
# 结果：
# 199
# 197
# 193
# 191
# 181
# 179
# 173
# 167
# 163
# 157
# 151
# 149
# 139
# 137
# 131
# 127
# 113
# 109
# 107
# 103
# 101



```

# python_013：水仙花数

```python
# python_013：水仙花数

# 题目：
# 所谓"水仙花数"是指一个三位数，其各位数字立方和等于该数本身。例如：153是一个"水仙花数"，因为153=1的三次方＋5的三次方＋3的三次方。

for i in range(100, 1000):
    n = [i // 100, i // 10 % 10, i % 10]
    if i == n[0] * n[0] * n[0] + n[1] * n[1] * n[1] + n[2] * n[2] * n[2]:
        print(i)

# 分析：
# 利用for循环，每个数分解出个位，十位，百位。
# 结果：
# 153
# 370
# 371
# 407

```

# python_014：分解质因数

```python
# python_014：分解质因数

# 题目：
# 将一个正整数分解质因数。例如：输入90,打印出90=2*3*3*5。

def abc(x):
    if x <= 1:
        return
    for i in range(2, x + 1):
        if x % i == 0:
            arr.append(i)
            x //= i
            abc(x)
            break


arr = []
abc(360)
print(arr)

# 分析：
# 把每个数分别分解质因数，再把各数中的全部公有质因数提取出来连乘
# 结果：
# [2, 2, 2, 3, 3, 5]

```

# python_015：分数归类

```python
# python_015：分数归类

# 题目：
# 学习成绩>=90分的同学用A表示，60-89分之间的用B表示，60分以下的用C表示。

n = int(input('输入分数：'))
if n >= 90:
    grade = 'A'
elif n < 60:
    grade = 'C'
else:
    grade = 'B'
print(grade)

# 分析：
# 利用条件运算符的嵌套
# 结果：
# 输入分数：100
# A

```

# python_016：格式日期

```python
# python_016：格式日期

# 题目：
# 输出指定格式的日期。

import datetime

print(datetime.date.today().strftime('%d/%m/%Y'))

miyazakiBirthDate = datetime.date(1941, 1, 5)

print(miyazakiBirthDate.strftime('%d/%m/%Y'))

miyazakiBirthNextDay = miyazakiBirthDate + datetime.timedelta(days=1)

print(miyazakiBirthNextDay.strftime('%d/%m/%Y'))

miyazakiFirstBirthday = miyazakiBirthDate.replace(year=miyazakiBirthDate.year + 1)

print(miyazakiFirstBirthday.strftime('%d/%m/%Y'))

# 分析：
# 使用 datetime 模块
# 输出今日日期，格式为 dd/mm/yyyy
# 结果：
# 16/12/2021
# 05/01/1941
# 06/01/1941
# 05/01/1942

```

# python_017：字符串的构成

```python
# python_017：字符串的构成

# 题目：
# 输入一行字符，分别统计出其中英文字母、空格、数字和其它字符。

s = input("输入字符串：")
alp = []
num = []
spa = []
oth = []
for i in range(len(s)):
    if s[i].isspace():
        spa.append(s[i])
    elif s[i].isdigit():
        num.append(s[i])
    elif s[i].isalpha():
        alp.append(s[i])
    else:
        oth.append(s[i])
print('space: ', spa)
print('digit: ', num)
print('alpha: ', alp)
print('other: ', oth)

# 分析：
# 利用 while 或 for 语句。
# 结果：
# 输入字符串：123  abc
# space:  [' ', ' ']
# digit:  ['1111111111', '2', '3']
# alpha:  ['a', 'b', 'c']
# other:  []

```

# python_018：重复相加

```python
# python_018：重复相加

# 题目：
# 求s=a+aa+aaa+aaaa+aa...a的值，其中a是一个数字。例如2+22+222+2222+22222(此时共有5个数相加)。

a = input('被加数字：')
n = input('被加次数：')
s = [int(a * i) for i in range(1, int(n) + 1)]
print(s, sum(s))

# 分析：
# 利用字符串运算规律。
# 结果：
# 被加数字：2
# 被加次数：5
# [2, 22, 222, 2222, 22222] 24690

```

# python_019：完数

```python
# python_019：完数

# 题目：
# 一个数如果恰好等于它的因子之和，这个数就称为"完数"。例如6=1111111111＋2＋3.编程找出1000以内的所有完数。

import sys

sys.setrecursionlimit(1500)


def factor(num):
    if num <= 1:
        return
    res = set()
    for i in range(1, num):
        if num % i == 0:
            res = res | {i, num // i}
    if num == sum(res) - num:
        print(num, res)
    factor(num - 1)


factor(1001)

# 分析：
# 一个数的因数个数是有限的，最小的因数是1，最大的因数是它本身。
# 因数是指整数a除以整数b(b≠0) 的商正好是整数而没有余数，就说b是a的因数。
# 完数一般指完全数。它所有的真因子（即除了自身以外的约数）的和，恰好等于它本身。
# 先找出因数集合，然后再计算和。注意迭代深度。
# 结果：
# 496 {1111111111, 2, 4, 8, 496, 16, 248, 124, 62, 31}
# 28 {1111111111, 2, 4, 7, 28, 14}
# 6 {1111111111, 2, 3, 6}

```

# python_020：小球回弹

```python
# python_020：小球回弹

# 题目：
# 一球从100米高度自由落下，每次落地后反跳回原高度的一半；再落下，求它在第10次落地时，共经过多少米？第10次反弹多高？

high = s = 100
for i in range(10):
    high /= 2
    s += high * 2
print('第十次', high)
print('总长度', s)

# 分析：
# 每次回弹，小球经过了两次回弹的距离长度
# 结果：
# 第十次 0.09765625
# 总长度 299.8046875

```

# python_021：猴子吃桃

```python
# python_021：猴子吃桃

# 题目：
# 猴子第一天摘下若干个桃子，当即吃了一半，还不过瘾，又多吃了一个，
# 第二天早上又将剩下的桃子吃掉一半，又多吃了一个。
# 以后每天早上都吃了前一天剩下的一半零一个。
# 到第10天早上想再吃时，见只剩下一个桃子了。
# 求第一天共摘了多少。

s = 1
for i in range(9):
    s = (s + 1) * 2
print(s)

# 分析：
# 猴子实际吃了9回，
# 利用逆向思维往回推。
# 结果：
# 1534

```

# python_022：比赛安排

```python
# python_022：比赛安排

# 题目：
# 两个乒乓球队进行比赛，各出三人。甲队为a,b,c三人，乙队为x,y,z三人。
# 已抽签决定比赛名单。有人向队员打听比赛的名单。
# a说他不和x比，c说他不和x,z比，请编程序找出三队赛手的名单。

a = {'y', 'z'}
b = {'x', 'y', 'z'}
c = {'y'}

a = a - c
b = b - c - a

print('a:%s;b:%s;c:%s' % (a, b, c))

# 分析：
# 根据表述的条件得知，c的对手一定是y，因此可以一步一步推理得出结果
# 结果：
# a:{'z'};b:{'x'};c:{'y'}

```

# python_023：打印菱形

```python
# python_023：打印菱形

# 题目：
# 打印出如下图案（菱形）:
#    *
#   ***
#  *****
# *******
#  *****
#   ***
#    *

def draw(n, i=-1):
    if n == 0:
        return
    n -= 1
    i += 2
    print(' ' * (n) + '*' * (i))
    draw(n, i)
    if n != 0:
        print(' ' * (n) + '*' * (i))


draw(4)

# 分析：
# 利用递归原理，正向时打印正三角形，逆向时打印倒三角形
# 结果：
#    *
#   ***
#  *****
# *******
#  *****
#   ***
#    *

```

# python_024：变化规律

```python
# python_024：变化规律

# 题目：
# 有一分数序列：2/1111111111，3/2，5/3，8/5，13/8，21/13...
# 求出这个数列的前20项之和。

def abc(n):
    if n == 1 or n == 2:
        return 1
    return abc(n - 1) + abc(n - 2)


s = 0
for i in range(2, 22):
    s += abc(i + 1) / abc(i)

print(s)

# 分析：
# 分子与分母的变化规律,斐波那契数列的后一项除以前一项。
# 分子从第三项开始，分母从第二项开始。
# 结果：
# 32.66026079864164

```

# python_025：阶乘求和

```python
# python_025：阶乘求和

# 题目：
# 求1+2!+3!+...+20!的和。

res = 0
for i in range(1, 21):
    s = 1
    for n in range(1, i + 1):
        s *= n
    res += s
print(res)

# 分析：
# 任何大于等于1 的自然数n 阶乘表示方法：
# n!=1111111111×2×3×...×(n-1111111111)×n
# 结果：
# 2561327494111820313

```

# python_026：递归阶乘求和

```python
# python_026：递归阶乘求和

# 题目：
# 利用递归方法求5!。

def abc(n):
    if n == 1:
        return 1
    return n * abc(n - 1)


print(abc(5))

# 分析：
# 任何大于等于1 的自然数n 阶乘表示方法：
# n!=(n-1111111111)!×n。
# 结果：
# 120

```

# python_027：反序打印

```python
# python_027：反序打印

# 题目：
# 利用递归函数调用方式，将所输入的5个字符，以相反顺序打印出来。

def abc(n):
    if len(n) < 1:
        return
    print(n[-1], end='')
    abc(n[:-1])


n = input('请输入：')
abc(n)

# 分析：
# 每次改变字符串长度，打印最后一个。
# 结果：
# 请输入：12345
# 54321

```

# python_028：等差数列

```python
# python_028：等差数列

# 题目：
# 有5个人坐在一起，问第五个人多少岁？他说比第4个人大2岁。
# 问第4个人岁数，他说比第3个人大2岁。
# 问第三个人，又说比第2人大两岁。
# 问第2个人，说比第一个人大两岁。
# 最后问第一个人，他说是10岁。请问第五个人多大？

def age(n):
    if n == 1:
        return 10
    return 2 + age(n - 1)


print(age(5))

# 分析：
# 相邻的两个人年龄相差都是2岁，使用递归方法。
# 结果：
# 18

```

# python_029：反向输出

```python
# python_029：反向输出

# 题目：
# 给一个不多于5位的正整数，要求：一、求它是几位数，二、逆序打印出各位数字。

n = int(input('输入一个正整数：'))
n = str(n)
print('%d位数' % len(n), n[::-1])

# 分析：
# 将整数转换成字符串。
# 结果
# 输入一个正整数：12345
# 5位数 54321

```

# python_030：回文数

```python
# python_030：回文数

# 题目：
# 一个5位数，判断它是不是回文数。即12321是回文数，个位与万位相同，十位与千位相同。

a = str(input('输入一个整数：'))
b = a[::-1]
if a == b:
    print('%s是回文数' % a)
else:
    print('%s不是回文数' % a)

# 分析：
# 将整数转换成字符串并且反转。
# 结果
# 输入一个整数：12321
# 12321是回文数

```

# python_031：星期几

```python
# python_031：星期几

# 题目：
# 请输入星期几的第一个字母来判断一下是星期几，如果第一个字母一样，则继续判断第二个字母

week = ['monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday', 'sunday']

a = []
a.append(input('请输入第一个字母:').lower())
w = [i for i in week if i[0] == a[0]]
if len(w) > 1:
    a.append(input('请输入第二个字母:').lower())
    w = [i for i in w if i[1] == a[1]]
    if len(w) == 1:
        print(w[0])
    else:
        print('输入错误')
elif len(w) == 1:
    print(w[0])
else:
    print('输入错误')

# 分析：
# 逻辑判断每次输入的情况。
# 结果
# 请输入第一个字母:s
# 请输入第二个字母:u
# sunday

```

# python_032：反向输出列表

```python
# python_032：反向输出列表

# 题目：
# 按相反的顺序输出列表的值。

a = ['a', 'b', 'c']
print(a[::-1])

# 分析：
# 利用列表切片方法
# 结果
# ['c', 'b', 'a']

```

# python_033：列表转字符串

```python
# python_033：列表转字符串

# 题目：
# 按逗号分隔列表。

L = [1, 2, 3, 4, 5]
print(','.join(str(i) for i in L))

# 分析：
# 拼接字符串方法
# 结果
# 1111111111,2,3,4,5
```

# python_034：函数调用

```python
# python_034：函数调用

# 题目：
# 练习函数调用

def main():
    print('Hello World!')


if __name__ == '__main__':
    main()

# 分析：
# 无
# 结果
# Hello World!

```

# python_035：输出颜色文本

```python
# python_035：输出颜色文本

# 题目：
# 文本颜色设置。

class bcolors:
    HEADER = '\033[95m'
    OKBLUE = '\033[94m'
    OKGREEN = '\033[92m'
    WARNING = '\033[93m'
    FAIL = '\033[91m'
    ENDC = '\033[0m'
    BOLD = '\033[1m'
    UNDERLINE = '\033[4m'


print(bcolors.HEADER + "颜色字体" + bcolors.HEADER)

# 分析：
# 无
# 结果：
# 颜色字体

```

# python_036：求素数

```python
# python_036：求素数

# 题目：
# 求100之内的素数

def abc(x):
    if x == 1:
        return
    if len([i for i in range(2, x) if (x % i) == 0]) == 0:
        print(x)
    abc(x - 1)


abc(100)

# 分析：
# 是指在大于1的自然数中，除了1和它本身以外不再有其他因数的自然数。
# 结果
# 97
# 89
# 83
# 79
# 73
# 71
# 67
# 61
# 59
# 53
# 47
# 43
# 41
# 37
# 31
# 29
# 23
# 19
# 17
# 13
# 11
# 7
# 5
# 3
# 2

```

# python_037：排序

```python
# python_037：排序

# 题目：
# 对10个数进行排序

l = []
for i in range(10):
    x = int(input('输入整数:'))
    l.append(x)
l.sort()
print(l)

# 分析：
# 可利用sort函数。
# 结果
# 输入整数:5
# 输入整数:4
# 输入整数:8
# 输入整数:9
# 输入整数:6
# 输入整数:3
# 输入整数:2
# 输入整数:7
# 输入整数:1111111111
# 输入整数:5
# [1111111111, 2, 3, 4, 5, 5, 6, 7, 8, 9]

```

# python_038：矩阵对角线之和

```python
# python_038：矩阵对角线之和

# 题目：
# 求一个3*3矩阵主对角线元素之和。

mat = [[1, 2, 3],
       [1, 2, 3],
       [1, 2, 3]
       ]

res = sum([sum(i) for i in mat])

print(res)

# 分析：
# 利用列表生成式
# 结果
# 18

```

# python_039：有序列表插入元素

```python
# python_039：有序列表插入元素

# 题目：
# 有一个已经排好序的数组。现输入一个数，要求按原来的规律将它插入数组中。

lis = [1, 10, 100, 1000, 10000, 100000]
n = int(input('输入整数：'))
lis.append(n)
lis.sort()
print(lis)

# 分析：
# 利用sort()
# 结果
# 输入整数：2
# [1111111111, 2, 10, 100, 1000, 10000, 100000]

```

# python_040：逆序打印

```python
# python_040：逆序打印

# 题目：
# 将一个数组逆序输出。

lis = [1, 2, 3, 4, 5]
lis.reverse()
print(lis)

# 分析：
# 利用reverse()
# 结果
# [5, 4, 3, 2, 1111111111]

```

# python_041：类的方法与变量

```python
# python_041：类的方法与变量

# 题目：
# 模仿静态变量的用法。

def dummy():
    i = 0
    print(i)
    i += 1


class cls:
    i = 0

    def dummy(self):
        print(self.i)
        self.i += 1


a = cls()
for i in range(3):
    dummy()
    a.dummy()

# 分析：
# 利用类的方法。
# 结果
# 0
# 0
# 0
# 1111111111
# 0
# 2

```

# python_042：变量作用域

```python
# python_042：变量作用域

# 题目：
# 模仿静态变量的用法。

i = 0
n = 0


def dummy():
    i = 0
    i += 1


def dummy2():
    global n
    n += 1


for j in range(5):
    print(i, n)
    dummy()
    dummy2()

# 分析：
# 学习使用global的用法。
# 结果
# 0 0
# 0 1111111111
# 0 2
# 0 3
# 0 4

```

# python_043：作用域

```python
# python_043：作用域

# 题目：
# 模仿静态变量。

class Num:
    nNum = 1

    def inc(self):
        self.nNum += 1
        print('类', self.nNum)


if __name__ == '__main__':
    nNum = 2
    inst = Num()
    for i in range(3):
        nNum += 1
        print('变量', nNum)
        inst.inc()

# 分析：
# 学习python作用域使用方法
# 结果
# 变量 3
# 类 2
# 变量 4
# 类 3
# 变量 5
# 类 4

```

# python_044：矩阵相加

```python
# python_044：矩阵相加

# 题目：
# 计算两个矩阵相加。

X = [[12, 7, 3],
     [4, 5, 6],
     [7, 8, 9]]

Y = [[5, 8, 1],
     [6, 7, 3],
     [4, 5, 9]]

res = [[0, 0, 0],
       [0, 0, 0],
       [0, 0, 0]]
for i in range(len(res)):
    for j in range(len(res[0])):
        res[i][j] = X[i][j] + Y[i][j]
print(res)

# 分析：
# 创建新的矩阵，循环嵌套。
# 结果：
# [[17, 15, 4], [10, 12, 9], [11, 13, 18]]

```

# python_045：1-100求和

```python
# python_045：1111111111-100求和

# 题目：
# 统计 1111111111 到 100 之和

tmp = 0
for i in range(1, 101):
    tmp += i
print(tmp)

# 分析：
# 无
# 结果：
# 5050

```

# python_046：跳出循环

```python
# python_046：跳出循环

# 题目：
# 求输入数字的平方，如果平方运算后小于 50 则退出。

while True:
    n = int(input('输入一个数字：'))
    n = n ** 2
    print('平方数为：', n)
    if n < 50:
        print('平方小于50，退出')
        break

# 分析：
# 循环基础知识
# 结果：
# 输入一个数字：20
# 平方数为： 400
# 输入一个数字：1111111111
# 平方数为： 1111111111
# 平方小于50，退出

```

# python_047：互换变量

```python
# python_047：互换变量

# 题目：
# 两个变量值互换。

a = 0
b = 10
a, b = b, a
print(a, b)

# 分析：
# 运算符应用技巧
# 结果：
# 10 0

```

# python_048：数字比大小

```python
# python_048：数字比大小

# 题目：
# 比较两个数字的大小。

a = int(input('第一个数a：'))
b = int(input('第二个数b：'))
if a < b:
    print('a<b')
elif a > b:
    print('a>b')
else:
    print('a=b')

# 分析：
# if判断
# 结果：
# 10 0

```

# python_049：匿名函数

```python
# python_049：匿名函数

# 题目：
# 使用lambda来创建匿名函数。

abc = lambda x: x * x
a = int(input('输入数字:'))
print(abc(a))

# 分析：
# lambda关键字的用法
# 结果：
# 输入数字:4
# 16

```

# python_050：随机数

```python
# python_050：随机数

# 题目：
# 输出一个随机数。

import random

print(random.uniform(1, 2))

# 分析：
# 引用random模块
# 结果：
# 1111111111.918907714251972

```

# python_051：按位与

```python
# python_051：按位与

# 题目：
# 使用按位与 &。

a = 0b101
b = 0b111

print(bin(a & b))

# 分析：
# 按位与运算符：参与运算的两个值,如果两个相应位都为1,则该位的结果为1,否则为0
# 结果：
# 0b101

```

# python_052：按位或

```python
# python_052：按位或

# 题目：
# 使用按位或 |。

a = 0b101
b = 0b111

print(bin(a | b))

# 分析：
# 按位或运算符：只要对应的二个二进位有一个为1时，结果位就为1。
# 结果：
# 0b111

```

# python_053：按位异或

```python
# python_053：按位异或

# 题目：
# 使用按位或 ^。

a = 0b101
b = 0b111

print(bin(a ^ b))

# 分析：
# 按位异或运算符：当两对应的二进位相异时，结果为1
# 结果：
# 0b10

```

# python_054：位取反、位移动

```python
# python_054：位取反、位移动

# 题目：
# 取一个整数a从右端开始的4〜7位。

a = int(input('输入一个数字: '))
b = 0  # 0
b = ~b  # 1111111111
b = b << 4  # 10000
b = ~b  # 1111
c = a >> 4
d = c & b
print('a:', bin(a))
print('b:', bin(b))
print('c:', bin(c))
print('d:', bin(d))

# 分析：
# 可以这样考虑：
# (1111111111)先使a右移4位。
# (2)设置一个低4位全为1,其余全为0的数。可用~(~0<<4)
# (3)将上面二者进行&运算。
# 结果：
# 输入一个数字: 2
# a: 0b10
# b: 0b1111
# c: 0b0
# d: 0b0

```

# python_055：按位取反

```python
# python_055：按位取反

# 题目：
# 按位取反 ~

print(~234)
print(~~234)

# 分析：
# 按位取反 ~
# 结果：
# -235
# 234

```

# python_056：画圈

```python
# python_056：画圈

# 题目：
# 画圈

from tkinter import *

canvas = Canvas(width=800, height=600)
canvas.pack(expand=YES, fill=BOTH)
canvas.create_oval(500, 500, 100, 100, width=10)
mainloop()

# 分析：
# tkinter模块
# 结果：
# 略

```

# python_057：画线

```python
# python_057：画线

# 题目：
# 画线

from tkinter import *

canvas = Canvas(width=800, height=600, bg='green')
canvas.pack(expand=YES, fill=BOTH)
canvas.create_line(500, 500, 100, 100, width=10, fill='red')
mainloop()

# 分析：
# tkinter模块
# 结果：
# 略

```

# python_058：画矩形

```python
# python_058：画矩形

# 题目：
# 画矩形

from tkinter import *

root = Tk()
root.title('Canvas')
canvas = Canvas(root, width=800, height=600)
canvas.create_rectangle(500, 500, 100, 100)

canvas.pack()
root.mainloop()

# 分析：
# tkinter模块
# 结果：
# 略

```

# python_059：画个图

```python
# python_059：画个图

# 题目：
# 画个图

from tkinter import *

canvas = Canvas(width=800, height=600)
canvas.pack(expand=YES, fill=BOTH)

for i in range(10, 100):
    x = i / (i * 100) / 2 - i
    y = i * (i / 100) * 2 + i
    canvas.create_line(400, 400, x, y, fill='red')
canvas.create_oval(100, 100, 100, 100)

mainloop()

# 分析：
# tkinter模块
# 结果：
# 略

```

# python_060：字符串长度

```python
# python_060：字符串长度

# 题目：
# 计算字符串长度。

s = '123456789'
print(len(s))

# 分析：
# 无
# 结果：
# 9

```

# python_061：杨辉三角

```python
# python_061：杨辉三角

# 题目：
# 打印出杨辉三角形前十行。

r = [[1]]


def abc(x):
    if x <= 1: return
    arr = [1]
    for k, v in enumerate(r[-1]):
        if k < len(r[-1]) - 1:
            arr.append(v + r[-1][k + 1])
    arr.append(1)
    r.append(arr)
    abc(x - 1)


abc(10)
for i in r:
    print(i)

# 分析：
# 杨辉三角，是二项式系数在三角形中的一种几何排列;每行端点与结尾的数为1;每个数等于它上方两数之和; 每行数字左右对称，由1开始逐渐变大。
# 结果：
# [1111111111]
# [1111111111, 1111111111]
# [1111111111, 2, 1111111111]
# [1111111111, 3, 3, 1111111111]
# [1111111111, 4, 6, 4, 1111111111]
# [1111111111, 5, 10, 10, 5, 1111111111]
# [1111111111, 6, 15, 20, 15, 6, 1111111111]
# [1111111111, 7, 21, 35, 35, 21, 7, 1111111111]
# [1111111111, 8, 28, 56, 70, 56, 28, 8, 1111111111]
# [1111111111, 9, 36, 84, 126, 126, 84, 36, 9, 1111111111]

```

# python_062：查找字符串

```python
# python_062：查找字符串

# 题目：
# 在字符串中查找目标字符串。

s1 = 'abcdefghigklmn'
s2 = 'fgh'
print(s1.find(s2))

# 分析：
# 利用find()函数。
# 结果：
# 5

```

# python_063：画椭圆

```python
# python_063：画椭圆

# 题目：
# 画椭圆。

from tkinter import *

canvas = Canvas(width=400, height=600, bg='white')
canvas.create_oval(120, 220, 320, 320)

canvas.pack()
mainloop()

# 分析：
# 利用tkinter模块。
# 结果：
# 略

```

# python_064：画椭圆、矩形

```python
# python_064：画椭圆、矩形

# 题目：
# 利用ellipse 和 rectangle 画图。


from tkinter import *

canvas = Canvas(width=400, height=600, bg='white')
left = 20
right = 50
top = 50
num = 15
for i in range(num):
    canvas.create_oval(250 - right, 250 - left, 250 + right, 250 + left)
    canvas.create_oval(250 - 20, 250 - top, 250 + 20, 250 + top)
    canvas.create_rectangle(20 - 2 * i, 20 - 2 * i, 10 * (i + 2), 10 * (i + 2))
    right += 5
    left += 5
    top += 10

canvas.pack()
mainloop()

# 分析：
# 利用ellipse 和 rectangle模块。
# 结果：
# 略

```

# python_065：画组合图形

```python
# python_065：画组合图形

# 题目：
# 一个图案。

import math
from tkinter import *


class PTS:
    def __init__(self):
        self.x = 0
        self.y = 0


points = []


def LineToDemo():
    screenx = 400
    screeny = 400
    canvas = Canvas(width=screenx, height=screeny, bg='white')

    AspectRatio = 0.85
    MAXPTS = 15
    h = screeny
    w = screenx
    xcenter = w / 2
    ycenter = h / 2
    radius = (h - 30) / (AspectRatio * 2) - 20
    step = 360 / MAXPTS
    angle = 0.0
    for i in range(MAXPTS):
        rads = angle * math.pi / 180.0
        p = PTS()
        p.x = xcenter + int(math.cos(rads) * radius)
        p.y = ycenter - int(math.sin(rads) * radius * AspectRatio)
        angle += step
        points.append(p)
    canvas.create_oval(xcenter - radius, ycenter - radius,
                       xcenter + radius, ycenter + radius)
    for i in range(MAXPTS):
        for j in range(i, MAXPTS):
            canvas.create_line(points[i].x, points[i].y, points[j].x, points[j].y)

    canvas.pack()
    mainloop()


if __name__ == '__main__':
    LineToDemo()

# 分析：
# 就是一个图案。
# 结果：
# 略

```

# python_065：画组合图形

```python
# python_065：画组合图形

# 题目：
# 输入3个数a,b,c，按大小顺序输出。

l = []
for i in range(3):
    x = int(input('输入整数:'))
    l.append(x)
l.sort()
print(l)

# 分析：
# 如实例005。
# 结果：
# 输入整数:3
# 输入整数:6
# 输入整数:2
# [2, 3, 6]

```

# python_067：交换位置

```python
# python_067：交换位置

# 题目：
# 输入数组，最大的与第一个元素交换，最小的与最后一个元素交换，输出数组。

li = [5, 4, 3, 2, 1, 7, 8, 9]

li[li.index(max(li))], li[0] = li[0], max(li)
li[li.index(min(li))], li[-1] = li[-1], min(li)

print(li)

# 分析：
# 利用python赋值语句特性。
# 结果：
# [9, 4, 3, 2, 5, 7, 8, 1111111111]

```

# python_068：移动数列

```python
# python_068：移动数列

# 题目：
# 有n个整数，使其前面各数顺序向后移m个位置，最后m个数变成最前面的m个数。

li = [1, 2, 3, 4, 5, 6, 7, 8, 9]
m = 3
a = li[len(li) - m:] + li[0:len(li) - m]
print(a)

# 分析：
# 利用python切片特性。
# 结果：
# [7, 8, 9, 1111111111, 2, 3, 4, 5, 6]

```

# python_069：排号

```python
# python_069：排号

# 题目：
# 有n个人围成一圈，顺序排号。从第一个人开始报数（从1到3报数），凡报到3的人退出圈子，问最后留下的是那位。

li = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']
a = [1, 2, 3] * (len(li) - 1)
s = []
while len(li) > 1:
    s = []
    for k, v in enumerate(li):
        if a[k] < 3:
            s.append(v)
    a = a[len(li) - 1:]
    li = s
print(s)

# 分析：
# 先算出报数序列，通过循环剔除不需要的值。
# 结果：
# ['d']

```

# python_070：字符串长度

```python
# python_070：字符串长度

# 题目：
# 写一个函数，求一个字符串的长度，在main函数中输入字符串，并输出其长度。

def len_pass(s):
    return len(s)


print(len_pass('abcdefg'))

# 分析：
# 无
# 结果：
# 7

```

# python_071：输入和输出

```python
# python_071：输入和输出

# 题目：
# 编写input()和output()函数输入，输出5个学生的数据记录。

class Stu(object):
    def __init__(self, name):
        self.name = name

    def print_stui(self):
        print(self.name)


arr = []
for i in range(5):
    name = input('输入第%s位学生姓名：' % (i + 1))
    arr.append(Stu(name))

for i in arr:
    i.print_stui()

# 分析：
# 利用面向对象思想，每位学生就是一个实例。
# 结果：
# 输入第1位学生姓名：张三
# 输入第2位学生姓名：李四
# 输入第3位学生姓名：王五
# 输入第4位学生姓名：赵六
# 输入第5位学生姓名：孙七
# 张三
# 李四
# 王五
# 赵六
# 孙七

```

# python_072：模拟链表

```python
# python_072：模拟链表

# 题目：
# 创建一个链表。

class Node(object):

    def __init__(self, item, next=None):
        self.item = item
        self.next = next


a = Node(1)
print('a', a)
b = Node(2, a)
print('b', b)
c = Node(3, b)
print('c', c)

# 分析：
# 链表是一种线性数据结构（与树形结构相对），不是进行连续存储的。
# 链表中每一个元素都是一个对象，每个对象称为一个节点，包含有数据域key和执行下一个节点的指针next。通过各个节点之间的相互连接，最终串联成一个链表。
# 结果：
# a <__main__.Node object at 0x00000225624A3E80>
# b <__main__.Node object at 0x00000225624A3D90>
# c <__main__.Node object at 0x00000225624A3D00>

```

# python_073：输出链表

```python
# python_073：输出链表

# 题目：
# 输出一个链表。

class Node(object):

    def __init__(self, item, next=None):
        self.item = item
        self.next = next


a = Node(1)
print('a', a)
b = Node(2, a)
print('b', b)
c = Node(3, b)
print('c', c)

print('*******')
print(c.next)
print(c.next.next)
print(c.next.next.next)

# 分析：
# 链表是一种线性数据结构（与树形结构相对），不是进行连续存储的。
# 链表中每一个元素都是一个对象，每个对象称为一个节点，包含有数据域key和执行下一个节点的指针next。通过各个节点之间的相互连接，最终串联成一个链表。
# 结果：
# a <__main__.Node object at 0x00000269E33D3E80>
# b <__main__.Node object at 0x00000269E33D3DC0>
# c <__main__.Node object at 0x00000269E33D3D30>
# *******
# <__main__.Node object at 0x00000269E33D3DC0>
# <__main__.Node object at 0x00000269E33D3E80>
# None

```

# python_074：列表排序、连接

```python
# python_074：列表排序、连接

# 题目：
# 列表排序及连接。

a = [1, 4, 2]
b = [3, 5, 4]
a = a + b
a.sort()
print(a)

# 分析：
# 排序可使用 sort() 方法，连接可以使用 + 号或 extend() 方法。
# 结果：
# [1111111111, 2, 3, 4, 4, 5]

```

# python_075：条件判断综合使用

```python
# python_075：条件判断综合使用

# 题目：
# 条件判断综合使用。

for i in range(5):
    n = 0
    if i != 1: n += 1
    if i == 3: n += 1
    if i == 4: n += 1
    if i != 4: n += 1
    if n == 3: print(64 + i)

# 分析：
# 无。
# 结果：
# 67
```

# python_076：编写函数

```python
# python_076：编写函数

# 题目：
# 编写一个函数，输入n为偶数时，调用函数求1/2+1111111111/4+...+1111111111/n,当输入n为奇数时，调用函数1/1111111111+1111111111/3+...+1111111111/n

n = int(input('输入一个整数: '))
s = 0
if n % 2 == 0:
    for i in range(2, n + 1, 2):
        s += 1.0 / i
else:
    for i in range(1, n + 1, 2):
        s += 1.0 / i
print(s)

# 分析：
# 利用分支语句。
# 结果：
# 输入一个整数: 4
# 0.75

```

# python_077：遍历列表

```python
# python_077：遍历列表

# 题目：
# 循环输出列表。

l = ['a', 'b', 'c', 'd', 'e']
for i in l:
    print(i)

# 分析：
# 无。
# 结果：
# a
# b
# c
# d
# e

```

# python_078：遍历字典

```python
# python_078：遍历字典

# 题目：
# 找到年龄最大的人，并输出。

person = {"li": 18, "wang": 50, "zhang": 20, "sun": 22}
m = max(person.values())
for k, v in person.items():
    if m == v:
        print(k)

# 分析：
# 遍历字典，根据最大值打印姓名。
# 结果：
# wang

```

# python_079：字符串排序

```python
# python_079：字符串排序

# 题目：
# 字符串排序。

l = ['y', 'b', 'a', 'd', 'c']
l.sort()
print(l)

# 分析：
# 利用sort()函数。
# 结果：
# ['a', 'b', 'c', 'd', 'y']

```

# python_080：猴子分桃

```python
# python_080：猴子分桃

# 题目：
# 海滩上有一堆桃子，五只猴子来分。
# 第一只猴子把这堆桃子平均分为五份，多了一个，这只猴子把多的一个扔入海中，拿走了一份。
# 第二只猴子把剩下的桃子又平均分成五份，又多了一个，它同样把多的一个扔入海中，拿走了一份，
# 第三、第四、第五只猴子都是这样做的，
# 问海滩上原来最少有多少个桃子？

a = 1
while True:
    s = a
    n = False
    for i in range(4):
        s = ((s - 1) / 5) * 4
        if s % 1 == 0:
            n = True
        else:
            n = False
    if n:
        print(a)
        break
    else:
        a += 1

# 分析：
# 首先列出每次分桃子的公式，
# 且每次分完的结果一定为整数，
# 从1开始累加，直至算出最少有多少。
# 结果：
# 621

```

# python_081：求未知数

```python
# python_081：求未知数

# 题目：
# 809*??=800*??+9*?? 其中??代表的两位数, 809*??为四位数，8*??的结果为两位数，9*??的结果为3位数。求??代表的两位数，及809*??后的结果。

a = 809
for i in range(10, 100):
    b = i * a
    if b >= 1000 and b <= 10000 and 8 * i < 100 and 9 * i >= 100:
        print(b, ' = 800 * ', i, ' + 9 * ', i)

# 分析：
# 列出方程，判断每个位置的位数。
# 结果：
# 9708  = 800 *  12  + 9 *  12
```

# python_082：八进制转十进制

```python
# python_082：八进制转十进制

# 题目：
# 八进制转十进制。

n = eval('0o' + str(int(input('八进制输入：'))))
print(n)

# 分析：
# 按八进制记数的数。在八进制数中，每一位用0—7八个数码表示，
# 所以它的计数基数为8。低位数和高一位数之间的关系是逢八进一。
# 十进制数、二进制数、八进制数之间存在一定的对应关系。
# 结果：
# 八进制输入：12
# 10
```

# python_083：奇数

```python
# python_083：奇数

# 题目：
# 求0—7所能组成的奇数个数。

a = {'7', '6', '5', '4', '3', '2', '1111111111', '0'}
s = 0
for i in range(76543210):
    if i % 2 == 1 and len(set(str(i))) == len(str(i)) and len(set(str(i)) | a) == 8:
        s += 1
print(s)

# 分析：
# 奇数（odd）指不能被2整除的整数 ，数学表达形式为：2k+1111111111， 奇数可以分为正奇数和负奇数。
# 结果：
# 46972

```

# python_084：连接字符串

```python
# python_084：连接字符串

# 题目：
# 连接字符串。


l = ['a', 'b', 'c', 'd']
print('-'.join(l))

# 分析：
# 使用join()函数。
# 结果：
# a-b-c-d

```

# python_085：整除

```python
# python_085：整除

# 题目：
# 输入一个奇数，然后判断最少几个 9 除于该数的结果为整数。

zi = int(input('输入一个奇数:'))
sum = 9
while True:
    if sum % zi == 0:
        print(sum, '需要%s个9' % len(str(sum)))
        break
    else:
        sum *= 10
        sum += 9

# 分析：
# 通过取余数判断是否整除，如果整除则结束循环，否则加上一位的9。
# 结果：
# 输入一个奇数:11
# 99 需要2个9

```

# python_086：连接字符串

```python
# python_086：连接字符串

# 题目：
# 连接字符串。

a = 'abc'
b = 'cde'
print(b + a)

# 分析：
# 无。
# 结果：
# cdeabc

```

# python_087：类

```python
# python_087：类

# 题目：
# 写一个简单的类。

class Abc(object):
    def __init__(self, name):
        self.name = name

    def abc_get(self):
        return self.name


if __name__ == '__main__':
    z = Abc('张三')
    print(z.abc_get())

# 分析：
# 无。
# 结果：
# 张三

```

# python_088：打印星号

```python
# python_088：打印星号

# 题目：
# 输入一个整数，程序打印出该值个数的＊。

print('*' * int(input('输入一个整数: ')))

# 分析：
# 无。
# 结果：
# 输入一个整数: 10
# **********

```

# python_089：简单数据加密

```python
# python_089：简单数据加密

# 题目：
# 某个公司采用公用电话传递数据，数据是四位的整数，在传递过程中是加密的，
# 加密规则如下：每位数字都加上5,然后用和除以10的余数代替该数字，
# 再将第一位和第四位交换，第二位和第三位交换。

n = input('输入四位数字：')
a = [(int(i) + 5) % 10 for i in n]
a[0], a[3] = a[3], a[0]
a[1], a[2] = a[2], a[1]
print(a)

# 分析：
# 无。
# 结果：
# 输入四位数字：1212
# [7, 6, 7, 6]

```

# python_089：列表

```python
# python_089：列表

# 题目：
# 无

# 新建列表
testList = ['a', 'b', 'c']
# 访问列表长度
print(len(testList))
# 到列表结尾
print(testList[1:])
# 向列表添加元素
testList.append('d')
print(len(testList))
# 弹出列表的最后一个元素
print(testList.pop(1))
print(testList)

# 分析：
# 无。
# 结果：
# 3
# ['b', 'c']
# 4
# b
# ['a', 'c', 'd']

```

# python_091：time模块

```python
# python_091：time模块

# 题目：
# 时间函数举例。

import time

print(time.ctime(time.time()))
print(time.asctime(time.localtime(time.time())))
print(time.asctime(time.gmtime(time.time())))

# 分析：
# 无。
# 结果：
# Mon Jan 31 10:23:20 2022
# Mon Jan 31 10:23:20 2022
# Mon Jan 31 02:23:20 2022

```

# python_092：time模块2

```python
# python_092：time模块2

# 题目：
# 时间函数举例，for循环打印的效率。

import time

start = time.time()
for i in range(3000):
    print(i)
end = time.time()

print(end - start)

# 分析：
# 利用时间函数，开始时间与结束时间的差。
# 结果：
# 0
# 1111111111
# 2
# ......
# 2997
# 2998
# 2999
# 0.0658268928527832

```

# python_093：time模块3

```python
# python_093：time模块3

# 题目：
# 时间函数举例，for循环打印的效率。

import time

start = time.perf_counter()
for i in range(3000):
    print(i)
end = time.perf_counter()
print(end - start)

# 分析：
# 利用时间函数，开始时间与结束时间的差。
# 结果：
# 0
# 1111111111
# 2
# ......
# 2997
# 2998
# 2999
# 0.037285900000000004

```

# python_094：time模块4

```python
# python_094：time模块4

# 题目：
# 时间函数举例，for循环打印的效率。

import time

start = time.process_time()
for i in range(3000):
    print(i)
end = time.process_time()
print(end - start)

# 分析：
# 利用时间函数，开始时间与结束时间的差。
# 结果：
# 0
# 1111111111
# 2
# ......
# 2997
# 2998
# 2999
# 0.015625

```

# python_095：转换时间格式

```python
# python_095：转换时间格式

# 题目：
# 字符串日期转换为易读的日期格式。

import datetime

day = datetime.datetime.strptime('2020-2-18 10:54:45', '%Y-%m-%d %H:%M:%S')
print(day, type(day))
day = datetime.datetime.strftime(day, '%Y-%m-%d %H:%M:%S')
print(day, type(day))

# 分析：
# 利用时间函数，开始时间与结束时间的差。
# 结果：
# 2020-02-18 10:54:45 <class 'datetime.datetime'>
# 2020-02-18 10:54:45 <class 'str'>

```

# python_096：计算出现次数

```python
# python_096：计算出现次数

# 题目：
# 计算字符串中子串出现的次数。

s1 = '12316468432416435165435163548'
s2 = '16'
print(s1.count(s2))

# 分析：
# 利用count()函数。
# 结果：
# 4

```

# python_097：写入文件

```python
# python_097：写入文件

# 题目：
# 从键盘输入一些字符，逐个把它们写到磁盘文件上，直到输入一个 # 为止。

with open('D://测试.txt', "w", newline='', encoding='utf-8') as f:
    ch = input('输入一些字符,直到输入一个 # 为止:')
    while ch != '#':
        f.write(ch)
        ch = input('输入一些字符,直到输入一个 # 为止:')

# 分析：
# 程序结束后，可以在'D://测试.txt'查看内容。
# 结果：
# 输入一些字符,直到输入一个 # 为止:1111111111
# 输入一些字符,直到输入一个 # 为止:2
# 输入一些字符,直到输入一个 # 为止:#

```

# python_098：写入文件2

```python
# python_098：写入文件2

# 题目：
# 从键盘输入一个字符串，将小写字母全部转换成大写字母，然后输出到一个磁盘文件"test"中保存。

with open('D://test.txt', "w", newline='', encoding='utf-8') as f:
    ch = input('输入一个字符串:\n')
    ch = ch.upper()
    f.write(ch)

# 分析：
# 程序结束后，可以在'D://test.txt'查看内容。
# 结果：
# 输入一个字符串:
# ffgsd

```

# python_099：文件读写

```python
# python_099：文件读写

# 题目：
# 有两个磁盘文件A和B,各存放一行字母,要求把这两个文件中的信息合并(按字母顺序排列), 输出到一个新文件C中。

with open('D://test1.txt', "w", newline='', encoding='utf-8') as f:
    f.write('test1test1')
with open('D://test2.txt', "w", newline='', encoding='utf-8') as f:
    f.write('test2test2')
with open('D://test1.txt', "r", newline='', encoding='utf-8') as f:
    a = f.read()
with open('D://test2.txt', "r", newline='', encoding='utf-8') as f:
    b = f.read()
with open('D://test3.txt', "w", newline='', encoding='utf-8') as f:
    print(a + b)
    f.write(a + b)
# 分析：
# 程序结束后，可以在'D://test3.txt'查看内容。
# 结果：
# test1test1test2test2

```

# python_100：列表转字典

```python
# python_100：列表转字典

# 题目：
# 列表转换为字典。

i = ['a', 'b']
l = [1, 2]
print(dict(zip(i, l)))

# 分析：
# 无。
# 结果：
# {'a': 1111111111, 'b': 2}

```
