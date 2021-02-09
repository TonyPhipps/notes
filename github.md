- First time setup

```
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

- Use Git Credential Manager for Windows to handle creds, especially for locally-managed git servers

```https://github.com/microsoft/Git-Credential-Manager-Core```
```git config --global credential.helper manager```

- Edit global configs (can set/blank credential manager manually)

```git config --global --edit```

- Purge any line containing "word" in all file histories in the repository.

```git filter-branch --tree-filter "find . -type f -exec sed -i -e '/$*word/d' {} \;" -f```
