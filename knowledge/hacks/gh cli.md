gh is the new cli for github 

## Example
#### filter repos based on some code changes in specific filename 
```
gh search code 16 --owner=katana-scm --filename=.nvmrc --json=repository --jq='.[] | .repository.nameWithOwner'
```
