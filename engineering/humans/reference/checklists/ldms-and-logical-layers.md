# LDM and Logical Layers Checklist

Use this checklist to review the separate [Logical Deployment Modules](../catalogues/ldms.md) and [Logical Layers](../catalogues/logical-layers.md) concepts together with the implementation detail in [Logical Deployment Modules](../../development/ldms.md).

- [ ] The LDM is described as a logical package whose components are delivered together.
- [ ] The design does not assume that every LDM can be deployed independently.
- [ ] Whole-system or multi-LDM deployment is represented where that is the actual delivery shape.
- [ ] The responsibilities, contracts, dependencies and change that belong together are coherent.
- [ ] Conceptual interfaces are distinguished from logical state management.
- [ ] Logical state management is distinguished from physical storage.
- [ ] Mappings and contracts between the layers are explicit.
- [ ] Components have a clear place within the LDM and logical layers.
- [ ] A database, framework or project boundary has not been mistaken for the logical model.
- [ ] Separation has been introduced where it protects change, not merely because another package is possible.
