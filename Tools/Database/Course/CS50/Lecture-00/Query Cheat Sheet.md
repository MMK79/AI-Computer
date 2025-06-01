```
SELECT "column0",... FROM "table";
```
* to select all columns you can use `*`
#### Sql writing style:
*  Capital for sql keywords, lower case for other things
* we will use `"` (double quote) for columns and tables
* `'` (single quote) for strings
### WHERE
`=`, `!=` , $\\<\\>$ (not equal in a different way), `NOT` (negate condition), `AND`, `OR`, `()` (prioritize inside query to run first)
* `=` for string is case sensitive
range in queries $\rightarrow$ `>`, `<`, `>=`, `<=` $\xrightarrow{can\ create\ it\ this\ way\ too}$ `BETWEEN __ AND __` 
`NULL` $\rightarrow$ means this value does not exist / missing data $\xrightarrow{for\ conditioning}$ `IS NULL`, `IS NOT NULL`
`LIKE` $\rightarrow$ roughly match some string into database $\rightarrow$ `%` (anything can be instead of it, any length even) , `_` (place for only one character)
* `LIKE` is not case sensitive unlike `=`
`ORDER BY` $\rightarrow$ sort things, `ASC` (default function), `DESC` (from highest to lowest)
* `ASC` for string sort from A-Z
`LIMIT` $\rightarrow$ get a peek view on data OR limit the results
`AS` $\rightarrow$ to make thing pretty/readable
### Sql Aggregate functions
Bring values together
`COUNT`, `AVG`, `MIN`, `MAX`, `SUM`, `ROUND(value you want to round, number of decimal)`
* `MIN` find the first, `MAX` find the last alphabetic order when you use them for string
* `COUNT` don't give unique number $\rightarrow$ `DISTINCT COUNT` to find the unique rows
### Sqlite command:
* `.schema` to see what is a structure of your database
* `.tables` to see the tables of your database
* `.quit` to quit sqlite