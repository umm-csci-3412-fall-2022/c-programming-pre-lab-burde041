# Leak report

There is a memory leak in `check_whitespace.c`. 
The `strip()` function returns a `calloc` string but the caller function
`is_clean()` does not free it after using it. The fix is to change `is_clean()`
so that it free the string. Since `strip()` can return either a `calloc` or literal
string, it also needs to be changed to only return a `calloc` string.
