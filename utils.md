# Utils

## Source/Header

- https://github.com/fluent/fluent-bit/blob/master/src/flb_utils.c
- https://github.com/fluent/fluent-bit/blob/master/include/fluent-bit/flb_utils.h

## APIs

### flb_utils_split(const char *line, int separator, int max_split)

#### Description

The **flb_utils_split** function allocates mk_list and returns.
The return value should be released by `flb_utils_split_free`

```c
    const char *test = "aaa bbb ccc";
    struct mk_list *list;

    list = flb_utils_split(test, " ", 3);
    // mk_list_size(list) should be 3

    // mk_list_entry_first and mk_list_entry_next ...
```
