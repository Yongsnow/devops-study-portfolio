GitHub Commit
   ↓
GitHub Actions (CI)
   - Run Tests (ci-test / ci-nontest)
   - Build Docker Image
   - Push to ECR
   ↓
Terraform Apply (IaC)
   - Build or Update AWS Infra
   - Create / Update EKS Cluster, IAM Roles, ALB, etc.
   ↓
AWS CodePipeline / CodeBuild (CD)
   - Pull from ECR
   - Deploy to EKS via kubectl or Helm
   - Health Check & Rollback if needed