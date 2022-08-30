---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "gitea_git_hook Resource - terraform-provider-gitea"
subcategory: ""
description: |-
  gitea_git_hook manages git hooks on a repository.
  import is currently not supported
  WARNING: using this resource requires to enable server side hookswhich are known to cause security issues https://github.com/go-gitea/gitea/pull/13058!
  if you want to procede, you need to enable server side hooks as stated here https://docs.gitea.io/en-us/config-cheat-sheet/#security-security
---

# gitea_git_hook (Resource)

`gitea_git_hook` manages git hooks on a repository.
import is currently not supported

WARNING: using this resource requires to enable server side hookswhich are known to cause [security issues](https://github.com/go-gitea/gitea/pull/13058)!

if you want to procede, you need to enable server side hooks as stated [here](https://docs.gitea.io/en-us/config-cheat-sheet/#security-security)

## Example Usage

```terraform
resource "gitea_org" "test_org" {
  name = "test-org"
}

resource "gitea_repository" "org_repo" {
  username = gitea_org.test_org.name
  name     = "org-test-repo"
}

resource "gitea_git_hook" "org_repo_post_receive" {
  name    = "post-receive"
  user    = gitea_org.test_org.name
  repo    = gitea_repository.org_repo.name
  content = file("${path.module}/post-receive.sh")
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `content` (String) Content of the git hook
- `name` (String) Name of the git hook to configure
- `repo` (String) The repository that this hook belongs too.
- `user` (String) The user (or organisation) owning the repo this hook belongs too

### Read-Only

- `id` (String) The ID of this resource.

