<!-- start title -->

# GitHub Action:Upload an npm project to aws code artifact

<!-- end title -->
<!-- start description -->

Uploads an npm project to aws code artifact

<!-- end description -->
<!-- start contents -->
<!-- end contents -->
<!-- start usage -->

```yaml
- uses: catalystsquad/action-upload-npm-aws-codeartifact@undefined
  with:
    # aws access key id
    aws-access-key-id: ""

    # aws secret access key
    aws-secret-access-key: ""

    # AWS Region, e.g. us-west-2
    # Default: us-west-2
    aws-region: ""

    # Whether to set the AWS account ID for these credentials as a secret value, so
    # that it is masked in logs. Valid values are 'true' and 'false'. Defaults to true
    mask-aws-account-id: ""

    # Use the provided credentials to assume an IAM role and configure the Actions
    # environment with the assumed role credentials rather than with the provided
    # credentials
    role-to-assume: ""

    # Role duration in seconds (default: 10 minutes)
    # Default: 600
    role-duration-seconds: ""

    # Role session name (default: GitHubActions)
    role-session-name: ""

    # The external ID of the role to assume
    role-external-id: ""

    # Skip session tagging during role assumption
    # Default: true
    role-skip-session-tagging: ""
```

<!-- end usage -->
<!-- start inputs -->

| **Input**                       | **Description**                                                                                                                                                      | **Default** | **Required** |
| :------------------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------: | :----------: |
| **`aws-access-key-id`**         | aws access key id                                                                                                                                                    |             |   **true**   |
| **`aws-secret-access-key`**     | aws secret access key                                                                                                                                                |             |   **true**   |
| **`aws-region`**                | AWS Region, e.g. us-west-2                                                                                                                                           | `us-west-2` |  **false**   |
| **`mask-aws-account-id`**       | Whether to set the AWS account ID for these credentials as a secret value, so that it is masked in logs. Valid values are 'true' and 'false'. Defaults to true       |             |  **false**   |
| **`role-to-assume`**            | Use the provided credentials to assume an IAM role and configure the Actions environment with the assumed role credentials rather than with the provided credentials |             |  **false**   |
| **`role-duration-seconds`**     | Role duration in seconds (default: 10 minutes)                                                                                                                       |    `600`    |  **false**   |
| **`role-session-name`**         | Role session name (default: GitHubActions)                                                                                                                           |             |  **false**   |
| **`role-external-id`**          | The external ID of the role to assume                                                                                                                                |             |  **false**   |
| **`role-skip-session-tagging`** | Skip session tagging during role assumption                                                                                                                          |   `true`    |  **false**   |

<!-- end inputs -->
<!-- start outputs -->

| **Output**      | **Description** | **Default** | **Required** |
| :-------------- | :-------------- | ----------- | ------------ |
| `random-number` | Random number   |             |              |

<!-- end outputs -->
<!-- start examples -->

### Example usage

```yaml
name: Publish to npm code artifact repository
on:
  release:
    types: [created]
jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: catalystsquad/action-upload-npm-aws-codeartifact@v1
        with:
          aws-access-key-id: ${{ secrets.AUTOMATION_AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AUTOMATION_AWS_SECRET_ACCESS_KEY }}
          role-to-assume: arn:aws:iam::000000000000:role/YourRoleHere
```

<!-- end examples -->
<!-- start [.github/ghdocs/examples/] -->
<!-- end [.github/ghdocs/examples/] -->
