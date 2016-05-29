#Why Hashing?
Internet has grown to millions of users generating terabytes of content each day. According to internet data tracking 
services, the amount of content on the internet doubles every six months. With this kind of growth, it is impossible to
find anything on the internet, unless we develop new data structures and algorithms for sorting and accessing data.
So what is wrong with traditional data structures like arrays and linked lists? Suppose we have a very large data set
stored in an array. The amount of time required to look up an element in the array is either O(logn) or O(n) based on whether
the array is sorted or not. If the array is sorted then a technique such as binary search can be used to search the array.
Otherwise, the array must be searched linearly. Either case may not be desirable if we need to process a very large data set.
Therefore, we introduce a new technique called hashing that allows us to update and retrieve any entry in constant time
O(1). This constant time or O(1) performance means the amount of time to perform the operation does not depend on input
size n.

#The Map Data Structure
In a mathematical sense, a map is a relation between two sets. We define Map M as a set of pairs, where each pair is of the
form (key,value) for which a given key, we can find a value using some kind of a function called a hash function. In its
simplest form, we can think of an array as a Map where key is the index and value is the value at that index. For example,
given an array A, if i is the key, then we can find the value by looking up A[i]. The idea of a hash table is more generalized
and can be described as follows.

The concept of a hash table is generalized idea of an array where key does not have to be an integer. We can have a name as 
a key, or for that manner any object as a key. The trick is to find a hash function to compute an index so that an object
can be stored at a specific location in a table such that it can be easily found.

#Example
Suppose we have a set of strings {"abc", "def", "ghi"} that we'd like to store in a table. Our objective here is to find
or update them quickly from a table, actually in O(1). We are not concerned about ordering them or maintaining any order
at all. Let us think of a simple schema to do this. Suppose we assign a=1, b=2, ...etc to all alphabetical characters. 
We can then simply compute a number for each of the strings by using the sum of the characters as follows:

"abc"=1+2+3=6, "def"=4+5+6=15, "ghi"=7+8+9=24

If we assume that we have a table the size of 5 to store these strings, we can compute the location of the string by
taking the sum mod 5. So then we will store "abc" in 6mod5=1, "def" in 15mod5=0, and "ghi" in 24mod5=4 in locations
1,0, and 4 as follows.

0=def, 1=abc, ......4=ghi

Now the idea is that if we are given a string, we can immediately compute the location using a simple hash function, which
is the sum of characters mod table size. Using this hash value, we can search for a string. This seems to be a great way
to store a dictionary. Therefore the idea of hashing seems to be a great way to store key, value in a table.

#Problems with Hashing
The method discussed above seems to good to be true as we begin to think more about the hash function. First of all, the
hash function we used, that is the sum of all the letters, is a bad one. In case we have permutations of the same letters,
"abc", "bac" in the set, we will end up with the same value for the sum and hence the key. In this case, the strings
would hash into the same location, creating what we would call a "collision". This is obviously not a good thing. Secondly,
we need to find a good table size, preferably a prime number so that even if the sums are different, then collisions can
be avoided, when we take mod of the sum to find the location. So we ask two questions.

#Question 1: How do we pick a good hash function?
#Question 2: How do we deal with collisions?
The problem of storing and retrieving data in O(1) time comes down to answering the above questions. Picking a good hash 
function is key to successfully implementing a hash table. What we mean by good is that the function must be easy to compute
and avoid collisions as much as possible. If the function is hard to compute, then we lose the advantage gained for lookups
in O(1).
