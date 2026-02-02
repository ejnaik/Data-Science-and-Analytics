```text
df.duplicated() : Returns Boolean T/F
```
```text
      brand    style  rating
0    Wowyow  cistern     4.0
1    Wowyow  cistern     4.0
2   Splaysh      jug     5.5
3   Splaysh    stock     3.3
4   Pipplee    stock     3.0

0    False
1     True
2    False
3    False
4    False
dtype: bool
```

```text
df.duplicated(subset=['type'], keep='last')
```

```text
DF :
color  rating     type
0   olive     9.0    rinds
1   olive     9.0    rinds
2    gray     4.5  pellets
3  salmon    11.0  pellets
4  salmon     7.0  pellets

OUTPUT:

0     True
1    False
2     True
3     True
4    False
dtype: bool
```
```text
df.drop_duplicates() : drop duplicates of exact matches of entire rows of data
```
```text

DF:

brand    style  rating
0   Wowyow  cistern     4.0
1   Wowyow  cistern     4.0
2  Splaysh      jug     5.5
3  Splaysh    stock     3.3
4  Pipplee    stock     3.0

OUTPUT :

     brand    style  rating
0   Wowyow  cistern     4.0
2  Splaysh      jug     5.5
3  Splaysh    stock     3.3
4  Pipplee    stock     3.0
```
```text
df = df.drop_duplicates(subset='style')
```
```text

DF:
 brand    style  rating
0   Wowyow  cistern     4.0
1   Wowyow  cistern     4.0
2  Splaysh      jug     5.5
3  Splaysh    stock     3.3
4  Pipplee    stock     3.0

OUTPUT:

     brand    style  rating
0   Wowyow  cistern     4.0
2  Splaysh      jug     5.5
3  Splaysh    stock     3.3
```
```text
df = df.drop_duplicates(subset=['style', 'rating'])
```
```text
DF: 
 brand    style  rating
0   Wowyow  cistern     4.0
1   Wowyow  cistern     4.0
2  Splaysh      jug     5.5
3  Splaysh    stock     3.3
4  Pipplee    stock     3.0

OUTPUT:

     brand    style  rating
0   Wowyow  cistern     4.0
2  Splaysh      jug     5.5
3  Splaysh    stock     3.3
4  Pipplee    stock     3.0
```
