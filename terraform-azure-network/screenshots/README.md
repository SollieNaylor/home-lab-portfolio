# Screenshots to collect — Terraform Azure Network

Capture from **Linux Mint** or the **Azure Portal** and review every screenshot before committing.

| File | Evidence | Status |
| --- | --- | --- |
| `01-terraform-installation.png` | `terraform version` | Capture pending |
| `02-terraform-plan.png` | `terraform validate` and pre-apply summary | Capture pending |
| `03-azure-deployment.png` | `Apply complete! Resources: 9 added, 0 changed, 0 destroyed.` | Capture pending |
| `04-terraform-no-drift.png` | `No changes. Your infrastructure matches the configuration.` | Capture pending |
| `05-azure-network-checks.png` | Subnet outbound settings, NSG associations and deny rule | Capture pending |
| `06-terraform-destroy.png` | Successful teardown (`9 destroyed`) and `az group exists` returning `false` | Capture pending; results verified in conversation |

**Before publishing:** Crop out full subscription IDs, email addresses, account context, tokens, portal profile menus, unrelated browser bookmarks, and any sensitive network details. Don't accidentally upload local Terraform state, authentication files, or plan files.
