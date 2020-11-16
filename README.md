# Publish CloudFormation Templates with CDK

[![MIT License](https://badgen.now.sh/badge/License/MIT/purple?1)](https://github.com/sbstjn/cfn-release-example/blob/master/LICENSE.md)
[![MIT License](https://badgen.net/github/release/sbstjn/cfn-release-example?1)](https://github.com/sbstjn/cfn-release-example/releases)

> Example project for running **Continuous Integration** and **Continuous Deployment** for CloudFormation Templates using the AWS CDK and GitHub Workflows.

**tl;dr:** _Run CI/CD with GitHub Actions for CloudFormation Templates and the CDK. Use git tags to deploy static CloudFormation templates to GitHub Releases and an S3 Bucket._

The [AWS Cloud Development Kit](https://aws.amazon.com/cdk/) is great to create, maintain, and deploy your AWS infrastructure with code. You can use it to _just_ create raw CloudFormation templates, as well. Together with GitHub Actions, you can run a pretty neat pipeline for your CloudFormation Templates.

If you store your CloudFormation Templates in an S3 Bucket, you can easily re-use them. For example, in **AWS Service Catalog**, **AWS CloudFormation StackSets**, or to create [_Launch Stack_ Buttons](https://aws.amazon.com/blogs/devops/construct-your-own-launch-stack-url/).

Of course, you only want to manage your CDK sources. The integration and deployment of the static CloudFormation Template should be triggered afterwards without manual steps. This project shows how …

## Workflow

### Integration

A [GitHub Action in `integration.yml`](.github/workflows/integration.yml) runs `cdk build` on every `push` event.

### Release

A [GitHub Action in `release.yml`](.github/workflows/release.yml) creates a **GitHub Release** for every `tag` matching `v0.1.0` pattern.

### Deployment

The static **CloudFormation Template** is uploaded to the **GitHub Release** and your **S3 Bucket**.

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
