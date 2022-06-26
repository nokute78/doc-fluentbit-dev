# mk_list

## Source/Header

https://github.com/fluent/fluent-bit/blob/master/lib/monkey/include/monkey/mk_core/mk_list.h

## APIs

### void mk_list_init(struct mk_list *list)

#### Description

The **mk_list_init** function initializes list.
Usually an argument `list` is a head of list.

```
head -> head -> head
```

### void mk_list_add(struct mk_list *_new, struct mk_list *head)

#### Description

The **mk_list_add** function adds _new to tail of list.

```
mk_list_init(&head)
mk_list_add(val1, &head)
mk_list_add(val2, &head)
```

Then

```
head -> head -> head
val1 -> head -> val1 -> head ..
val2 -> head -> val1 -> val2 -> head ...
```

### void mk_list_add_after(struct mk_list *_new,struct mk_list *prev, struct mk_list *head)

#### Description

The **mk_list_add_after** function adds _new to next of prev.
If the list size is 0 or 1, it calls **mk_list_add**.


The list is 
```
head -> val1 -> val2 -> head
```

Calls mk_list_add_after
```
mk_list_add_after(val3, val1, head);
```

Then
```
head -> val1 -> val3 -> val2 -> head
```
