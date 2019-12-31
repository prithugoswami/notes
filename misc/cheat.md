# Multiplexing

- Set of techniques that allow the simultaneous transmission of multiple 
signals across a single data link.
- several low-bandwidth signals are multiplexed and sent across using a
high-bandwidth *link* refer to [code]


![mux](img/6.1.png){ width=80% }


a formula, ${e}^{i\pi }+1=0$,     nside a paragraph.
a formula, $$\forall x \in X$$,     nside a paragraph.

| The limerick packs laughs anatomical
| In space that is quite economical.
|    But the good ones I've seen
|    So seldom are clean
| And the clean ones so seldom are comical



Term 1

:   Definition 1

Term 2 with *inline markup*

:   Definition 2

        { some code, part of Definition 2 }

    Third paragraph of definition 2.


: Sample grid table.

+---------------+---------------+--------------------+
| Fruit         | Price         | Advantages         |
+===============+===============+====================+
| Bananas       | $1.34         | - built-in wrapper |
|               |               | - bright color     |
+---------------+---------------+--------------------+
| Oranges       | $2.10         | - cures scurvy     |
|               |               | - tasty            |
+---------------+---------------+--------------------+


``` {#code .c .numberLines}
minclude <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "hashtable.h"

/* --------------------- */
/* Linked List Functions */
/* --------------------- */

void *
HashTableGet(char *key, HashTable *hashtable){
    unsigned long hash = hash_function(key, hashtable->capacity);
    List *list = hashtable->lists[hash];
    if (ListIsEmpty(list))
        return NULL;

    else{// if only one element in the list
        elem_t *elem = ListGetItem(0, list);
        return elem->value;
    }
}
```
