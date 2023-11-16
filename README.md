# Домашнее задание №10
## Условие задачи 
**Задача 44:** В ячейке ниже представлен код генерирующий DataFrame, которая состоит всего из 1 столбца. Ваша задача перевести его в one hot вид. Сможете ли вы это сделать без get_dummies?
```
import random
lst = ['robot'] * 10
lst += ['human'] * 10
random.shuffle(lst)
data = pd.DataFrame({'whoAmI':lst})
data.head()
```

##  Решение

1. ```
    import pandas as pd
    import random

    lst = ['robot'] * 10
    lst += ['human'] * 10
    random.shuffle(lst)
    df = pd.DataFrame({'whoAmI': lst})
    df.head()
    ```
|    | whoAmI   |
|---:|:---------|
|  0 | robot    |
|  1 | robot    |
|  2 | human    |
|  3 | robot    |
|  4 | human    |
|  5 | human    |

2. ```
    col_human = []
    col_robot = []
    df.whoAmI.unique()
    for i in range(0, df.shape[0]):
        if df.iloc[i]['whoAmI'] == 'human':
            col_human.append(1)
            col_robot.append(0)
        else:
            col_human.append(0)
            col_robot.append(1)
    df['human'] = col_human
    df['robot'] = col_robot
    ```
|    | whoAmI   |   human |   robot |
|---:|:---------|--------:|--------:|
|  0 | robot    |       0 |       1 |
|  1 | robot    |       0 |       1 |
|  2 | human    |       1 |       0 |
|  3 | robot    |       0 |       1 |
|  4 | human    |       1 |       0 |
|  5 | human    |       1 |       0 |
