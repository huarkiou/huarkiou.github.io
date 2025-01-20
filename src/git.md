# git

## 移除某个文件的所有commit记录

```bash
git filter-branch -f  --index-filter 'git rm -rf --cached --ignore-unmatch file-to-deleted' HEAD
git push origin --force --all
```
