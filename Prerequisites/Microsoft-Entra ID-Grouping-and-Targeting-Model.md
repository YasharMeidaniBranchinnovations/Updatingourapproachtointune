# Microsoft Entra ID Grouping and Targeting Model

## Objective

This section defines a standardized Microsoft Entra ID grouping and targeting model that governs how users and devices are identified, categorized, and targeted across all Microsoft Intune and Windows Autopilot workflows.

This grouping model is a foundational prerequisite. All Autopilot provisioning, policy enforcement, application deployment, compliance evaluation, and security controls depend on the existence of consistent and well-defined group structures. Without this model, downstream configuration becomes inconsistent, difficult to troubleshoot, and non-scalable.

## Design Principles

The grouping and targeting model is based on the following principles:

- Groups express intent, not configuration  
- Identity attributes are used as inputs, not deployment targets  
- Policies and applications are never assigned directly to raw identity data  
- Targeting logic is defined once and reused consistently  
- Exclusions always take precedence over inclusions  
- Group purpose is explicit, limited, and auditable  

## Group Type Classification

Microsoft Entra ID groups are divided into four functional categories. Each category has a specific purpose and defined usage boundaries.

### Identity Groups

**Purpose**

Identity groups represent organizational facts derived from Microsoft Entra ID attributes such as department, job function, or employment type.

**Characteristics**

- User-based  
- Typically dynamic  
- Sourced from directory or HR-managed attributes  
- No configuration, policy, or deployment logic attached  

**Examples**

- ID-Dept-Engineering  
- ID-Dept-Finance  
- ID-Employment-Contractor  

**Usage Rules**

Identity groups are never assigned directly to Microsoft Intune policies, applications, scripts, or Windows Autopilot deployment profiles. They are used exclusively as inputs for role determination.

### Device State Groups

**Purpose**

Device state groups describe technical characteristics or lifecycle state of devices.

**Characteristics**

- Device-based  
- Usually dynamic  
- Evaluated based on operating system, enrollment method, ownership, or platform  

**Examples**

- DEV-Platform-Windows  
- DEV-Enrollment-Autopilot  
- DEV-Ownership-Corporate  

**Usage Rules**

Device state groups are used for baseline security enforcement, enrollment configuration, and platform-specific targeting. They do not represent business role or functional intent.

### Role Groups

**Purpose**

Role groups define functional intent and required capabilities for users or devices.

**Characteristics**

- Usually user-based  
- May be dynamic or static  
- Derived from one or more identity groups  
- Represent how a device is expected to be used  

**Examples**

- ROLE-Developer  
- ROLE-Finance  
- ROLE-Operations  
- ROLE-Executive  

**Role Mapping Model**

Departments and identity attributes are mapped to role groups. Multiple departments may map to the same role. Exceptions are handled through explicit role group membership rather than modification of identity attributes.

**Usage Rules**

Role groups act as the logical source for role-specific applications, configuration, and access controls. They are not targeted directly by Intune workloads.

### Assignment Groups

**Purpose**

Assignment groups are technical containers used directly by Microsoft Intune for assigning policies, applications, scripts, and profiles.

**Characteristics**

- User-based or device-based  
- Static or dynamic  
- Contain no business logic  
- Fully replaceable without affecting identity structure  

**Examples**

- ASG-WIN-BASELINE-SECURITY  
- ASG-WIN-ROLE-DEV-APPS  
- ASG-WIN-ESP-REQUIRED  

**Usage Rules**

All Intune assignments target assignment groups only. No policy, application, or configuration profile is assigned directly to identity groups or role groups.

## User Versus Device Targeting

Targeting decisions follow a consistent rule set:

- Device-based groups are used for security posture, enrollment, compliance, and operating system configuration  
- User-based groups are used for applications, role capabilities, and user experience  

This separation ensures that device trust is enforced regardless of user sign-in, while applications and role-based tools follow the user.

## Naming Convention

All groups follow a prefix-based naming convention to ensure clarity, filtering, and auditability.

- ID- prefix for identity groups  
- DEV- prefix for device state groups  
- ROLE- prefix for functional role groups  
- ASG- prefix for Intune assignment groups  

Naming conventions are applied consistently across environments.

## Assignment and Exclusion Rules

- All Intune policies, applications, and profiles are assigned to assignment groups only  
- Identity and role groups are never targeted directly  
- Exclusion groups always take precedence over inclusion groups  
- Exclusions are used sparingly and require explicit justification  

## Operational Impact

Defining the grouping and targeting model as a prerequisite ensures that all downstream Autopilot and Intune configuration is deterministic, repeatable, and auditable. Changes to user role or device purpose are handled through group membership updates rather than configuration rewrites.

This model enables scalable zero-touch provisioning, predictable security enforcement, and controlled exception handling across the full device lifecycle.
