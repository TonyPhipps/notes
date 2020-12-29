# Force Outlook to preview and send in Plain Text
HKEY_CURRENT_USER\Software\Microsoft\Office\version\Outlook\Options\Mail\ReadAsPlain - (DWORD) 1
    Windows Registry Editor Version 5.00
    [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\16.0\Outlook\Options\Mail]
    "ReadAsPlain"=dword:00000001

## GPO
GPO templates : https://www.howto-outlook.com/howto/policies.htm
User Configuration -> Policies -> Administrative Templates -> Microsoft Outlook XXXX -> Outlook Options -> Mail Format -> Internet Formatting -> Message Format "Set message format" is "Enabled: Plain Text"
User Configuration -> Policies -> Administrative Templates -> Microsoft Outlook XXXX -> Outlook Options -> Preferences -> E-mail Options -> "Read Email as Plaint Text " is "Enabled"
