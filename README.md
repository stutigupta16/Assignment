# DMW-Assignment

Name - Stuti Gupta

Roll no - 1913141


# apriori-python
This is a simple implementation of Apriori Algorithm in Google Colab. It takes in a csv file with a list of transactions, and finds out the maximum frequent item sets. The values for `minimum_support` and `minimum_confidence` need to be specified in the notebook.

Minimum Support 30%

Minimum Confidence 60%

## Understanding the implementation

### Processing the input
1 We expect an input file to be a csv of the following format:
```csv

item1, item2, item3, ... so on
 , t, ...
t, t, t,...
t, t, ...
... so on...

```
2 We input the file using dataframes from pandas library:

```python
df = pd.read_csv("myDataFile.csv")
```
---
### How to generate candidates?

Step 1: self-joining Lk

Step 2: pruning

Example of Candidate-generation

L3={abc, abd, acd, ace, bcd}

Self-joining: L3*L3

abcd from abc and abd

acde from acd and ace

Pruning:

acde is removed because ade is not in L3

C4 = {abcd}

---
### The Apriori Algorithm (Pseudo-Code)

```

Ck: Candidate itemset of size k

Lk : frequent itemset of size k

L1 = {frequent items};

for (k = 1; Lk !=∅; k++) do begin

Ck+1 = candidates generated from Lk;

for each transaction t in database do

increment the count of all candidates in Ck+1 that are contained in t

Lk+1 = candidates in Ck+1 with min_support

end

return ∪k Lk;
