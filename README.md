# Deploy CloudFormation Templates with CDK

> Example for running Continuous Integration and Continuous Deployment for CloudFormation Templates using the AWS CDK and GitHub Workflows.

## Configuration

You need to set the following `secrets` for your repository:

- `AWS_BUCKET_NAME`
- `AWS_BUCKET_REGION`
- `AWS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`

## Local Development

```bash
# Create new version using NPM and create git tag
$ > npm version minor
v0.1.1

# Push tag to GitHub
$ > git push origin --tags
```
