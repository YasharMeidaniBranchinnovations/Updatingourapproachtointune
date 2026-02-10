# Microsoft Intune Windows Architecture – Start to Finish

This repository defines a **complete, ordered Microsoft Intune architecture** for managing Windows devices.

It is not a collection of documents.  
It is a **pipeline**.

Read and implement **top to bottom**.  
Each section depends on the previous one.

---

## Architecture Read Order

### 1. Identity and Administrative Control

These sections define identity, grouping, and administrative boundaries.  
Nothing else works if these are wrong.

1. [Microsoft Entra ID Identity Foundation](Prerequisites/Microsoft-EntraID-Identity-Foundation.md)
2. [Microsoft Entra ID Grouping and Targeting Model](Prerequisites/Microsoft-Entra%20ID-Grouping-and-Targeting-Model.md)
3. [Microsoft Intune Role Based Access Control](Microsoft%20Intune%20Role%20Based%20Access%20Control/section-microsoft-intune-role-based-access-control.md)

---

### 2. Enrollment Control and Device Entry

These sections control **who is allowed to enroll** and **how devices are permitted to enter** the environment.

4. [Windows Enrollment Restrictions and Allowed Join Types](Windows%20Enrollment%20Restrictions%20and%20Allowed%20Join%20Types/section-windows-enrollment-restrictions-and-allowed-join-types.md)
5. [Bring Your Own Device (BYOD) Access Model](Bring%20Your%20Own%20Device%20(BYOD)%20Access%20Model/section-byod-access-model.md)

---

### 3. Windows Autopilot Provisioning

These sections define **zero touch provisioning from OOBE to ready state**.

6. [Windows Autopilot Device Registration](Windows%20Autopilot%20Device%20Registration/section-windows-autopilot-device-registration.md)
7. [Autopilot Device Grouping and Deployment Profiles](Autopilot%20Device%20Grouping%20and%20Deployment%20Profiles/section-autopilot-device-grouping-and-deployment-profiles.md)
8. [Enrollment Status Page (ESP)](Enrollment%20Status%20Page%20(ESP)/section-enrollment-status-page-esp.md)
9. [Triggering Autopilot Provisioning and Verifying Deployment](Triggering%20Autopilot%20Provisioning%20and%20Verifying%20Deployment/section-triggering-autopilot-provisioning-and-verifying-deployment.md)
10. [Troubleshooting Windows Autopilot Deployments](Troubleshooting%20Windows%20Autopilot%20Deployments/section-troubleshooting-windows-autopilot-deployments.md)

---

### 4. Compliance, Trust, and Access Enforcement

These sections define **when a device is trusted** and **how access is enforced**.

11. [Microsoft Intune Compliance Policies](Microsoft%20Intune%20Compliance%20Policies/section-microsoft-intune-compliance-policies.md)
12. [Microsoft Intune Windows Compliance Baseline](Microsoft%20Intune%20Windows%20Compliance%20Baseline/section-microsoft-intune-windows-compliance-baseline.md)
13. [Conditional Access Integration and Enforcement Model](Conditional%20Access%20Integration%20and%20Enforcement%20Model/section-conditional-access-integration-and-enforcement-model.md)

---

### 5. Endpoint Security and Privilege Protection

These sections define the **mandatory security baseline**.  
Nothing overrides this layer.

14. [Microsoft Intune Endpoint Security Configuration Policies](Microsoft%20Intune%20Endpoint%20Security%20Configuration%20Policies/section-microsoft-intune-endpoint-security-configuration-policies.md)
15. [Microsoft Intune Local Group Management](Microsoft%20Intune%20Local%20Group%20Management/section-microsoft-intune-local-group-management.md)

---

### 6. Operating System Configuration Hardening

These sections define **how Windows behaves** after security is enforced.

16. [Microsoft Intune Settings Catalog Configuration Policies](Microsoft%20Intune%20Settings%20Catalog%20Configuration%20Policies/section-microsoft-intune-settings-catalog-configuration-policies.md)

---

### 7. Applications and Productivity Enablement

These sections define **what makes a device usable**.

17. [Application Deployment and Required Applications](Application%20Deployment%20and%20Required%20Applications/section-application-deployment-and-required-applications.md)
18. [Microsoft Intune Remote Help](Microsoft%20Intune%20Remote%20Help/section-microsoft-intune-remote-help.md)

---

### 8. Updates and Change Control

These sections define **how change is introduced safely**.

19. [Windows Update for Business Ring Model (WUfB)](Windows%20Update%20for%20Business%20Ring%20Model%20(WUfB)/section-windows-update-for-business-ring-model.md)

---

### 9. Health Monitoring and Validation

This section defines **how you know the platform is actually healthy**.

20. [Microsoft Intune Tenant Platform Health Monitoring – Endpoint Analytics](Microsoft%20Intune%20Tenant%20Platform%20Health%20Monitoring%20%E2%80%93%20Endpoint%20Analytics/section-microsoft-intune-tenant-platform-health-monitoring-endpoint-analytics.md)

---

## One Line Mental Model

Identity decides who  
Enrollment decides if  
Autopilot decides how  
Security decides trust  
Configuration decides behavior  
Applications decide usability  
Updates decide stability  
Analytics decides truth

---

## Rule for This Repository

- One folder = one architectural stage
- Folder name = section title
- Section file lives inside the folder
- Read order is enforced by this README
- Do not reorganize without changing the pipeline

This is intentional.
