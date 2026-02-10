# Microsoft Intune Role Based Access Control

## Objective

Ensure administrative access to Microsoft Intune is correctly delegated using role based access control, enabling least privilege administration while maintaining centralized governance and operational separation.

## High Level End to End Workflow

Administrative access to Intune follows a layered model. Microsoft Entra ID roles determine who is eligible to administer Intune. Intune RBAC roles define what actions an administrator can perform. Scope tags restrict which Intune objects an administrator can see and manage. All layers must be correctly configured for effective access control.

## Identity Prerequisites

Role management in Intune depends on directory level permissions in Microsoft Entra ID. Administrators must hold either the Global Administrator role or the Intune Administrator role, also referred to as the Intune Service Administrator. These roles are required to create, modify, and assign Intune RBAC roles.

## Intune RBAC Roles

Intune RBAC roles exist within the Intune admin center and govern permissions specific to Intune operations. These roles define the actions an administrator can perform, including device configuration, compliance management, application management, enrollment configuration, and reporting access. Roles may be built in or custom. Custom roles allow granular permission control aligned with operational responsibilities.

## Scope Tags

Scope tags are used to restrict administrative visibility within Intune. Scope tags do not grant permissions and do not apply policies to devices. By default, all Intune objects are associated with the Default scope tag. Custom scope tags may be created to segment administration by location, department, or business unit. Administrators can only see and manage Intune objects that match the scope tags assigned to their role.

## Custom Role Creation and Assignment

Custom roles define specific Intune permissions based on administrative needs. A role assignment consists of an admin group, one or more scope tags, and optional user or device scopes. Administrators are limited to performing actions defined by the role and only on objects visible through assigned scope tags.

## Operational Model

Intune administrative control operates across three layers. Microsoft Entra ID roles establish eligibility to administer Intune. Intune RBAC roles define permitted actions. Scope tags restrict object visibility. All three layers must align to enforce secure and scalable administration.

## Summary

Microsoft Intune uses a layered RBAC model to manage administrative access. Microsoft Entra ID roles determine who can access Intune administration. Intune RBAC roles define what actions administrators can perform. Scope tags limit which Intune objects administrators can see and manage. Proper configuration ensures least privilege access and controlled operational boundaries.
