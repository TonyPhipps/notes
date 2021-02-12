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

Hide "#N/A" when formulas error-out
```
=IFERROR(your formula here,"") 
```

Convert Time Format and Timezone Offet

Fri, Jan 11 2021 12:24AM MST

```="05:00" + (DATEVALUE(MID(C2, 10, 2) & "-" & MID(C2, 6, 3) & "-" & MID(C2, 13, 4)) + (MID(C2, 18, 5) & " " & MID(C2, 23, 2)))```

Where "05:00" is the time offset, currently adding 5h to make it GMT
