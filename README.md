# AWS ECR Publish Workflow

Publish your Docker image to AWS ECR.

## How to use?

```yaml
name: Publish Docker Image
on: [push]

permissions:
  id-token: write
  contents: read

jobs:
  publish:
    uses: gh-actions-workflows/aws-ecr-workflows/.github/workflows/publish-ecr.yaml@1.3
    with:
      image_name: my-image-name
      image_tag: ${{ github.sha }} # Use whatever value you want for the tag
      aws_region: ${{ vars.AWS_REGION }}
    secrets:
      aws_role_to_assume: ${{ secrets.AWS_ROLE }}
```

For more details on how it works, see the file: [publish-ecr.yaml](https://github.com/gh-actions-workflows/aws-ecr-workflows/blob/master/.github/workflows/publish-ecr.yaml).

For details on how to create the required role, see the following documentation: [AWS Configure Credentials](https://github.com/aws-actions/configure-aws-credentials/blob/main/README.md).
