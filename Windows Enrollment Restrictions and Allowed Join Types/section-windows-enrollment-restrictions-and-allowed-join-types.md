# Windows Enrollment Restrictions and Allowed Join Types

## Objective

Define strict enrollment restrictions and join type controls for Windows devices to prevent unmanaged device sprawl, enforce organizational ownership boundaries, and ensure only supported enrollment paths are permitted.

These controls are evaluated before any Windows Autopilot or Microsoft Intune workflow begins and act as the first policy gate for device enrollment.

## Enrollment Restriction Scope

Windows enrollment restrictions are configured in Microsoft Intune and apply to all Windows enrollment methods, including Windows Autopilot, user driven enrollment, and manual MDM enrollment.

## Allowed Device Ownership

Corporate owned devices are permitted to enroll into Microsoft Intune.

Personal Windows device enrollment is restricted unless explicitly required for business scenarios. BYOD enrollment, when allowed, is governed by separate compliance and configuration policies and does not use Windows Autopilot.

## MDM Authority

Microsoft Intune is designated as the sole mobile device management authority for Windows devices.

No third party MDM solutions are permitted to manage Windows devices in parallel. Devices already managed by another MDM must be unenrolled before enrollment into Intune is allowed.

## Allowed Join Types

The following join types are permitted:

- Microsoft Entra ID join for corporate owned Windows devices  
- Hybrid Microsoft Entra ID join only where legacy on premises dependencies require it  

Workgroup join and local only device enrollment is not supported for managed corporate devices.

## User Enrollment Permissions

Enrollment permissions are restricted to defined user groups.

General enrollment by all users is disabled. Only users who are members of designated enrollment groups are permitted to enroll Windows devices into Intune.

## Administrator Enrollment Controls

Administrative accounts are restricted from enrolling devices to prevent accidental bypass of standard enrollment controls.

Dedicated break glass and device staging accounts are excluded only where operationally required.

## Device Enrollment Limits

A maximum number of enrolled devices per user is enforced to limit sprawl and accidental over enrollment.

Exceptions to device limits require explicit approval and documented justification.

## Operational Impact

By enforcing enrollment restrictions and join type controls as a prerequisite, the tenant ensures that only approved devices, join types, and users can enter the managed environment. This significantly reduces unmanaged device sprawl, improves security posture, and simplifies downstream Autopilot, compliance, and troubleshooting workflows.
