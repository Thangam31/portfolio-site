# \# Portfolio Site — Stage 0

# 

# Live: https://dv3se6bkqkrpv.cloudfront.net

# 

# \## Architecture

# 

# Browser → CloudFront (CDN + HTTPS) → S3 (private, OAC)

# 

# Deployed automatically via GitHub Actions on every push to main.

# 

# \## Stack

# 

# \- S3 (private bucket)

# \- CloudFront (CDN + HTTPS via OAC)

# \- GitHub Actions (CI/CD: S3 sync + CloudFront invalidation)

# \- IAM user with least-privilege policy

# 

# \## Troubleshooting

# 

# \### Issue 1: GitHub Actions failed with "AccessDenied"

# Cause: Removed IAM policy from deployer user.

# Fix: Re-attached portfolio-deployer-policy.

# Lesson: IAM permissions are the #1 cause of pipeline failures.

# 

# \### Issue 2: Pipeline succeeded but old content still showing

# Cause: Removed CloudFront invalidation permission. S3 updated but CDN cache served old files.

# Fix: Restored cloudfront:CreateInvalidation in the IAM policy.

# Lesson: CDN invalidation is mandatory after every deploy.

# 

# \## What I learned

# 

# \- S3 static hosting with private bucket

# \- CloudFront OAC for secure S3 access

# \- GitHub Actions CI/CD with AWS Secrets

# \- CloudFront cache invalidation

# \- IAM least-privilege in practice



