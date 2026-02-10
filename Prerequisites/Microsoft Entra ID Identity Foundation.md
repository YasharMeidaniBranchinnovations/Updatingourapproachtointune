# Microsoft Entra ID Identity Foundation

Windows Autopilot and Intune do not begin with devices, deployment profiles, or configuration policies. They begin with Microsoft Entra ID identity.

A valid user identity must exist in Microsoft Entra ID before any Autopilot or Intune process can occur. Devices are recognized, enrolled, and managed only after identity is established and validated. Autopilot provisioning relies on identity to authenticate users, authorize device enrollment, and determine applicable policies and applications.

Microsoft Entra ID (Identity)  
↓  
User Authentication  
↓  
Authorization & Policy Targeting  
↓  
Device Enrollment & Recognition  
↓  
Autopilot Provisioning  
↓  
Intune Configuration & Compliance  

Intune operates entirely on top of Microsoft Entra ID. All access control, policy targeting, and compliance evaluation are identity-driven. Without a functioning Entra ID identity layer, Intune cannot enroll devices, apply configuration, or enforce security controls.

Identity Failure  
├─ Device-level troubleshooting fails  
├─ Network-level troubleshooting fails  
└─ Profile-level troubleshooting fails  

If identity is misconfigured or unavailable, Autopilot provisioning fails before it meaningfully begins. Device-level, network-level, and profile-level troubleshooting will not succeed until identity is confirmed to be operational.

Before proceeding with Autopilot troubleshooting, ensure that Microsoft Entra ID identity is correctly configured and functioning as expected.
