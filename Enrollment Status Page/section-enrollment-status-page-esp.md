# Enrollment Status Page (ESP)

## Objective

Describe the role of the Enrollment Status Page in Microsoft Intune and how it integrates with Windows Autopilot to control visibility, behavior, and user access during device provisioning.

## High-Level End-to-End Flow

During Windows Autopilot provisioning, the Enrollment Status Page is evaluated once the device enters Out-of-Box Experience and begins enrollment. If enabled and assigned, the Enrollment Status Page displays provisioning progress, enforces installation requirements, and optionally restricts device access until required apps and profiles are installed.

This ensures controlled and observable provisioning during initial setup and first user sign-in.

## Overview of the Enrollment Status Page

The Enrollment Status Page is an Intune feature that governs what users see and what actions are permitted while a device is being provisioned. It applies during initial device setup and first user sign-in when devices are enrolled through Autopilot.

By default, a single Enrollment Status Page configuration exists and applies to all users and all devices.

## Default Enrollment Status Page Configuration

The default Enrollment Status Page is assigned globally. It determines whether users can see provisioning progress and whether device usage is restricted while applications and profiles are being installed.

If progress display is disabled, users see no indication of provisioning activity during Autopilot deployment.

## Enrollment Status Page Settings

Enrollment Status Page settings control multiple aspects of the provisioning experience, including visibility, error handling, and access restrictions.

Key configuration options include displaying application and profile installation progress, showing error messages if installation exceeds a defined time threshold, enabling diagnostic log collection, and displaying custom status messages.

The page can also be restricted to devices provisioned through Out-of-Box Experience only.

## Device Access Control During Provisioning

The Enrollment Status Page can block device use until required applications and profiles are installed. When enabled, users cannot access the desktop until provisioning completes successfully.

Additional controls allow users to reset the device or continue using the device if errors occur, depending on organizational policy.

## Creating Additional Enrollment Status Page Profiles

Beyond the default configuration, additional Enrollment Status Page profiles can be created to support different device or user scenarios.

Each profile can be configured with its own settings and assigned to specific device or user groups. This allows differentiated provisioning behavior across environments, device types, or user populations.

## Assignment and Priority

Enrollment Status Page profiles are evaluated based on priority. Profiles assigned to specific groups take precedence over the default configuration.

When multiple profiles exist, priority order determines which configuration is applied. Higher-priority profiles override lower-priority profiles.

## Administrative Scope

Enrollment Status Page profiles may optionally include administrative scope tags. These tags control which administrators can view or manage the profile and do not affect device behavior during provisioning.

## Operational Impact

While not mandatory, the Enrollment Status Page improves transparency during Autopilot deployment and provides additional safeguards during provisioning. It helps users understand provisioning progress and enables administrators to enforce completion of required configuration before device use.

## Summary

The Enrollment Status Page enhances the Windows Autopilot experience by controlling visibility, enforcement, and user interaction during device enrollment. It can be applied globally or targeted to specific groups, supports priority-based evaluation, and plays a key role in ensuring consistent and controlled device provisioning.
