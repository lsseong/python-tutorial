## import CSV
```
import pandas as pd
df = pd.read_csv('C:/temp/algo/marketdata/ARCA/GDX.csv')
```

```
import csv
with open('C:/temp/data/winequality-red.csv') as f:
    wines = list(csv.reader(f, delimiter=';'))
```
More about with statement - http://preshing.com/20110920/the-python-with-statement-by-example/
