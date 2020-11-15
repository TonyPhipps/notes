Use windows Credential Store to handle credentials

```git config --global credential.helper wincred```

Use Git Credential Manager for Windows to handle creds, especially for locally-managed git servers

```https://github.com/microsoft/Git-Credential-Manager-Core```

Edit global configs (can set/blank credential manager manually)

```git config --global --edit```

Purge any line containing "word" in all file histories in the repository.

```git filter-branch --tree-filter "find . -type f -exec sed -i -e '/$*word/d' {} \;" -f```
