# Publish CloudFormation Templates with CDK

[![MIT License](https://badgen.now.sh/badge/License/MIT/purple?1)](https://github.com/sbstjn/cfn-release-example/blob/master/LICENSE.md)
[![MIT License](https://badgen.net/github/release/sbstjn/cfn-release-example?1)](https://github.com/sbstjn/cfn-release-example/releases)

> Run **Continuous Integration** and **Continuous Deployment** with [GitHub Actions](actions) for CloudFormation Templates and the [AWS Cloud Development Kit](https://aws.amazon.com/cdk/). Use `tags` to create [GitHub Releases](releases) and upload the static YML files to S3 for AWS integrations.

When orchestrating AWS service, you sometimes end up need a static CloudFormation Template stored in an S3 Buckets. The basic tools for CloudFormations can be hard to tackle and building a pipeline to manage static files, is boring as hell. Thanks to the [AWS Cloud Development Kit](https://aws.amazon.com/cdk/) and GitHub Actions, you can build a pretty neat pipeline to deploy static CloudFormation Templates.

_If you store your CloudFormation Templates in an S3 Bucket, you can easily re-use them. For example, in **AWS Service Catalog**, **AWS CloudFormation StackSets**, or to create [*Launch Stack* Buttons](https://aws.amazon.com/blogs/devops/construct-your-own-launch-stack-url/)._

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
