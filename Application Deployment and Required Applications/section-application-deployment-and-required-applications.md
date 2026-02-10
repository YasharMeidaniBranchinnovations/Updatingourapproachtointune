# Application Deployment and Required Applications

## Objective

Define how applications are delivered, enforced, and validated during Windows Autopilot provisioning to ensure that a device exiting enrollment is fully operational, role appropriate, and ready for productive use.

## Why This Layer Exists

Enrollment, identity, and security establish trust, but they do not make a device usable. A successfully enrolled and secured device with no applications is not a complete deployment. Application deployment is therefore treated as a first class layer of the Autopilot build process. This layer defines what software exists on the device, how it is delivered, how it is updated, and what constitutes a production ready endpoint.

## Position in the Autopilot Flow

Application deployment occurs after Microsoft Entra ID authentication and Intune enrollment and is enforced during provisioning through the Enrollment Status Page when configured. Required applications are installed before the user is granted access to the desktop. Optional applications are made available after provisioning through the Company Portal. A device is not considered complete until required applications are installed successfully.

## Application Delivery Mechanisms in Intune

Applications are delivered using supported Microsoft Intune application models. Win32 applications are used for line of business software, developer tooling, utilities, and any application requiring custom installation logic, detection rules, or dependency handling. Microsoft Store applications are used where supported to simplify installation and servicing. Microsoft 365 Apps for Windows are deployed using the native Microsoft 365 Apps deployment model to ensure consistent configuration and update behavior. PowerShell scripts are used only where an application cannot be packaged cleanly or where post installation configuration is required.

## Core Required Application Baseline

Every provisioned device must meet a defined core application baseline before it is considered ready. This baseline applies to all corporate managed devices regardless of role and represents the minimum software required for identity access, communication, and productivity.

The following applications are mandatory on all devices and are deployed as required applications through Intune. Microsoft 365 Apps for Windows are installed to provide Outlook, Microsoft Teams, Word, Excel, PowerPoint, and supporting productivity services. Microsoft Edge is installed and managed to ensure compatibility with Microsoft identity, Conditional Access enforcement, and Microsoft 365 application integrations. The Intune Company Portal is installed to provide user self service access to optional applications, remediation actions, and device information. Where Microsoft Defender for Endpoint is used, the Defender for Endpoint onboarding package is installed to enable endpoint detection, device risk signaling, and integration with Conditional Access.

Where access to internal resources requires a network access client, the approved VPN or Zero Trust network agent is included as part of the core baseline. If the organization operates fully on SaaS services, this component is omitted.

These applications are enforced during provisioning. If any core required application fails to install, the Enrollment Status Page blocks device access and provisioning does not complete.

## Role Based Required Applications

Beyond the core baseline, additional applications are deployed based on role. Role based applications are required for specific job functions and are assigned automatically using Microsoft Entra ID group membership. Users do not choose these applications and cannot remove them.

For development roles, required applications include Visual Studio Code, Git for Windows, Windows Subsystem for Linux, and Docker Desktop or equivalent container tooling where applicable. For analytics and business intelligence roles, required applications include Power BI Desktop and any approved data access or modeling tools required for reporting or analysis. For IT operations and support roles, required applications include Microsoft Intune Remote Help and approved administrative or diagnostic tooling necessary to support end users and managed devices.

Role based applications are installed automatically during or immediately after provisioning depending on enforcement requirements. Where role based applications are critical for day one productivity, they may be enforced during the Enrollment Status Page. Where timing is less critical, they are installed post sign in but remain required.

## Optional Applications

Applications that are not required for baseline operation or role fulfillment are published as optional. Optional applications are delivered through the Intune Company Portal and may be installed by the user on demand without administrative rights. Examples include secondary browsers such as Google Chrome or Mozilla Firefox, non essential developer utilities, productivity add ons, and other approved tools. Optional applications never block provisioning and are not part of the device readiness definition.

## Dependency Handling and Installation Order

Where application dependencies exist, Intune dependency handling is used to enforce correct installation order. Core required applications are installed and evaluated first, followed by role based required applications. Optional applications are excluded from provisioning dependency chains to avoid unnecessary delays or failures.

## Update Ownership and Responsibility

Update responsibility is explicitly defined per application. Applications deployed and managed through Intune follow Intune controlled update behavior. Applications with built in vendor update mechanisms are allowed to update themselves unless explicitly restricted. Ownership of update responsibility is documented to prevent overlap, missed updates, or conflicting servicing models.

## Definition of a Ready Device

A device is considered ready when identity enrollment has completed, Endpoint Security baselines are enforced, required configuration policies are applied, and all core required and role based required applications have installed successfully. At this point, the user can sign in and begin work without additional setup, administrative access, or manual software installation.

## Operational Impact

Treating applications as a formal provisioning layer ensures consistency across deployments, reduces support burden, and eliminates post enrollment manual work. Users receive a predictable experience, IT maintains control over required software, and Autopilot delivers a complete end to end provisioning outcome rather than a partially configured system.

## Summary

Application deployment completes the Autopilot lifecycle. Identity establishes trust, security establishes protection, configuration defines behavior, and applications enable productivity. A device exiting Autopilot without its required applications is not complete. This model ensures every device is secure, configured, and immediately usable.
