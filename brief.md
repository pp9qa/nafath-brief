Version: NAFATH-V1
Track: AI

## Overview

A national single sign-on service connects identity, security and privacy across the website, mobile app and government services. Software must separate proof of a citizen's identity from permission to access an API. AI can flag unusual logins, but its mistakes need testing, monitoring and human review. Android permissions limit the mobile app's access to protected features and information. DNS over HTTPS protects DNS exchanges with the chosen resolver, while phishing-resistant authentication helps protect accounts from fake login pages. Data governance determines which legal duties apply and how personal information is handled. These decisions need joint review because a weakness in one area can affect the whole login journey. My main focus is managing the risks of AI-based suspicious-login detection using the NIST AI Risk Management Framework.

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

DNS over HTTPS (DoH) sends DNS questions and answers through an encrypted HTTPS connection between a device and its chosen resolver. This protects those messages from eavesdropping and tampering along that connection. It does not make browsing anonymous: the resolver can still associate queries with the client's IP address, and traffic analysis remains possible. DoH also does not replace DNSSEC, which checks DNS data authenticity; a dishonest resolver can still return incorrect answers.

Resource: RFC 8484 - DNS Queries over HTTPS (DoH) - https://www.rfc-editor.org/rfc/rfc8484.html

## Cybersecurity

Phishing-resistant authentication binds cryptographic proof to the genuine service or secure channel, preventing fake sites from collecting usable login responses. FIDO2/WebAuthn credentials with PIN or biometric verification provide phishing-resistant MFA. PIV smart cards using client-authenticated TLS also qualify when a PIN provides a verified second factor. Passwords plus SMS codes, authenticator-app codes or ordinary approval prompts do not qualify. The login service should choose methods that resist phishing without relying on citizens spotting scams.

Resource: NIST SP 800-63B-4 - Authentication and Authenticator Management - https://pages.nist.gov/800-63-4/sp800-63b.html

## Data

Article 3(b) excludes state bodies' processing for legally prescribed functions. Where the law applies, obtain explicit consent unless an Article 10bis exception applies; explain processing purposes, protect confidentiality, assess risks, and appoint a data protection officer. Support rights to copies, correction and deletion under the prescribed rules. Notify the Ministry and affected people of qualifying breaches. Delete stored data immediately when its purpose ends, except where an existing dispute or legal obligation requires retention.

Resource: Royal Decree 6/2022 Issuing the Personal Data Protection Law (Consolidated) - https://decree.om/2022/l20220006/

## Misconception in My Track

A common misconception is that a successful accuracy test makes a suspicious-login model safe to deploy permanently. Section 5.3, Measure, of the NIST AI RMF Core calls for testing before deployment and during operation. Accuracy alone cannot establish whether errors unfairly affect some citizens or expose private information. For this service, I would assess these risks before launch, monitor performance afterwards, and keep human review available when automated flags are disputed.

## Open Question

What false-alarm rate would be acceptable for this login service, and how should the authority route disputed AI flags to human review without delaying legitimate citizens unnecessarily?
