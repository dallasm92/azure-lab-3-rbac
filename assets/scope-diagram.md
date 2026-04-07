# Scope Diagram

```mermaid
flowchart TD
    A[Azure subscription 1]
    B[rg-azure-lab-rbac]
    C[rbaclabstorage01]
    D[Lab-Readers]
    E[Lab-Contributors]

    A --> B
    B --> C

    D -- Reader --> B
    E -- Contributor --> C
    D -. inherited Reader .-> C
```

The diagram reflects the final state shown in the screenshots:

- `Lab-Readers` is assigned `Reader` at the resource-group scope
- `Lab-Contributors` is assigned `Contributor` directly on the storage account
- the storage account inherits the `Reader` permission from the parent resource group
