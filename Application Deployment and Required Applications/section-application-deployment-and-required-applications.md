# Microsoft Intune Windows Architecture

Read and implement in order. Each section depends on the previous one.

---

## Start to End Read Order

### 1. Identity and Control Foundation

1. [Microsoft Entra ID Identity Foundation](Microsoft%20Entra%20ID%20Identity%20Foundation/section-microsoft-entra-id-identity-foundation.md)
2. [Microsoft Entra ID Grouping and Targeting Model](Microsoft%20Entra%20ID%20Grouping%20and%20Targeting%20Model/section-microsoft-entra-id-grouping-and-targeting-model.md)
3. [Microsoft Intune Role Based Access Control](Microsoft%20Intune%20Role%20Based%20Access%20Control/section-microsoft-intune-role-based-access-control.md)

---

### 2. Enrollment Control and Device Entry

4. [Windows Enrollment Restrictions and Allowed Join Types](Windows%20Enrollment%20Restrictions%20and%20Allowed%20Join%20Types/section-windows-enrollment-restrictions-and-allowed-join-types.md)
5. [Bring Your Own Device%20(BYOD)%20Access%20Model](Bring%20Your%20Own%20Device%20(BYOD)%20Access%20Model/section-byod-access-model.md)

---

### 3. Windows Autopilot Provisioning

6. [Windows Autopilot Device Registration](Windows%20Autopilot%20Device%20Registration/section-windows-autopilot-device-registration.md)
7. [Autopilot Device Grouping and Deployment Profiles](Autopilot%20Device%20Grouping%20and%20Deployment%20Profiles/section-autopilot-device-grouping-and-deployment-profiles.md)
8. [Enrollment Status Page%20(ESP)](Enrollment%20Status%20Page%20(ESP)/section-enrollment-status-page-esp.md)
9. [Triggering Autopilot Provisioning and Verifying Deployment](Triggering%20Autopilot%20Provisioning%20and%20Verifying%20Deployment/section-triggering-autopilot-provisioning-and-verifying-deployment.md)
10. [Troubleshooting Windows Autopilot Deployments](Troubleshooting%20Windows%20Autopilot%20Deployments/section-troubleshooting-windows-autopilot-deployments.md)

---

### 4. Compliance, Trust, and Access Enforcement

11. [Microsoft Intune Compliance Policies](Microsoft%20Intune%20Compliance%20Policies/section-microsoft-intune-compliance-policies.md)
12. [Microsoft Intune Windows Compliance Baseline](Microsoft%20Intune%20Windows%20Compliance%20Baseline/section-microsoft-intune-windows-compliance-baseline.md)
13. [Conditional Access Integration and Enforcement Model](Conditional%20Access%20Integration%20and%20Enforcement%20Model/section-conditional-access-integration-and-enforcement-model.md)

---

### 5. Endpoint Security and Privilege Control

14. [Microsoft Intune Endpoint Security Configuration Policies](Microsoft%20Intune%20Endpoint%20Security%20Configuration%20Policies/section-microsoft-intune-endpoint-security-configuration-policies.md)
15. [Microsoft Intune Local Group Management](Microsoft%20Intune%20Local%20Group%20Management/section-microsoft-intune-local-group-management.md)

---

### 6. Configuration Hardening

16. [Microsoft Intune Settings Catalog Configuration Policies](Microsoft%20Intune%20Settings%20Catalog%20Configuration%20Policies/section-microsoft-intune-settings-catalog-configuration-policies.md)

---

### 7. Applications and Productivity

17. [Application Deployment and Required Applications](Application%20Deployment%20and%20Required%20Applications/section-application-deployment-and-required-applications.md)
18. [Microsoft Intune Remote Help](Microsoft%20Intune%20Remote%20Help/section-microsoft-intune-remote-help.md)

---

### 8. Updates and Lifecycle Control

19. [Windows Update for Business Ring Model%20(WUfB)](Windows%20Update%20for%20Business%20Ring%20Model%20(WUfB)/section-windows-update-for-business-ring-model.md)

---

### 9. Health Monitoring and Validation

20. [Microsoft Intune Tenant Platform Health Monitoring%20%E2%80%93%20Endpoint%20Analytics](Microsoft%20Intune%20Tenant%20Platform%20Health%20Monitoring%20%E2%80%93%20Endpoint%20Analytics/section-microsoft-intune-tenant-platform-health-monitoring-endpoint-analytics.md)

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
