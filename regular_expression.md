Replace an Outlook-created contacts list with a CSV of emails
- Find: ```.+?<(.+?)>;*```
- Replace: ```\1\r\n```


Replace an Outlook-created contacts list with a CSV of names
- Find: ```\s*(.+?)\s<.+?>;*```
- Replace: ```\1\r\n```
