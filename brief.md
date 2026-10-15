Version: NAFATH-V1
Track: AI

## Overview

A national single sign-on service connects identity, security and privacy across the website, mobile app and government services. Software must separate proof of a citizen's identity from permission to access an API. AI can flag unusual logins, but its mistakes need testing, monitoring and human review. Android permissions limit the mobile app's access to protected features and information. DNS over HTTPS protects DNS exchanges with the chosen resolver, while phishing-resistant authentication helps protect accounts from fake login pages. Data governance determines which legal duties apply and how personal information is handled. These decisions need joint review because a weakness in one area can affect the whole login journey. The project should define responsibilities and checks before launch.

## Software

OAuth 2.0 is an authorization framework for delegated, limited access to resources, such as an app calling an API on a citizen's behalf. It does not itself standardize user identity information. OpenID Connect adds an identity layer for login, allowing the service to verify the citizen using authentication performed by an identity provider. The app requests the openid scope and receives an ID token carrying authentication information. Access tokens authorize resource access.

Resource: OpenID Connect Core 1.0 incorporating errata set 2 - https://openid.net/specs/openid-connect-core-1_0.html

## AI

Applying NIST's AI Risk Management Framework through Govern, Map, Measure and Manage, the authority should assign accountability, map potential harms and test the login detector before deployment. Risks include missed attacks, false alarms affecting legitimate citizens, biased results, privacy loss and attacks against the model. Tests should reflect real users and operating conditions. Document limitations, provide human review and appeals, and define incident responses. Monitoring must continue after launch because performance and risks can change.

Resource: AI RMF Core - https://airc.nist.gov/airmf-resources/airmf/5-sec-core/

## Mobile

Android isolates apps in a sandbox and controls access to protected data or device features through permissions. On Android 6.0 and later, dangerous permissions require runtime approval. The login app should request permission when the citizen starts the feature needing it, after checking whether access is already granted. It should explain the reason when appropriate and check permission before each protected operation. If permission is denied or revoked, unrelated features should remain usable.

Resource: Request runtime permissions - https://developer.android.com/training/permissions/requesting

## Networking

## Cybersecurity

## Data

## Misconception in My Track

## Open Question
