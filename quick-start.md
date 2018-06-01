## Key symbols


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


## Read Big File

```
filepath = 'Iliad.txt'  
with open(filepath) as fp:  
   for cnt, line in enumerate(fp):
       print("Line {}: {}".format(cnt, line))
```
fp is an iterable object. The enumerate() function adds a counter to an iterable. So for each element in cursor , a tuple is produced with (counter, element) ; the for loop binds that to row_number and row , respectively. It's a builtin generator function.

http://stackabuse.com/read-a-file-line-by-line-in-python/

## List

### List Comprehension
```
myList = [i for i in range(10)]
```
Is equivalent to
```
myList = []
for i in range(10):
    myList.append(i)
```
