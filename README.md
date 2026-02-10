# Microsoft Intune Windows Architecture – Start to Finish

This repository is a **step by step Intune implementation pipeline**.

Each section depends on the previous one.  
Do not skip steps. Do not reorder sections.

---

## Read Order (This Is the Architecture)

### 1. Identity and Control Foundation
Everything starts with identity. Nothing works without this.

1. [Microsoft Entra ID Identity Foundation](section-microsoft-entra-id-identity-foundation.md)
2. [Microsoft Entra ID Grouping and Targeting Model](section-microsoft-entra-id-grouping-and-targeting-model.md)
3. [Microsoft Intune Role Based Access Control](section-microsoft-intune-role-based-access-control.md)

---

### 2. Enrollment Control and Device Entry
Defines **who is allowed to enroll** and **how devices enter**.

4. [Windows Enrollment Restrictions and Allowed Join Types](section-windows-enrollment-restrictions-and-allowed-join-types.md)
5. [Bring Your Own Device (BYOD) Access Model](section-byod-access-model.md)

---

### 3. Windows Autopilot Provisioning
Defines **zero touch provisioning from OOBE to ready state**.

6. [Windows Autopilot Device Registration](section-windows-autopilot-device-registration.md)
7. [Autopilot Device Grouping and Deployment Profiles](section-autopilot-device-grouping-and-deployment-profiles.md)
8. [Enrollment Status Page (ESP)](section-enrollment-status-page.md)
9. [Triggering Autopilot Provisioning and Verifying Deployment](section-triggering-autopilot-provisioning-and-verifying-deployment.md)
10. [Troubleshooting Windows Autopilot Deployments](section-troubleshooting-windows-autopilot-deployments.md)

---

### 4. Compliance, Trust, and Access Enforcement
Defines **when a device is trusted** and **how access is enforced**.

11. [Microsoft Intune Compliance Policies](section-microsoft-intune-compliance-policies.md)
12. [Microsoft Intune Windows Compliance Baseline](section-microsoft-intune-windows-compliance-baseline.md)
13. [Conditional Access Integration and Enforcement Model](section-conditional-access-integration-and-enforcement-model.md)

---

### 5. Endpoint Security (Mandatory First Security Layer)
Defines **core device protection**. Nothing overrides this layer.

14. [Microsoft Intune Endpoint Security Configuration Policies](section-microsoft-intune-endpoint-security-configuration-policies.md)
15. [Microsoft Intune Local Group Management](section-microsoft-intune-local-group-management.md)

---

### 6. Configuration Hardening (After Security)
Defines **how Windows behaves**, not how it is protected.

16. [Microsoft Intune Settings Catalog Configuration Policies](section-microsoft-intune-settings-catalog-configuration-policies.md)

---

### 7. Applications and Productivity
Defines **what makes the device usable**.

17. [Application Deployment and Required Applications](section-application-deployment-and-required-applications.md)
18. [Microsoft Intune Remote Help](section-microsoft-intune-remote-help.md)

---

### 8. Updates and Lifecycle Control
Defines **how change is introduced safely**.

19. [Windows Update for Business Ring Model](section-windows-update-for-business-ring-model.md)

---

### 9. Health Monitoring and Validation
Defines **how you know everything is working**.

20. [Microsoft Intune Tenant Platform Health Monitoring – Endpoint Analytics](section-microsoft-intune-tenant-platform-health-monitoring-endpoint-analytics.md)

---

## One Sentence Mental Model

Identity decides **who**  
Enrollment decides **if**  
Autopilot decides **how**  
Security decides **trust**  
Configuration decides **behavior**  
Applications decide **usability**  
Updates decide **stability**  
Analytics decides **truth**

---

## If Something Breaks

Find the step where it belongs.  
Do not debug outside its layer.  
Do not fix problems downstream.

That is the architecture.
