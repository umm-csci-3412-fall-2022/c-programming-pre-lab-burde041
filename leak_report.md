# Leak report

There is a memory leak in `check_whitespace.c`. 
The `strip()` function returns a `calloc` string but the caller function
`is_clean()` does not free it after using it. The fix is to change `is_clean()`
so that it frees the string in the case it is not empty.
