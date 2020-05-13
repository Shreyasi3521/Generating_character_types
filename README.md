# Generating character types
We have character 𝜓 = { k, S, R} where k is number of strokes in set S = {S_1,S_2,...,S_k}, thus k relations in set R = {R_1,R_2,...,R_k}.\
Within a stroke, say S_i, we have sub-strokes separated by pauses taken by the writer, i.e., S_i={s_i_1,s_i_2,...s_i_ni}. \
Each s_i_j is {x_i_j, y_i_j, z_i_j}. Here x_i_j is sub-stroke control point, y_i_j is sub_stroke scale, z_i_j is the identity of sub-stroke.\
Relations are of 4 types:
 - Along: R_i={𝜀_i = Along, u_i, v_i, t_i}\
 u_i is the stroke number selected at random from {1,2,...,i-1}\
 v_i is the sub-stroke number selected at random from {1,2,...,u_i}\
 t_i is the coordinate in the sub-stroke selected randomly\
 - Independent: R_i={𝜀_i = Independent, J_i, L_i}\
 J_i <- P(J_i) where P(J_i) is a multinomial over 2D to select x coordinate of begining of new stroke\
 L_i <- P(L_i|J_i) to select y coordinate of begining of new stroke\
 - End: R_i={𝜀_i = End, u_i}\
 u_i is the stroke number selected at random from {1,2,...,i-1}\
 - Start: R_i={𝜀_i = Start, u_i}\
 u_i is the stroke number selected at random from {1,2,...,i-1}\
First to generate stroke:\
We have i, ni.\
```
def generate_stroke(i, n_i):
  z_i_1 <- P(z_i_1)
  for j in {2,...,n_i}:
    z_i_j <- P(z_i_j|z_i_(j-i))
  for j in {1,...,n_i}:
    x_i_j <- P(x_i_j|z_i_j)
    y_i_j <- P(y_i_j|z_i_j)
    s_i_j = {x_i_j, y_i_j, z_i_j}
  S_i = {s_i_1,...,s_i_ni}
  return S_i
```
Now to generate new character types :\
The number of strokes in character is given by P(k). Now we have k.
```
k <- P(k)
for i in range(k):
  ni <- P(ni|k)
  
```
