# Okta + Salesforce SAML SSO IAM Lab

## Project Status

**Status:** Completed  
**Environment:** Okta Integrator / Developer Account + Salesforce Developer Edition  
**Primary Tools:** Okta, Salesforce, SAML 2.0, Okta Verify MFA, Salesforce SAML Validator  
**Project Type:** IAM / SSO / SaaS Application Onboarding / Identity Federation Lab  

---

## Table of Contents

- [Project Overview](#project-overview)
- [Business Scenario](#business-scenario)
- [Lab Objectives](#lab-objectives)
- [Tools and Technologies](#tools-and-technologies)
- [Architecture](#architecture)
- [Workshop Alignment](#workshop-alignment)
- [IAM Concepts Demonstrated](#iam-concepts-demonstrated)
- [Lab Modules](#lab-modules)
  - [Module 1: Okta and Salesforce Environment Setup](#module-1-okta-and-salesforce-environment-setup)
  - [Module 2: Okta User Creation](#module-2-okta-user-creation)
  - [Module 3: Okta Group Creation](#module-3-okta-group-creation)
  - [Module 4: MFA and Authentication Policy Review](#module-4-mfa-and-authentication-policy-review)
  - [Module 5: Salesforce SAML SSO Configuration](#module-5-salesforce-saml-sso-configuration)
  - [Module 6: Okta Salesforce Application Configuration](#module-6-okta-salesforce-application-configuration)
  - [Module 7: Group-Based Application Assignment](#module-7-group-based-application-assignment)
  - [Module 8: SSO Testing and Troubleshooting](#module-8-sso-testing-and-troubleshooting)
  - [Module 9: SAML Validation and Logs](#module-9-saml-validation-and-logs)
- [Troubleshooting Summary](#troubleshooting-summary)
- [Screenshots and Evidence](#screenshots-and-evidence)
- [Security and Business Value](#security-and-business-value)
- [Skills Demonstrated](#skills-demonstrated)
- [Challenges and Lessons Learned](#challenges-and-lessons-learned)
- [Final Outcome](#final-outcome)
- [Resume Bullet](#resume-bullet)
- [Future Improvements](#future-improvements)
- [Disclaimer](#disclaimer)

---

## Project Overview

This project simulates a real-world Identity and Access Management SaaS application onboarding process using **Okta** as the Identity Provider and **Salesforce Developer Edition** as the Service Provider.

The goal of this lab was to configure centralized authentication, create users and groups in Okta, assign Salesforce access through group-based application assignment, configure SAML-based Single Sign-On, test login behavior, validate the SAML response, troubleshoot user mapping issues, and review authentication-related logs.

This lab demonstrates practical IAM concepts used in enterprise environments, including **Single Sign-On**, **SAML 2.0**, **Identity Provider and Service Provider integration**, **MFA verification**, **RBAC-style group assignment**, **SaaS application onboarding**, and **SSO troubleshooting**.

---

## Business Scenario

Acme Corp wants to centralize authentication for Salesforce through Okta. Instead of users logging into Salesforce directly with separate credentials, users should authenticate through Okta and access Salesforce using SAML-based Single Sign-On.

As the IAM engineer, I configured Okta as the Identity Provider and Salesforce as the Service Provider. I created users and groups in Okta, reviewed MFA policy settings, assigned Salesforce access through group membership, configured SAML SSO, tested the login flow, validated the SAML response, and resolved a user mapping issue that prevented Salesforce from matching the SAML Subject to the correct Salesforce user.

---

## Lab Objectives

The main objectives of this lab were:

- Create test users in Okta
- Create groups in Okta
- Assign users to groups
- Review where MFA and authentication policies are configured in Okta
- Add Salesforce as an application integration in Okta
- Configure Salesforce as a SAML Service Provider
- Configure Okta as the SAML Identity Provider
- Assign Salesforce access through an Okta group
- Test IdP-initiated SSO from Okta to Salesforce
- Validate the SAML response using Salesforce SAML Validator
- Troubleshoot SAML Subject and username mapping issues
- Review logs for troubleshooting and audit visibility
- Document the full SaaS application onboarding workflow

---

## Tools and Technologies

| Tool / Technology | Purpose |
|---|---|
| Okta Integrator / Developer Account | Identity Provider, user management, group management, app assignment, and SSO configuration |
| Salesforce Developer Edition | SaaS application and SAML Service Provider |
| SAML 2.0 | Federation protocol used for Single Sign-On |
| Okta Verify | MFA method used during authentication |
| Okta Authentication Policies | MFA and sign-on policy review |
| Okta App Catalog | Used to add the Salesforce application integration |
| Salesforce Single Sign-On Settings | Used to enable and configure SAML SSO |
| Salesforce SAML Validator | Used to validate and troubleshoot the SAML response |
| Salesforce User Management | Used to create and validate Salesforce users |
| Browser-Based SSO Testing | Used to test IdP-initiated login flow |
| Okta System Log | Used for authentication and SSO event review |
| Salesforce Login History | Used for Salesforce-side login review |

---

## Architecture

```text
Okta User
  |
  | 1. User signs into Okta
  v
Okta Identity Provider
  |
  | 2. User is assigned to an Okta group
  v
Okta Group
  |
  | 3. Group is assigned to Salesforce application
  v
Salesforce Application in Okta
  |
  | 4. Okta sends SAML assertion
  v
Salesforce Service Provider
  |
  | 5. Salesforce validates SAML response and maps user
  v
Salesforce Access Granted
```

---

## Workshop Alignment

This lab follows the Zero to Sec **IAM Workshop #1 – Intro to Identity & Access Management** workflow.

| Workshop Area | Lab Implementation |
|---|---|
| Creating users in Okta | Created test users in Okta Directory |
| Creating groups in Okta | Created department-style groups such as HR and Marketing |
| Reviewing MFA/authentication policies | Reviewed Okta Verify and authentication policy settings |
| Configuring Salesforce SSO using SAML | Added Salesforce from the Okta App Catalog and configured SAML 2.0 |
| Assigning an application to a group | Assigned Salesforce access through an Okta group |
| Testing and troubleshooting SSO | Tested Okta-to-Salesforce login and resolved user mapping issue |
| Reviewing logs | Reviewed Okta/Salesforce logs for troubleshooting and audit visibility |

---

## IAM Concepts Demonstrated

- Identity Provider and Service Provider relationship
- SAML 2.0 authentication flow
- SaaS application onboarding
- IdP-initiated SSO
- User provisioning
- Group-based application assignment
- RBAC-style access control
- MFA authentication review
- Username-based SAML Subject mapping
- SAML response validation
- Access troubleshooting
- Authentication log review
- SaaS identity lifecycle management

---

# Lab Modules

---

## Module 1: Okta and Salesforce Environment Setup

### Objective

Prepare the Okta and Salesforce developer environments for the IAM SSO lab.

### Tasks

- [x] Created Okta Integrator / Developer account
- [x] Enrolled in Okta Verify
- [x] Logged into the Okta Admin dashboard
- [x] Created Salesforce Developer Edition account
- [x] Logged into Salesforce setup
- [x] Identified Salesforce Users and Single Sign-On Settings sections

### Implementation Details

Okta was used as the Identity Provider and Salesforce Developer Edition was used as the SaaS Service Provider. Both platforms were opened in separate browser tabs to support the SAML configuration workflow.

## Architecture Diagram

![Okta-Sales force IAM Lab Architecture](https://raw.githubusercontent.com/zaquaycage0/zaquaycage0/refs/heads/main/Architecture%20Diagram%20okta.png)

**Figure 1:** Okta-to-Salesforce SAML SSO architecture showing Okta as the Identity Provider, Salesforce as the Service Provider, and SAML authentication flow between both systems.


### What I Learned

This step showed how IAM administrators prepare both the Identity Provider and Service Provider before configuring an SSO integration.

---

## Module 2: Okta User Creation

### Objective

Create test users in Okta to simulate employee identities.

### Tasks

- [x] Navigated to **Directory → People**
- [x] Created first test user
- [x] Created second test user
- [x] Set passwords manually for testing
- [x] Activated the users
- [x] Confirmed both users appeared in Okta Directory

### Users Created

| User | Purpose | Status |
|---|---|---|
| Test User 1 | HR-style user for group assignment testing | Active |
| Test User 2 | Marketing-style user for Salesforce access testing | Active |

### Creating a User

![Okta-Sales force User created](https://raw.githubusercontent.com/zaquaycage0/zaquaycage0/refs/heads/main/Screenshot%202026-06-08%20185959.png)

### What I Learned

This step demonstrated basic identity creation in Okta and showed how users are managed from the Okta Directory.

---

## Module 3: Okta Group Creation

### Objective

Create Okta groups and assign users to those groups to demonstrate group-based access control.

### Tasks

- [x] Navigated to **Directory → Groups**
- [x] Created an HR group
- [x] Created a Marketing group
- [x] Assigned one user to the HR group
- [x] Assigned one user to the Marketing group
- [x] Confirmed group membership

### Groups Created

| Group | Purpose | Assigned User |
|---|---|---|
| HR | Department-style group for access control testing | Test User 1 |
| Marketing | Department-style group for Salesforce application access testing | Test User 2 |

### Access Control Concept

Instead of assigning applications directly to each user, access can be assigned to a group. When a user is added to the group, the user inherits access to the applications assigned to that group.

### Groups Created

![Okta-Sales force IAM Groups](https://raw.githubusercontent.com/zaquaycage0/zaquaycage0/refs/heads/main/Screenshot%202026-06-08%20190107.png)

### What I Learned

This step demonstrated how groups support RBAC-style access management by allowing administrators to grant or remove application access through group membership.

---

## Module 4: MFA and Authentication Policy Review

### Objective

Review where MFA and authentication policies are configured in Okta.

### Tasks

- [x] Navigated to **Security → Authentication Policies**
- [x] Reviewed the Okta Dashboard policy
- [x] Identified where MFA requirements can be configured
- [x] Reviewed how policies can be applied per application
- [x] Confirmed Okta Verify was used during authentication

### Key Concept

Okta authentication policies control how users authenticate to Okta and applications. Policies can be configured to require factors such as password, Okta Verify, phishing-resistant authentication, or other MFA methods depending on the application and organizational requirements.

###  Authentication Policies

![Okta-Sales force IAM Lab  Authentication Policies](https://raw.githubusercontent.com/zaquaycage0/zaquaycage0/refs/heads/main/Screenshot%202026-06-08%20195943.png)

### What I Learned

This step showed where MFA enforcement is managed in Okta and how authentication policies help secure access to the Okta dashboard and connected applications.

---

## Module 5: Salesforce SAML SSO Configuration

### Objective

Enable SAML Single Sign-On in Salesforce so Salesforce can accept SAML assertions from Okta.

### Tasks

- [x] Opened Salesforce Setup
- [x] Navigated to **Settings → Identity → Single Sign-On Settings**
- [x] Enabled SAML
- [x] Created new SAML Single Sign-On settings
- [x] Configured Salesforce SAML values from Okta setup instructions
- [x] Uploaded the Okta Identity Provider certificate
- [x] Saved the Salesforce SSO configuration
- [x] Copied the Salesforce Login URL for Okta configuration

### Salesforce SSO Settings

| Setting | Value |
|---|---|
| SAML Version | 2.0 |
| Identity Provider | Okta |
| Entity ID | `https://saml.salesforce.com` |
| SAML Identity Type | Username |
| SAML Identity Location | Subject |
| Service Provider Initiated Request Binding | HTTP POST |
| Assertion Decryption | Not Encrypted |
| User Provisioning | Not Enabled |

### Salesforce SAML SSO

![Okta-Sales force IAM Lab Salesforce SAML SSO](https://raw.githubusercontent.com/zaquaycage0/zaquaycage0/refs/heads/main/Screenshot%202026-06-08%20200909.png)

### What I Learned

This step demonstrated how Salesforce is configured as a SAML Service Provider and how it uses Identity Provider details from Okta to establish trust.

---

## Module 6: Okta Salesforce Application Configuration

### Objective

Add Salesforce as an application integration in Okta and configure SAML 2.0 as the sign-on method.

### Tasks

- [x] Navigated to **Applications → Applications**
- [x] Selected **Browse App Catalog**
- [x] Added Salesforce from the Okta App Catalog
- [x] Set the instance type to sandbox/test environment
- [x] Selected **SAML 2.0** as the sign-on method
- [x] Opened Okta setup instructions
- [x] Used Okta instructions to configure Salesforce SSO settings
- [x] Added Salesforce Login URL back into the Okta app configuration

### Configuration Summary

| Component | Configuration |
|---|---|
| Identity Provider | Okta |
| Service Provider | Salesforce |
| Application Source | Okta App Catalog |
| Sign-On Method | SAML 2.0 |
| Environment Type | Sandbox / Test |
| MFA Method | Okta Verify |

### Okta Salesforce App Configuration

![Okta-Sales force IAM Lab Salesforce SAML SSO](https://raw.githubusercontent.com/zaquaycage0/zaquaycage0/refs/heads/main/Screenshot%202026-06-08%20202245.png)

### What I Learned

This step demonstrated how IAM administrators onboard a SaaS application into Okta and configure SAML-based trust between the Identity Provider and Service Provider.

---

## Module 7: Group-Based Application Assignment

### Objective

Assign Salesforce access through an Okta group instead of assigning the application directly to each user.

### Tasks

- [x] Opened the Salesforce application in Okta
- [x] Assigned the Salesforce application to a group
- [x] Confirmed the assigned group contained the intended test user
- [x] Verified that the user inherited Salesforce application access
- [x] Tested how group membership impacts application visibility

### Application Assignment Matrix

| Okta Group | Application | Access Result |
|---|---|---|
| Marketing | Salesforce | User receives Salesforce app access |
| HR | Salesforce | Not assigned unless intentionally added |

### Access Flow

```text
User
  ↓
Okta Group Membership
  ↓
Salesforce Application Assignment
  ↓
Salesforce App Appears on Okta Dashboard
```

### Salesforce App Assigned to Group

![Okta-Sales force IAM Lab Salesforce App Assigned to Group](https://raw.githubusercontent.com/zaquaycage0/zaquaycage0/refs/heads/main/Screenshot%202026-06-08%20201651.png)


### What I Learned

This step demonstrated why group-based access assignment is more scalable than assigning application access directly to individual users.

---

## Module 8: SSO Testing and Troubleshooting

### Objective

Test IdP-initiated SSO from Okta into Salesforce and troubleshoot login issues.

### Tasks

- [x] Opened an incognito browser window
- [x] Logged into Okta as the assigned test user
- [x] Verified Salesforce appeared on the Okta dashboard
- [x] Clicked the Salesforce application tile
- [x] Tested the SAML SSO flow
- [x] Reviewed error behavior when SSO did not work
- [x] Investigated user mapping between Okta and Salesforce

### Initial Issue

The initial login attempt failed because Salesforce could not map the incoming SAML Subject to a Salesforce user.

Example error:

```text
Unable to map the subject to a Salesforce user
```

### Root Cause

Salesforce was configured to use **Username** as the SAML Identity Type and **Subject** as the SAML Identity Location. Okta was sending a SAML Subject value that did not exactly match the Salesforce Username.

| Attribute | Value |
|---|---|
| Okta Username | `JaDoe@example.com` |
| SAML Subject Sent by Okta | `JaDoe@example.com` |
| Salesforce Username | `jadoe@example.com.oktalab2026` |
| Salesforce SAML Identity Type | Username |
| Salesforce SAML Identity Location | Subject |

### Resolution

The Okta Salesforce application username was updated to match the exact Salesforce Username.

| Field | Updated Value |
|---|---|
| Okta User | `JaDoe@example.com` |
| Okta Salesforce App Username | `jadoe@example.com.oktalab2026` |
| Salesforce Username | `jadoe@example.com.oktalab2026` |

After the username mapping was corrected, Salesforce was able to map the SAML Subject to the correct user.

### SSO Error 

![Okta-Sales force IAM Lab SSO Error](https://raw.githubusercontent.com/zaquaycage0/zaquaycage0/refs/heads/main/Screenshot%202026-06-08%20190519.png)

### Corrected Username Mapping

![Okta-Sales force IAM Lab Corrected](https://raw.githubusercontent.com/zaquaycage0/zaquaycage0/refs/heads/main/Screenshot%202026-06-12%20200018.png)

### What I Learned

This step demonstrated that SAML SSO can fail even when the trust configuration is mostly correct. User mapping is a critical part of SAML troubleshooting.

---

## Module 9: SAML Validation and Logs

### Objective

Validate the SAML response and review logs for troubleshooting and audit visibility.

### Tasks

- [x] Used Salesforce SAML Validator
- [x] Reviewed SAML Subject
- [x] Confirmed issuer, audience, recipient, status, and signature validation
- [x] Confirmed MFA-related authentication context
- [x] Reviewed Okta logs for authentication and app access activity
- [x] Reviewed Salesforce login history where available

### SAML Validation Results

| Validation Check | Result |
|---|---|
| SAML Version | 2.0 |
| Issuer Match | OK |
| Audience Match | OK |
| Recipient | OK |
| Status | OK |
| Signature Validation | OK |
| Response Signed | True |
| Correct Certificate Supplied | True |
| Authentication Statement | OK |
| Conditions Statement | OK |
| Timestamp Validation | OK |

### MFA Authentication Context

The Salesforce SAML Validator showed MFA-related authentication methods:

```text
AMR Strong: mfa, okta_verify
AMR Weak: phr, pwd
ACR Weak: PasswordProtectedTransport
```

This confirmed that Okta Verify MFA was included in the authentication context.

### Salesforce SAML Validator Results

![Okta-Sales force IAM Validator Results](https://raw.githubusercontent.com/zaquaycage0/zaquaycage0/refs/heads/main/Screenshot%202026-06-12%20195504.png)

### What I Learned

This step demonstrated how logs and SAML validation tools help identify whether an issue is caused by trust configuration, authentication, or user identity mapping.

---

## Troubleshooting Summary

| Issue | Root Cause | Resolution |
|---|---|---|
| Salesforce could not map SAML Subject to a user | Okta sent a SAML Subject that did not match the Salesforce Username | Updated the Okta Salesforce application username to match the Salesforce Username |
| SAML validation passed but login failed | Technical trust settings were valid, but user mapping failed | Compared SAML Subject against Salesforce Username |
| User could not access Salesforce app | User/group assignment needed to be verified | Confirmed app assignment through Okta group membership |
| Authentication issue required review | Login flow needed troubleshooting | Reviewed Salesforce SAML Validator and Okta logs |

---

## Screenshots and Evidence

Recommended screenshots for this project:

| Screenshot | Description | Status |
|---|---|---|
| `module-1-okta-salesforce-setup.png` | Okta and Salesforce environments open | Not Added |
| `module-2-okta-users-created.png` | Okta test users created | Not Added |
| `module-3-okta-groups-created.png` | Okta groups created | Not Added |
| `module-3-okta-group-membership.png` | Users assigned to Okta groups | Not Added |
| `module-4-okta-authentication-policies.png` | Okta authentication policy section | Not Added |
| `module-5-salesforce-saml-sso-settings.png` | Salesforce Single Sign-On Settings | Not Added |
| `module-6-okta-salesforce-app-configuration.png` | Okta Salesforce app configuration | Not Added |
| `module-7-salesforce-group-assignment.png` | Salesforce app assigned to Okta group | Not Added |
| `module-8-sso-error.png` | SAML login/user mapping error | Not Added |
| `module-8-corrected-username-mapping.png` | Corrected Okta application username mapping | Not Added |
| `module-9-saml-validator-results.png` | Salesforce SAML Validator results | Not Added |
| `module-9-okta-system-log.png` | Okta System Log showing authentication/app event | Not Added |
| `module-9-salesforce-login-history.png` | Salesforce login history showing SSO event | Optional |

---

## Security and Business Value

This lab demonstrates how organizations centralize SaaS authentication using an Identity Provider such as Okta.

Instead of users managing separate Salesforce credentials, authentication is controlled through Okta. This allows IAM and security teams to enforce MFA, manage access through groups, reduce manual access assignment, and review authentication activity through logs.

Business value demonstrated:

- Centralized authentication for SaaS applications
- Reduced password management risk
- MFA verification through Okta Verify
- Group-based access assignment
- Scalable application access management
- Improved troubleshooting through logs
- Practical SAML SSO configuration experience
- Better support for joiner, mover, and leaver access workflows

---

## Skills Demonstrated

- Okta administration
- Salesforce SSO configuration
- SAML 2.0 authentication
- Identity Provider and Service Provider integration
- SaaS application onboarding
- Okta user management
- Okta group management
- Group-based application assignment
- MFA policy review
- Username-based identity mapping
- SAML response validation
- SSO troubleshooting
- Log review
- IAM documentation

---

## Challenges and Lessons Learned

### Challenges

- Salesforce usernames must be globally unique, which caused the Salesforce Username to differ from the Okta username.
- The SAML response passed several validation checks, but login still failed because the SAML Subject did not map to an active Salesforce user.
- SSO configuration required moving between Okta setup instructions and Salesforce SSO settings.
- Application assignment had to be validated through group membership.

### Lessons Learned

- SAML troubleshooting requires validating both the technical SAML response and the user identity mapping configuration.
- A SAML assertion can be valid but still fail if the Subject does not match the Service Provider’s expected user attribute.
- Group-based application assignment is more scalable than direct user assignment.
- MFA and authentication policies are important parts of SaaS access security.
- Logs are critical for troubleshooting failed authentication and SSO issues.
- Clear documentation of Identity Provider and Service Provider settings makes troubleshooting faster.

---

## Final Outcome

By completing this lab, I configured and documented an Okta-to-Salesforce SAML SSO integration that included:

- Okta as the Identity Provider
- Salesforce as the Service Provider
- Okta user creation
- Okta group creation
- Group-based Salesforce app assignment
- Okta Verify MFA review
- SAML 2.0-based Single Sign-On
- Salesforce SAML SSO configuration
- Salesforce SAML Validator testing
- Username-based SAML Subject mapping
- SSO troubleshooting and resolution
- Okta log review
- Successful IdP-initiated SSO into Salesforce

---

## Resume Bullet

> Configured and documented an Okta-to-Salesforce SAML SSO lab simulating enterprise SaaS application onboarding, including Okta user and group management, group-based application assignment, SAML 2.0 configuration, Okta Verify MFA validation, Salesforce SSO settings, SAML response validation, log review, and troubleshooting of username-based identity mapping errors.

---

## Future Improvements

Future improvements for this lab may include:

- Add SP-initiated SSO testing from Salesforce
- Add Okta group-based access testing with multiple departments
- Add Salesforce profile or permission set validation
- Add Okta Sign-On Policy testing for Salesforce access
- Add Okta System Log screenshots and event analysis
- Add Salesforce Login History review
- Compare username-based mapping vs Federation ID mapping
- Add a second SaaS application to demonstrate repeatable application onboarding

---

## Disclaimer

This lab was created in a controlled developer environment for educational and portfolio purposes. The company, users, and scenarios are fictional and are designed to simulate real-world IAM, SSO, and SaaS application onboarding workflows.
