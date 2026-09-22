# Architecture Notes

This document expands on the conceptual architecture used in the Azure case study. It describes the relationship between major infrastructure components without claiming a production deployment.

## Logical flow

```text
User / Administrator
        |
        v
   Azure RBAC
        |
        v
 Resource Group
   |       |
   |       +-------------------+
   v                           v
Virtual Network            Azure Storage
   |
   +---- Subnet / NSG ---- Windows VM
   |
   +---- Subnet / NSG ---- Linux VM
                               |
                               v
                    Azure Monitor / Log Analytics
```

## Design considerations

### Resource organization
A resource group provides a management boundary for related Azure resources. Grouping related resources makes access control, monitoring, and lifecycle management easier to reason about.

### Network segmentation
Virtual Networks and subnets provide the network structure. NSGs add traffic filtering at the subnet or network-interface level.

### Compute
Windows and Linux VMs provide the operating-system layer. Troubleshooting therefore needs to consider both Azure-side configuration and guest-OS state.

### Identity and access
RBAC defines who can perform actions and at what scope. A connectivity issue and a permissions issue can look similar to an end user, so they should be tested separately.

### Observability
Azure Monitor and Log Analytics provide operational context. Metrics and logs are most useful when they are part of the design rather than added only after a problem appears.

## Scope

This architecture is a learning model based on technologies practised in coursework. It intentionally avoids invented resource names, IP addresses, production data, or customer environments.
