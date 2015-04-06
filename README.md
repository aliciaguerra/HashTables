# HashTables
- In computing, a hash table is a data structure that can be used to implement an associateciative array, a structure that can map keys to values. A hash table uses a hash function to compute an index into an array of buckets or slots, from which the correct value may be found.
- Ideally, the hash function will assign each key to a unique bucket, but this situation is rarely achievable in practice (usually some keys will hash into the same bucket). Instead, most hash table designs assume that hash collisions - different keys that are assigned by the hash function to the same bucket - will occur and ust be accomodated in some way.
- In a well-dimensioned hash table, the average cost (number of instructions) for each lookup is independent of the number of elements stored in the table. Many hash table designs also allow arbitrary insertions or deletions of key-value pairs, at amortized constant average cost per operation.
- In many situations, hash tables turn out to be more efficient than search trees or any other table lookup structure. For this reason, they are widely used for associative arrays, database indexing, caches, and sets.
#Hashing
The main idea of hashing is to distribute the entries (key/value pairs) across an array of buckets. Given a key, the algorithm computes an index that suggests where the index can be found: <br>
`index=f(key, array_size)` <br>
Often this is done in two steps: <br>
`hash=hashfunc(key)` <br>
`index=hash%array_size` <br>
In this method, the hash is independent of the array size, and it is then reduced to an index (a number between 0 and array_size-1) using the modulo operator (%). <br>
In the case that the array size is a power of two, the remainder operation is reduced to masking, which improves speed, but can increase problems with a poor hash function. <br>
<b>Choosing a Good Hash Function</b><br>
A good hash function and implementation algorithm are essential for good hash table performance, but may be difficult to achieve. <br>
A basic requirement is that the function should provide a uniform distribution of hash values. A non-uniform distribution increases the number of collisions and the cost of resolving them. Uniformity is sometimes difficult to ensure about design, but may be evaluated empirically using statistical tests. <br>
The distribution needs to be uniform for table sizes that occur for the application. In particular, if one uses dynamic resizing with exact doubling and halving of the table s, then the hash function needs to be uniform only when s is a power of 2. On some other hand, some hashing algorithms provide uniform hashes only when s is a prime number. <br>
For open addressing schemes, the hash function should also avoid clustering, the mapping of two or more keys to consecutive slots. Such clustering may cause the lookup cost to skyrocket, even if the load factor is low and collisions are infrequent. The popular multiplicative is claimed to have particularly poor clustering behavior. <br>
Cryptographic hash functions are believed to provide good hash functions for any table size s, either by modulo reduction or by bit masking. They may also be appropriate if there is a risk of malicious users trying to sabotage a network a network service by submitting requests designed to generate a large number of collisions in the server's hash tables. However, the risk of sabotage can also be avoided by cheaper methods (such as applying a secret salt to the data, or using a universal hash function). <br><br>
<b>Perfect Hash Function</b><br>
If all keys are shown ahead of time, a perfect hash function can be used to create a perfect hash table that has no collisions. If minimal perfect hashing is used, every location in the hash table can be used as well. <br>
Perfect hashing allows for constant time lookups in the worst case. This is in contrast to most chaining and open addressing methods, where the time for lookup is low on average, but may be very large (proportional to the number of entries) for some sets of keys. 
#Key Statisics
A critical statistic for a hash table is the load factor. This is simply the number of entries divided by the number of buckets, that is, n/k where n is the number of entries and k is the number of buckets. <br>
If the load factor is kept reasonable, the hash table should perform well, provided the hashing is good. If the load factor is too large
#Collision Resolution
Hash collisions are practically unavoidable when hashing a random subset of a large set of possible keys.
<br>
<b>Seperate Chaining</b>
