# sds

## Summary

`flb_sds` is based on https://github.com/antirez/sds .

It is compatible with char array string.

## Source/Header

- https://github.com/fluent/fluent-bit/blob/master/src/flb_sds.c
- https://github.com/fluent/fluent-bit/blob/master/include/fluent-bit/flb_sds.h


## Data structure of `flb_sds`.

|Member|Description|Offset of `flb_sds_t`|
|------|-----------|---------------------|
|len   | uint64_t. Used size of `buf`. | -16|
|alloc | uint64_t. Allocated size of `buf`.|-8|
|buf   |The string. `flb_sds_t` points this member. | 0|

## APIs

### flb_sds_create(const char *str)

#### Description
The **flb_sds_create** function allocates and creates `flb_sds` from _str_.
It returns `flb_sds_t` which points the member of `flb_sds`.

_str_ should be null terminated.

It should be released by `flb_sds_destroy`


### flb_sds_create_len(const char *str, int len)

#### Description
The **flb_sds_create_len** function allocates and creates `flb_sds` from _str_.
It returns `flb_sds_t` which points the member of `flb_sds`.

It should be released by `flb_sds_destroy`


### flb_sds_destroy(flb_sds_t s)


#### Description

The **flb_sds_destroy** function releases `flb_sds`.

