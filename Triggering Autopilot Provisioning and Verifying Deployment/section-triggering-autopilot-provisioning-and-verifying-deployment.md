# Triggering Autopilot Provisioning and Verifying Deployment

## Objective

Demonstrate how a registered device enters Windows Out-of-Box Experience, triggers Autopilot provisioning, and is validated as successfully deployed and managed within Microsoft Intune.

## High-Level End-to-End Flow

Once a device has been registered with Autopilot, included in the Autopilot device group, and associated with a deployment profile, provisioning is initiated when the device enters Windows Out-of-Box Experience. During this phase, Autopilot applies the assigned configuration, enrolls the device into Intune, and completes setup. After provisioning, the device state can be verified within both the operating system and the Intune admin center.

## Initiating Out-of-Box Experience

For existing devices used in testing or demonstrations, Windows Out-of-Box Experience can be manually triggered to simulate a new device deployment. This forces the device to restart and re-enter the setup experience.

For newly purchased devices, this step is not required. New devices ship in Out-of-Box Experience by default and will automatically begin the Autopilot process upon first boot and network connectivity.

## Autopilot Provisioning Experience

When the device enters Out-of-Box Experience and connects to the internet, Autopilot recognizes the device based on its registered device ID. The sign-in experience reflects tenant-specific branding configured in Microsoft Entra ID.

After authentication, the Enrollment Status Page displays provisioning progress. This includes stages such as device preparation, device setup, and account setup. The duration of this process varies depending on assigned policies, applications, and network conditions.

During this phase, the device may restrict user access until required configuration is completed, depending on Enrollment Status Page settings.

## Completion of Provisioning

Once all provisioning stages complete successfully, the device proceeds to the Windows sign-in screen. At this point, the device has been reset, configured, and enrolled according to the assigned Autopilot deployment profile.

After signing in, the device is fully operational and managed through Intune.

## Device State Validation on the Endpoint

From the device itself, the connection to the organization can be verified through Windows settings under access to work or school. The device should display a connection to the organization’s Microsoft Entra tenant, confirming successful enrollment.

Depending on the deployment profile configuration, the device may be joined to Microsoft Entra ID only or to a hybrid environment. Domain join behavior reflects the options selected during deployment profile configuration.

## Verification in Microsoft Intune

Within the Intune admin center, the deployed device appears under Windows devices, confirming that enrollment has completed successfully. Initial compliance status may show as not yet evaluated until compliance policies are processed.

The device also appears under Windows Autopilot devices with its deployment status updated to assigned, indicating that an Autopilot deployment profile has been successfully applied.

## Deployment Profile Confirmation

Deployment profiles display associated devices, allowing verification that the intended profile was applied to the correct hardware identity. This confirms end-to-end alignment between device registration, group targeting, and deployment configuration.

## Resulting State

At the conclusion of this process:

- The device has completed Autopilot provisioning  
- The deployment profile has been successfully applied  
- The device is enrolled and visible in Intune  
- The device is associated with the correct tenant and configuration  

This confirms successful execution of the Windows Autopilot deployment lifecycle.
