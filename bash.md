# crontab

## List crontab jobs for current user
```crontab -l```

## List crontab jobs for another user
```crontab -l -u anotheruser```

## List crontab jobs for all users
```for user in $(cut -f1 -d: /etc/passwd); do crontab -u $user -l; done```
