# Autopilot Device Grouping and Deployment Profiles

## Objective

Establish the required grouping and deployment profile configuration to ensure Windows devices registered with Autopilot are correctly identified and provisioned during Windows Out-of-Box Experience through Microsoft Intune.

## High-Level End-to-End Flow

The Windows Autopilot deployment process follows a defined sequence. Device IDs are registered in the tenant and become visible to Intune. Registered devices are automatically associated with a dedicated device group. Autopilot deployment profiles are assigned to that group to define provisioning behavior. Provisioning is executed only when the device enters Windows Out-of-Box Experience with network connectivity.

This flow ensures that device recognition, targeting, and configuration remain automated and centrally managed.

## Purpose

When Windows Autopilot is used with device IDs to identify machines that will be reconfigured, an additional configuration step is required before deployment profiles can be applied. Autopilot deployment profiles do not target individual devices directly and instead rely on device-based group membership. A dedicated device group must exist to allow Autopilot to recognize and manage registered devices.

## Requirement for Device-Based Grouping

Autopilot deployment profiles require a group association to determine which devices should receive a given configuration. Even after device IDs have been imported into Intune, deployment profiles cannot be applied unless those devices are members of an appropriate group.

This group acts as the detection mechanism that links registered device identities to Autopilot deployment behavior.

## Autopilot Device Group Configuration

### Group Type

The group used for Autopilot must be a Security group, as security groups are the only group type capable of containing devices.

### Membership Type

For Autopilot scenarios involving new or incoming devices, the group must be configured as a Dynamic device group. Dynamic membership ensures that devices are automatically included as soon as their device ID is registered in the tenant.

Static groups may be used for existing devices, but they require manual population and are not suitable for zero-touch provisioning workflows.

### Dynamic Membership Logic

The dynamic device group uses a rule that identifies all devices registered with Windows Autopilot. Microsoft provides a supported query that evaluates whether a device has an Autopilot device ID associated with it.

Once this rule is applied, any device registered in Autopilot is automatically added to the group without manual intervention. This enables newly purchased devices to be recognized immediately when they first connect during setup.

## Role of the Autopilot Device Group

The Autopilot device group serves as the targeting mechanism for deployment profiles. Any device included in this group becomes eligible to receive Autopilot provisioning when it enters Windows Out-of-Box Experience.

Without this group, deployment profiles have no method to identify which devices should be provisioned through Autopilot.

## Windows Autopilot Deployment Profiles

### Scope and Platform

Autopilot deployment profiles apply only to Windows devices. Autopilot is supported on Windows 10 and later and is not available for other operating systems. Deployment profiles are created under Windows enrollment within Intune.

### Deployment Profile Configuration

#### Deployment Mode

Deployment profiles support different provisioning modes, including user-driven and self-deploying. User-driven deployment allows limited user interaction during setup, while self-deploying restricts user input and automates the process.

#### Join Type

Profiles define whether devices join Microsoft Entra ID directly or perform a hybrid join with on-premises Active Directory.

#### User Experience Controls

Profiles control whether software license terms, privacy settings, and account configuration options are shown to users. Hiding these options results in acceptance on behalf of the user and enforces standardized configuration.

It is recommended to prevent users from selecting administrative privileges during setup by enforcing standard user configuration.

#### Pre-Provisioned Deployment

Profiles may allow pre-provisioned deployment, previously referred to as white glove. This option supports scenarios where devices are prepared in advance with applications and policies and later handed off to users without reinstalling content.

#### Language and Region Settings

Profiles can specify default language, region, and keyboard settings, or allow users to select these values during setup depending on deployment requirements.

#### Device Naming

Deployment profiles support device naming templates to enforce consistent naming conventions. Templates may include static prefixes and randomized values to ensure uniqueness across devices.

### Profile Assignment

Deployment profiles are assigned through group association rather than direct device targeting. The dynamic Autopilot device group is assigned as an included group for the profile.

Exclusion groups may also be configured. In Intune, exclusions always take precedence over inclusions.

Once assigned, the profile is associated with all devices that are members of the group.

## Converting Existing Devices to Autopilot

Deployment profiles include an option to automatically register targeted devices with Autopilot if they are not already registered. When enabled, devices in the assigned group become Autopilot-capable.

This does not immediately impact devices. Autopilot provisioning occurs only when a device is reset and enters Windows Out-of-Box Experience.

## Automatic Enrollment Prerequisite

For Autopilot provisioning to complete successfully, automatic enrollment must be enabled in Intune. MDM and MAM auto-enrollment settings must be configured to allow enrollment for the intended scope.

In newly configured Intune tenants, these settings may be disabled by default and must be explicitly enabled.

## Tenant Branding During Autopilot

Company branding configured in Microsoft Entra ID controls the visual and textual experience presented during user sign-in. This includes logos, background elements, and custom sign-in messaging.

Branding is optional but provides a consistent organizational experience during Autopilot-driven setup.

## Resulting Configuration State

After completing device group creation, deployment profile configuration, profile assignment, and prerequisite settings, Autopilot-registered devices are dynamically grouped, deployment profiles are correctly associated, and devices are prepared for automated provisioning during Windows Out-of-Box Experience.

At this point, the Autopilot deployment configuration is complete and operational.
