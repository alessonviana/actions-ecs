# Build, push and deploy app in AWS ECS
Github Actions to reusable in projects AWS ECR and ECS. 

## Inputs
| Name | Description | Require | Default | Type |
|------|-----------|-----------|--------|------|
| aws_role_arn | Role arn | yes | null | string |
| aws_region | AWS region to deploy | no | eu-central-1 | string |
| ecs_cluster | AWS ECS cluster name | yes | "null" | string |
| service | Service name | yes | null | string |

## Using 
Create the following directory. 

`.github/workflows/ci-cd-ecs.yaml`

Use this example below in your pipeline.

```yaml
name: "Build, push and deploy app in AWS ECS"
on:
  push:
    branches:
      - main

permissions:
  id-token: write
  contents: read
  packages: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: zeroemissionsworld/zew-actions/.github/workflows/ci-cd-ecs.yaml@v0.2.0
        with:
          aws_role_arn: ${{ vars.AWS_ROLE_ARN }}
          aws_region: ${{ vars.AWS_REGION }}
          ecs_cluster: ${{ vars.ECS_CLUSTER }}
          service: ECS-SERVICE-NAME
```
