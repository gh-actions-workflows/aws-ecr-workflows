# AWS ECR Publish Workflow

Publique a sua imagem Docker no AWS ECR.

## Como usar?

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
      image_tag: ${{ github.sha }} # Utilize o o valor que quiser para a tag
      aws_region: ${{ vars.AWS_REGION }}
    secrets:
      aws_role_to_assume: ${{ secrets.AWS_ROLE }}
```

Para mais detalhes sobre o funcionamento consulte o arquivo: [publish-ecr.yaml](https://github.com/gh-actions-workflows/aws-ecr-workflows/blob/master/.github/workflows/publish-ecr.yaml).

Para detalhes de como criar a role necessária consulte a seguinte documentação: [AWS Configure Credentials](https://github.com/aws-actions/configure-aws-credentials/blob/main/README.md).
