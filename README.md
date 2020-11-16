# Publish CloudFormation Templates with CDK

[![MIT License](https://badgen.now.sh/badge/License/MIT/purple?1)](https://github.com/sbstjn/cfn-release-example/blob/master/LICENSE.md)
[![MIT License](https://badgen.net/github/release/sbstjn/cfn-release-example?1)](https://github.com/sbstjn/cfn-release-example/releases)

> Run **Continuous Integration** and **Continuous Deployment** with [GitHub Actions](actions) for CloudFormation Templates and the [AWS Cloud Development Kit](https://aws.amazon.com/cdk/). Use `git tags` to manage [GitHub Releases](releases) and upload static YAML files to S3 for AWS integrations.

**tl;dr:** _Use the AWS CDK to build a static YAML file and deploy it to S3._

When orchestrating AWS services, you might end up needing a static CloudFormation Template stored in an S3 Bucket. The basic tools for CloudFormation Templates can be frustrating and building a pipeline to manage static files, is boring as hell. Thanks to the [AWS Cloud Development Kit](https://aws.amazon.com/cdk/) and GitHub Actions, you can run a pretty neat pipeline to deploy static CloudFormation Templates.

## Workflow

Use the the **CDK** to create a CloudFormation Stack.

### Integration

A [GitHub Action in `integration.yml`](.github/workflows/integration.yml) runs `cdk build` on every `push` event.

### Release

A [GitHub Action in `release.yml`](.github/workflows/release.yml) creates a **GitHub Release** for every `tag` matching `v0.1.0` pattern.

### Deployment

The static **YAML** file is uploaded to the **GitHub Release** and your **S3 Bucket**.

## Configuration

You need to set the following `secrets` for your repository:

- `AWS_BUCKET_NAME`
- `AWS_BUCKET_REGION`
- `AWS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
