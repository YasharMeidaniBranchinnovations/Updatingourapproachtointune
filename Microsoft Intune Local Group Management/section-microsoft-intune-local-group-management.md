# Microsoft Intune Local Group Management

## Objective

Explain how local Windows group membership is centrally managed using Microsoft Intune to provide consistent administrative rights across managed devices without manual intervention.

## High Level End to End Workflow

Windows devices contain local users and local groups that control permissions on the device itself. Traditionally, administrators managed these groups manually or through on-premises group policy. With Intune, local group membership can be managed centrally by deploying a policy that adds or removes users or groups from local Windows groups on enrolled devices. Policies are evaluated and applied by Intune MDM and enforced on devices during sync cycles.

## Local Groups on Windows Devices

All Windows machines include built in local groups such as Administrators and Remote Desktop Users. Membership in these groups determines local privileges on the device. These groups can be viewed locally through Computer Management under Local Users and Groups. Each member is identified internally using a Security Identifier, or SID, which uniquely represents users, groups, and system services.

## Challenges with Manual Administration

Manually managing local group membership does not scale. In environments with hundreds or thousands of devices, adding a user to a local group on each machine is not practical. Traditional domain environments addressed this through Group Policy restricted groups, but this approach does not apply to cloud-managed or Intune-only devices.

## Intune Based Local Group Management

Microsoft Intune provides a centralized method for managing local group membership through Endpoint Security policies. This allows administrators to define which users or groups should be members of specific local Windows groups across all managed devices.

## Policy Location

Local group membership policies are created in the Intune admin center under Endpoint Security in the Account Protection section. The Local user group membership profile type is used for this purpose and supports Windows 10 and later devices.

## Policy Configuration

When creating the policy, administrators select the target local group such as Administrators or Remote Desktop Users. Membership can be defined by adding users or groups from Microsoft Entra ID, specifying local accounts manually, or using security identifiers. The policy can add, remove, or replace group members depending on the chosen configuration.

## Assignments and Scope

The policy is assigned to device groups, user groups, or all devices as required. Exclusions may also be defined. If a device or user is part of both an included and excluded assignment, the exclusion always takes precedence. This behavior is consistent across Intune policies.

## Policy Application and Sync Behavior

Once assigned, the policy is delivered to devices through the Intune MDM channel. Policy application is not immediate and may take up to an hour depending on device sync timing. Administrators may manually trigger a device sync from the Intune admin center to accelerate policy delivery. A device reboot may also help ensure changes are applied promptly.

## Verification on the Device

After the policy is applied, the local group membership can be verified directly on the device through Computer Management. The targeted user or group will appear as a member of the specified local group, confirming successful policy enforcement.

## Operational Impact

This approach ensures consistent local privilege management across all Intune managed devices. Administrative access is granted centrally, auditable, and automatically enforced without requiring manual configuration on individual machines.

## Summary

Microsoft Intune enables centralized management of local Windows group membership through Endpoint Security account protection policies. These policies allow administrators to add or remove users from local groups across all managed devices. Policy delivery is handled by Intune MDM and applied during device sync cycles. This method replaces manual configuration and legacy group policy approaches for cloud managed environments while providing scalable and consistent access control.
