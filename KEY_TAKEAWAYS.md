# Key Takeaways

## Lessons Learned

- Azure RBAC is easier to validate when assignments are tested at more than one scope.
- Group-based role assignments are cleaner than assigning roles directly to individual users.
- Resource-group scope is useful for broad visibility, while resource-level scope is better for narrower change access.
- The Azure IAM view makes inherited permissions easier to understand when the same principal appears at multiple levels.

## Common Mistakes To Avoid

- Assigning `Contributor` too broadly when only one resource needs modification rights
- Forgetting that permissions assigned at a higher scope can flow down to child resources
- Mixing direct user assignments with group-based assignments without a clear reason
- Assuming an inherited role was created locally at the current resource just because it appears in the IAM list

## Real-World Azure Administration Relevance

This lab maps well to common Azure administration work:

- separating read-only access from change access
- using Entra groups as the main access-control unit
- scoping permissions at the lowest practical level
- reviewing IAM results to confirm that the design behaves the way it was intended to behave
