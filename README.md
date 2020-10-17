# Secret Manager

This module provides an opinionated wrapper around creating and managing secret values
in GCP [Secret Manager](https://cloud.google.com/secret-manager).

```hcl
module "secret" {
  source = "git::https://github.com/memes/terraform-google-secret-manager?ref=1.0.0"
  project_id = "my-project-id"
  id = "my-secret"
  secret = "T0pS3cret!"
  accessors = ["group:team@example.com"]
}
```

<!-- spell-checker:ignore markdownlint -->
<!-- markdownlint-disable MD033 MD034-->
<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

| Name | Version |
|------|---------|
| terraform | ~> 0.13 |
| google | ~> 3.40 |

## Providers

| Name | Version |
|------|---------|
| google | ~> 3.40 |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| accessors | An optional list of IAM account identifiers that will be granted accessor (read-only)<br>permission to the secret. | `list(string)` | `[]` | no |
| id | The secret identifier to create; this value must be unique within the project. | `string` | n/a | yes |
| labels | An optional map of label key:value pairs to assign to the secret resources.<br>Default is an empty map. | `map(string)` | `{}` | no |
| project\_id | The GCP project identifier where the secret will be created. | `string` | n/a | yes |
| replication\_locations | An optional list of replication locations for the secret. If the value is an<br>empty list (default) then an automatic replication policy will be applied. Use<br>this if you must have replication constrained to specific locations.<br><br>E.g. to use automatic replication policy (default)<br>replication\_locations = []<br><br>E.g. to force secrets to be replicated only in us-east1 and us-west1 regions:<br>replication\_locations = [ "us-east1", "us-west1" ] | `list(string)` | `[]` | no |
| secret | The secret payload to store in Secret Manager. Binary values should be base64<br>encoded before use. | `string` | n/a | yes |

## Outputs

| Name | Description |
|------|-------------|
| id | The id of the Secret Manager key that contains the secret. |
| name | The fully-qualified name of the Secret Manager key that contains the secret. |

<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
<!-- markdownlint-enable MD033 MD034 -->