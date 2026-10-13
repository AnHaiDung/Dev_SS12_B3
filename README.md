# Bài 3: Tách biệt luồng CI/CD đa môi trường (Staging & Production) với GitHub Environments

## Mục tiêu
- Quản lý hạ tầng triển khai đa môi trường (Staging vs Production) thông qua GitHub Environments.
- Cấu hình Environment Protection Rules yêu cầu phê duyệt thủ công trước khi deploy lên Production.

## Cấu hình GitHub Environments
1. **staging**:
   - Environment name: `staging`
   - URL: `https://staging.example.com`
2. **production**:
   - Environment name: `production`
   - URL: `https://api.prod.example.com`
   - Protection Rules: Bật **Required reviewers** (chọn tài khoản cá nhân).

## Workflow CI/CD
- File: `.github/workflows/cd-multi-env.yml`
- Job `deploy-staging`: Chạy khi push vào branch `develop` (deploy lên môi trường `staging`).
- Job `deploy-prod`: Chạy khi push vào branch `main` (deploy lên môi trường `production`, yêu cầu phê duyệt thủ công).
