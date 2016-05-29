#The very simple hash table example
In the current article we show the very simple hash table example. It uses simple hash function, collisions are resolved
using linear probing (open addressing strategy) and hash table has constant size. 

#Hash table
Underlying array has constant size to store 128 elements and each slot contains a key-value pair. Key is stored to
determine between key-value pair, which have the same hash. 

#Hash Function
Table allows only integers as values. Hash function to be used is the remainder of division by 128. In the view of
implementation, the hash function can be encoded using remainder operator or using bitwise AND with 127.

Note: Power of two sized tables are often used in practice (for instance in Java). When used, there is a special hash function,
which is applied in addition to the main one. The measure prevents collisions occuring for hash codes that do not differ
in lower codes.

#Collision Resolution Strategy
Linear probing is applied to resolve collisions. In case the slot, indicated by hash function, has already been occupied,
algorithm tries to find an empty one by probing consequent slots in the array.

Note: Linear probing is not the best technique to be used when table is of a constant size. When load factor exceeds
particular value, hash table performance will increase non-linearly. Also, the number of stored key-value pairs is limited
to the size of the table (128).

#Code Snippets
This implementation suffers one bug. When there is no more place in the table, the loop, searching for empty slot, will
run indefinitely. It won't happen in real hash table based on open addressing, because it is most likely dynamic-sized.
Also, the removal's implementation is ommitted to maintained simplicity. 

                            public class HashEntry {
                              private int key;
                              private int value;
                              
                              HashEntry(int key, int value) {
                              this.key=key;
                              this.value = value;
                              }
                              
                              public int getKey() {
                              return key;
                              }
                              
                              public int getValue() {
                              }
                              }
                              
HashMap Class

                           public class HashMap {
                            private final static int TABLE_SIZE = 128;
                            HashEntry[] table;
                            
                            HashMap() {
                             table = new HashEntry(TABLE_SIZE);
                             for(int i=0; i<TABLE_SIZE; i++) 
                              table[i]=null;
                              }
                              
                            private int get(int key) {
                             int hash = (key % TABLE_SIZE);
                             while(table[hash] != null && table[hash].getKey() != key)
                              hash = (hash+1) % TABLE_SIZE;
                             if(table[hash] == null)
                              return -1;
                             else
                              return table[hash].getValue();
                            }
                            
                            public void put(int key, int value) {
                             int hash = (key % TABLE_SIZE);
                             while(table[hash) != null && table[hash].getKey() != key)
                              hash = (hash+1) % TABLE_SIZE;
                              table[hash] = new HashEntry(key,value);
                              }
                            }
                              
                              
