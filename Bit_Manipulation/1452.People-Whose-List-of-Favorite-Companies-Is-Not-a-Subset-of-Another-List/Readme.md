### 1452.People-Whose-List-of-Favorite-Companies-Is-Not-a-Subset-of-Another-List

#### 解法1：暴力验证
我们建立每个人的公司列表转化为集合。对于每个人i，我们查看那些公司列表比i更长的那些人j，看i的公司列表是不是j的公司列表的子集。如果i是j的子集的话，那么i就不是答案，终止对i的考察。如果i不是任何j的子集，那么就把i放入答案。

#### 解法2：bitmask
以上解法有一个可以显著优化的地方。对于第i个人而言，不需要考察所有其他人j。我们令c2p[c]表示喜欢公司c的人的集合。我们只要考察i喜欢的所有公司的c2p集合的交集。最终留在交集里的人，就是和i一样喜欢相同公司的人。显然如果这个交集除了i之外还有其他人的话，就说明i的公司列表就是这些人的公司列表的子集。

数据结构上如何来存储c2p[c]呢？当然可以用一个set。只不过set之间做交集的运算写起来有点麻烦。更方便的数据结构是bitset<100>，用每个bit表示这个人是否喜欢这家公司。这样c2p[x]&c2p[y]就能表达哪些人同时喜欢x和y两家公司，交集的操作非常方便。
