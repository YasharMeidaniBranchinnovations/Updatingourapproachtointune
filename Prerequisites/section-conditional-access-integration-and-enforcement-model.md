# Conditional Access Integration and Enforcement Model

## Objective

Define how Microsoft Entra Conditional Access enforces access controls by consuming identity and device compliance signals evaluated by Microsoft Intune.

Conditional Access is the enforcement layer that ensures access to organizational resources is granted only when defined identity, authentication, and device trust conditions are met. While Microsoft Intune evaluates device compliance, Conditional Access is responsible for translating that compliance state into real access decisions.

## Role of Conditional Access in the Architecture

Microsoft Entra Conditional Access functions as the Zero Trust policy engine for the tenant. All access to cloud resources is evaluated dynamically at sign-in based on identity context and risk signals. Conditional Access does not configure devices and does not evaluate compliance rules. It consumes signals produced by other systems and enforces access decisions accordingly.

## Separation of Responsibilities

Microsoft Intune acts as the device compliance evaluator. It assesses device health and security posture using compliance policies and reports a final compliance state for each device.

Microsoft Entra Conditional Access acts as the access enforcement engine. It consumes identity, authentication, and device compliance signals and determines whether access is allowed, restricted, or blocked. Conditional Access does not require knowledge of individual compliance policy settings. Enforcement is based solely on the final compliance result reported by Intune.

## Dependency on Microsoft Entra ID Identity

Conditional Access is fully identity-driven. All enforcement decisions are evaluated only after a user successfully authenticates using a Microsoft Entra ID identity. Without a valid Entra ID identity, Conditional Access policies cannot be evaluated. Device state, compliance, and risk signals are always assessed in the context of an authenticated user session.

## Control Statement

Access to organizational cloud resources is permitted only when Conditional Access requirements are satisfied. Device compliance alone does not restrict access. Enforcement occurs exclusively through Microsoft Entra Conditional Access policies.

## Primary Conditional Access Enforcement Patterns

Conditional Access policies are implemented using the following standard enforcement patterns, aligned with Microsoft recommended best practices and Zero Trust architecture.

### Require Compliant Device

Access to Microsoft 365 and other protected cloud applications requires the device to be marked compliant by Microsoft Intune. This ensures that only devices meeting the defined security baseline are permitted to access organizational resources.

### Multi Factor Authentication Enforcement

Multi factor authentication is required based on user role, application sensitivity, and sign-in risk. Privileged and administrative roles are always subject to multi factor authentication requirements.

### Legacy Authentication Blocking

Legacy authentication protocols are blocked using Conditional Access policies to prevent bypass of modern authentication, device compliance evaluation, and MFA enforcement.

### Approved Application Access

Where supported, access from unmanaged or BYOD devices is limited to approved client applications protected by application protection policies. This allows controlled access without extending full device trust to personal endpoints.

### Session Controls

Session controls are applied where required to reduce risk. These controls may include limiting session duration, enforcing reauthentication, or restricting data access behavior for high-risk scenarios.

### Emergency Access Considerations

Emergency access, also known as break glass accounts, is explicitly excluded from broad Conditional Access enforcement to prevent tenant lockout scenarios. These accounts are tightly controlled, monitored, and used only for emergency recovery.

## Operational Impact

By integrating Conditional Access as a prerequisite, device compliance transitions from a reporting mechanism into an enforceable access control. This model ensures that access decisions are identity-driven, risk-aware, and consistently enforced across the tenant, closing the loop between device state, identity, and resource access.
