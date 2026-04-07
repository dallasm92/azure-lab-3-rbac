# Scope And Role Summary

## Assignment Table

| Principal / group | Role | Scope | Purpose | Assignment type |
|---|---|---|---|---|
| `Lab-Readers` | Reader | `rg-azure-lab-rbac` | Read-only visibility across resources in the lab resource group | Direct on resource group |
| `Lab-Contributors` | Contributor | `rbaclabstorage01` | Change access limited to the storage account used in the lab | Direct on storage account |
| Dallas Morison | Owner | Subscription | Existing high-level administrative access visible in IAM | Inherited, not created by the lab |

## Inheritance Notes

The final storage-account IAM screen shows how Azure inheritance works in practice:

| Principal / group | How it appears on the storage account | Why |
|---|---|---|
| `Lab-Readers` | `Reader` with `Resource group (Inherited)` | The role was assigned at the parent resource-group scope |
| `Lab-Contributors` | `Contributor` with `This resource` | The role was assigned directly on the storage account |
| Dallas Morison | `Owner` with `Subscription (Inherited)` | The role already existed at a higher scope |

## Summary

This lab shows a simple and useful access model:

- use a higher scope for low-risk visibility
- use a narrower scope for change access
- confirm the final result from the child resource to see both direct and inherited permissions together
