# Implementation Notes

## Observed Resource Names

The screenshots show these names directly:

| Item | Observed value |
|---|---|
| Subscription | `Azure subscription 1` |
| Resource group | `rg-azure-lab-rbac` |
| Storage account | `rbaclabstorage01` |
| Entra group 1 | `Lab-Readers` |
| Entra group 2 | `Lab-Contributors` |

## Resource Configuration Notes

From the storage-account screenshots:

| Setting | Observed value |
|---|---|
| Region | `East US` |
| Performance | `Standard` |
| Replication | `RA-GRS` |
| Preferred storage type | `Azure Blob Storage or Azure Data Lake Storage Gen 2` |

## Scope Used for Each Assignment

### `Lab-Readers`

- Role: `Reader`
- Scope: `rg-azure-lab-rbac`
- Result at resource-group IAM: direct assignment on `This resource`
- Result at storage-account IAM: shown as inherited from the resource group

### `Lab-Contributors`

- Role: `Contributor`
- Scope: `rbaclabstorage01`
- Result at storage-account IAM: direct assignment on `This resource`

## Security Reasoning Behind Group-Based Access

Using groups instead of assigning roles directly to individual users has several practical advantages:

- access can be changed by updating group membership instead of rewriting role assignments
- the intent is easier to understand when the group names reflect the permission level
- auditing is simpler because the access model is more structured

This lab used that pattern in a basic form:

- one group for read-only visibility
- one group for change access

## Least-Privilege Explanation

The screenshots support a least-privilege design choice:

- broad read-only visibility was granted at the resource-group scope
- higher-impact change access was kept at the single-resource scope

That is a safer pattern than assigning `Contributor` across the whole resource group when the real requirement is only to manage one storage account.

## Role Difference in Practical Terms

### Reader

- Can view the resource and its configuration
- Cannot make changes

### Contributor

- Can create and modify resources in the assigned scope
- Cannot grant access to other principals unless an additional role allows that

## Notes About the Final IAM Screens

The final storage-account IAM screen shows three categories of access:

- subscription-inherited `Owner` for the operator account
- direct `Contributor` for `Lab-Contributors`
- resource-group-inherited `Reader` for `Lab-Readers`

Only the group-based RBAC assignments are treated as part of the lab implementation. The inherited `Owner` role was visible in the portal but was not created as a lab step.
