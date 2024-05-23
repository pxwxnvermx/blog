+++
title = 'Notes about C'
date = 2024-05-23T11:15:04+05:30
draft = false
+++

## Arrays

```c
// array with 10 int space
int *a = malloc(sizeof(int) * 10);

arr[i] == i[arr] == *(arr + i) == *(i + arr)
```


## Cache Locality
Arrays offer better cache locality as they have contiguos memory allocation for members.
Basing other data structures on contiguous memory allocation makes them better 
suitable for performance intensive applications. 

Dynamically allocated data structures like Linked lists have bad cache locality as 
nodes have addresses which are seperated in memory.

```
Array                         Linked List
Address      Contents       | Address      Contents
ffff 0000    data[0]        | ffff 1000    l_data
ffff 0040    data[1]        |   ....
ffff 0080    data[2]        | ffff 3460    l_data->next
ffff 00c0    data[3]        |   ....
ffff 0100    data[4]        | ffff 8dc0    l_data->next->next
                            | ffff 8e00    l_data->next->next->next
                            |   ....
                            | ffff 8f00    l_data->next->next->next->next
```

The below link has a good explanation above the permutation table for noise generation 
about the importance of cache locality and choosing the correct data type so that the 
permutations for noise can be fit into the cache whole. It uses char which is 1byte compared 
to int which could be either 2 or 4 bytes. The char used is unsigned giving values from 0 to 255.
Which is ideal for the permutation table as the noise wraps around after 255.

[Perlin Noise Implementation](https://github.com/jdah/minecraft-weekend/blob/master/lib/noise/noise1234.c)

#### Links
- https://stackoverflow.com/questions/12065774/why-does-cache-locality-matter-for-array-performance
- https://stackoverflow.com/questions/12598741/accessing-array-declared-by-malloc
- https://stackoverflow.com/questions/492384/how-to-find-the-size-of-an-array-from-a-pointer-pointing-to-the-first-element-a
- https://stackoverflow.com/questions/25068903/what-are-pascal-strings
- https://joellaity.com/2020/01/31/string.html
