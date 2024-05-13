
# Indicators trading and drawbacks

This project tries to decode some basic purely Indicators basses strategies, and ty to highlight how they are not worthy of the hype they get


## Strategy Idea

- In the first project i have applied bolinger bands on RSI indicator and the have sold nifty when RSI went above half standard devitaion of upper band and vice-versa

- I have applied this on a short term basis where by price seems to follow somewhat of a random walk, but the second file  is attached to show how this strategy performs pathetically in the long run when applied to a 7 year time frame.


## Deployment1

This is the import snipt it from the first code where i mention a period of n = 10 and form the bolinger bands with stdev = 0.5

```bash
df['mean'] = df['RSI'].rolling(window = 10).mean()

df['upper_band'] = df['mean'] + (0.5*df['stdev'])
df['lower_band'] = df['mean'] - (0.5*df['stdev'])
```


## Deployment2

In the second code this loop has been performed to convert all positions>1 --> to 1, like when we get multiple signals at once, the positions column gets appended by 2 or 3 depending on the no. of signals but we want it to be 1 or 0 throughout as 1 represents the whole portfolio

```bash
  for i in range(len(df['Close'])):
    if df['Cum_positions'].iloc[i] == 2:
        df['Cum_positions'].iloc[i] = 1
    else:
        pass
```
    