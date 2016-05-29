#Hashtable Implementation in Java
I came across many forums and blogs where I saw questions to implement hashtable but there is no satisfactory answer
for that question. I tried here to give the answer, how to implement hashtable in Java using array.

First, let's go in hashtable fundamental.The hashtable stores key-value pairs at a specific index on an array. The function
hash in program calculates the hash code once the hash code is calculated modulo is taken by the size of the array to
map the key at a particular index of the array. Remmeber to minimize collision take size at prime number.

There are possibility of collisions on elements at a aparticular index if the hash value calculated same for the two different
key and since the old value will be overwritten in by the new value. To avoid this sitation, there are multiple ways to
implement the logic but here we are avoiding this logic. We will focus how hashtable structure internal structure and how
does it work. I have implemented two main methods "get" and "put". 

                         package com.interview;
                         public class MyHashTable<K,V> {
                          /*take the capacity as prime number to reduce the collisions*/
                          private static int SIZE = 31;
                          /*initialize array to store value*/
                          private V[] tableValues = (V[]) new Object[SIZE];
                          
                        public synchronized V put(K key, V vlaue) {
                         if(value==null) {
                          throw new NullPointerException();
                          }
                         int index = hash(key.hashCode())%size;
                         tablesValues[index] = value;
                         return value;
                         }
                         
                        public synchronized V get(K key) {
                        int index = hash(key.hashCode()) % SIZE;
                        return tableValues[index];
                        }
                        
                        /*Method calculates the hashCode*/
                        private synchronized int hash(int h) {
                         h ^= (h>>>20) ^ (h>>>12);
                         return h ^ (h>>>7) ^ (h>>>4);
                         }
                         
                        public static void main(String args[]) {
                         MyHashTable<String, String> table = new MyHashTable<String, String>();
                         /*Store 10 values in hashtable*/
                         for(int i=0; i<10; i++) {
                          table.put("key" + i, "value" + i);
                          }
                          
                          /*retrieve values*/
                          for(int i=0; i<10; i++){
                          System.out.println();
                                    }
                                }
                            }
                        
                          }
                      
