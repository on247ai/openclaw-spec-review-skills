# Ghi chú publish GitHub

Repo này đã được chuẩn bị để commit/push lên GitHub.

## Trường hợp đã có `gh`
```bash
gh repo create <repo-name> --public --source=. --remote=origin --push
```

## Trường hợp không có `gh`
1. Tạo repo mới trên GitHub bằng web UI.
2. Sau đó chạy:
```bash
git remote add origin <repo-url>
git branch -M main
git push -u origin main
```
