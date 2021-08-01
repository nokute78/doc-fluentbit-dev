# Record Accessor

## Summary

## Source/Header

- https://github.com/fluent/fluent-bit/blob/master/src/flb_record_accessor.c
- https://github.com/fluent/fluent-bit/blob/master/src/flb_ra_key.c
- https://github.com/fluent/fluent-bit/tree/master/src/record_accessor
- https://github.com/fluent/fluent-bit/blob/master/include/fluent-bit/flb_record_accessor.h
- https://github.com/fluent/fluent-bit/blob/master/include/fluent-bit/flb_ra_key.h
- https://github.com/fluent/fluent-bit/tree/master/include/fluent-bit/record_accessor

## Data structure of `flb_record_accessor`

|Member|Description|
|------|-----------|
| size_hint   | size_t. The hint of an outgoing size buffer. |
| pattern | flb_sds_t. The pattern string. e.g. `$nest['key_name']` |
| list   | struct mk_list. The list of `flb_ra_parser`. |
| _head | struct mk_list. |

## Data structure of `flb_ra_parser`

|Member|Description|
|------|-----------|
| type   | int. Token type. `FLB_RA_PARSER_*`. `STRING`, `KEYMAP`, `ARRAY_ID`, `FUNC`, `REGEX_ID`, `TAG` and `TAG_PART`.|
| id | int. For `REGEX_ID` or `TAG_PART`.|
| key  | `struct flb_ra_key *`. |
| slist | `struct mk_list*`. |
| _head | `struct mk_list`. Link to parent flb_record_accessor->list.|



## APIs

### flb_ra_create(char *str, int translate_env)

#### Description

The **flb_ra_create** function allocates and creates `flb_record_accessor` from _str_.
The return value should be released by `flb_ra_destroy` after using.

_translate_env_ can be set `FLB_TRUE` or `FLB_FALSE`.
if `FLB_TRUE`, some environment variables has been created as part of the string.

