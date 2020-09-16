Compare Cell B2 to LookupSheet and find a matching row, then populate this Cell with the LookupSheet's 4th column
```
=VLOOKUP(B2,LookupSheet,4,FALSE)
```

Make the contents of this cell match that of another after a string substitution
```
=SUBSTITUTE(A2,"currentstring","newstring")
```

Two or more string replacements (copy/paste into A2 to continue nesting)
```
=SUBSTITUTE(SUBSTITUTE(A2,"currentstring1","newstring1"),"currentstring2","newstring2")
```
