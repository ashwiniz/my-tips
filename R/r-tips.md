# R tips

Q: Wanted column names with "GMC" string (pattern in the colnames of the data)
Step1:
grep function gives indices with the given pattern inside a character vector x
grepl function gives a logical vector with the given pattern inside a character vector x
Step 2:
list returns the colnames wherever it is true or with the given index

The below code returns the colnames which contains "GMC" pattern
```
wanted_cols <- colnames(alldata) 
wanted_cols <- wanted_cols[grepl("GMC", wanted_cols)]
```
