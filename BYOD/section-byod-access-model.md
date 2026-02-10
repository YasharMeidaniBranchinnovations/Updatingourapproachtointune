# Bring Your Own Device (BYOD) Access Model

## Objective

Define a secure and scalable Bring Your Own Device (BYOD) access model that allows users to access Microsoft corporate applications such as Microsoft Outlook and Microsoft Teams from personal devices, while protecting organizational data and minimizing intrusion into personal device ownership.

## BYOD Position in the Intune and Zero Trust Architecture

BYOD devices are not treated as trusted endpoints. They are treated as untrusted personal devices that are granted conditional and limited access to corporate resources. Unlike corporate owned devices, BYOD devices do not participate in Windows Autopilot, Endpoint Security configuration, or full device configuration baselines. Instead, access is governed through Microsoft Entra ID, Conditional Access, Intune Mobile Application Management (MAM), and optional device compliance evaluation. This approach aligns with Zero Trust principles by assuming no inherent trust in the device and enforcing controls dynamically based on identity, application context, and device posture.

## Supported BYOD Scenarios

The BYOD model supports access to Microsoft 365 productivity applications, specifically Microsoft Outlook and Microsoft Teams, to read and respond to email and messages, participate in chats and meetings, and perform basic communication tasks. Corporate data is not intended to persist on the device outside the managed application container.

## App Only BYOD (MAM Without Enrollment)

For low risk scenarios, BYOD access is provided using Intune Mobile Application Management without device enrollment. Devices are not enrolled into Intune and are not managed at the operating system level. Management is applied only to the application container after the user signs in. Application protection policies enforce data encryption within the app, application level PIN or biometric protection, restrictions on copy and paste to unmanaged apps, prevention of saving corporate data to personal storage, and selective wipe of corporate app data if access is revoked. The device itself remains fully personal and IT has no visibility into device configuration, installed applications, or user activity outside the managed app.

## BYOD With Device Compliance Evaluation

For scenarios requiring stronger security guarantees, BYOD devices may be enrolled for compliance evaluation only. Devices are enrolled into Intune to report posture signals such as operating system version, encryption state, and device integrity but are not subject to Endpoint Security baselines or Settings Catalog configuration. Compliance policies evaluate minimum requirements such as supported OS version, encryption enabled, screen lock configuration, and detection of rooted or compromised devices. Compliance policies do not configure devices. They only assess state. Conditional Access uses compliance status to allow or block access to corporate applications.

## Conditional Access Enforcement

All BYOD access is enforced through Microsoft Entra Conditional Access. Conditional Access applies identity controls such as multi factor authentication, approved client application requirements, and blocking of legacy authentication. Where compliance evaluation is enabled, access is granted only to compliant devices. Where app only access is used, enforcement relies on identity and application signals without device trust assumptions.

## Explicit Exclusions From BYOD

BYOD devices are explicitly excluded from Windows Autopilot provisioning, Endpoint Security policies, Microsoft Defender Antivirus configuration, Attack Surface Reduction rules, Windows Firewall configuration, BitLocker and Personal Data Encryption enforcement, Windows LAPS, local administrator group enforcement, and Settings Catalog device configuration baselines. These controls apply only to corporate owned and managed devices.

## Privacy and Ownership Boundary

The BYOD model preserves personal device ownership. IT does not monitor personal activity, access personal files, install software outside approved applications, or perform full device wipe operations. When access is revoked, only corporate application data is removed and personal data remains untouched.

## Summary

The BYOD access model enables secure use of Microsoft corporate applications on personal devices without extending full device management or ownership assumptions. Low risk scenarios use app only protection through Intune MAM without enrollment. Higher risk scenarios introduce device compliance evaluation without enforcing configuration. All access decisions are enforced through identity driven Conditional Access, aligning with Microsoft recommended Intune and Zero Trust architecture.
