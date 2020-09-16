Compare Cell B2 to LookupSheet and find a matching row, then populate this Cell with the LookupSheet's 4th column
```
=VLOOKUP(B2,LookupSheet,4,FALSE)
```

Compare cell B2 to LookupSheet's column B and find a matching row, then populate this Cell with the LookupSheet's matching row's column A cell contents.
```
=INDEX('LookupSheet'!A:A,MATCH(B2,'LookupSheet'!B:B,0))
```



Make the contents of this cell match that of another after a string substitution
```
=SUBSTITUTE(A2,"currentstring","newstring")
```

Two or more string replacements (copy/paste into A2 to continue nesting)
```
=SUBSTITUTE(SUBSTITUTE(A2,"currentstring1","newstring1"),"currentstring2","newstring2")
```
