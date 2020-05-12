# Generating character types
We have character 𝜓 = { k, S, R} where k is number of strokes in set S = {S_1,S_2,...,S_k}, thus k relations in set R = {R_1,R_2,...,R_k}.
Within a stroke, say S_i, we have sub-strokes separated by pauses taken by the writer, i.e., S_i={s_i_1,s_i_2,...s_i_ni}. 
First to generate stroke:
We have i, ni.
Now to generate new character types :
The number of strokes in character is given by P(k). Now we have k.
```
k <- P(k)
```
The number of sub-strokes is given by P(ni|k). Now we have ni.
Then we generate stroke with ni,i.
```
for i in range(k):
  ni <- P(ni|k)
  
```
