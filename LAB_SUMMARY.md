# Lab Summary

## Lab

Azure Lab 3: Group-Based RBAC at Resource Group and Storage Account Scope

## Goal

Use Microsoft Entra security groups and Azure RBAC to separate read-only access from change access at different scopes.

## Skills Demonstrated

- Microsoft Entra security group creation
- Azure RBAC role assignment at resource group and resource scope
- Least-privilege access design
- Group-based access instead of direct user assignment
- IAM review for inherited versus direct permissions

## Final State

- `rg-azure-lab-rbac` created as the RBAC test scope
- `rbaclabstorage01` created as the narrower Contributor target
- `Lab-Readers` assigned `Reader` at the resource-group scope
- `Lab-Contributors` assigned `Contributor` at the storage-account scope
- Final IAM view showed both direct and inherited access in the expected places

## Portfolio Value

This lab shows practical Azure authorization design instead of only resource deployment. It demonstrates group-based role assignment, scope boundaries, and inherited access, which map directly to real-world cloud administration work.
