# Security Policy

Beebeeb is an end-to-end encrypted storage platform. Security is not a feature --- it is the product. We appreciate responsible disclosure of vulnerabilities and will work with you to resolve them promptly.

## Reporting a vulnerability

**Email:** [security@beebeeb.io](mailto:security@beebeeb.io)

Please include:

- A clear description of the vulnerability
- Steps to reproduce, including any tools or scripts used
- The affected repository and version (or commit hash)
- Your assessment of severity and potential impact
- Any suggested mitigation, if you have one

**Do not** open a public GitHub issue for security vulnerabilities. Use the email address above.

## Response timeline

| Step | Timeframe |
|---|---|
| Acknowledgment of your report | Within 48 hours |
| Initial assessment and severity classification | Within 5 business days |
| Status update with remediation plan | Within 10 business days |
| Fix deployed (critical/high severity) | As soon as possible, target 30 days |

We will keep you informed throughout the process and notify you when the fix is released.

## Scope

The following are in scope for security reports:

- **core** --- Cryptographic primitives, key derivation, encryption/decryption, key wrapping
- **server** --- API authentication, authorization, session management, data handling
- **web** --- Client-side encryption, WASM crypto module, authentication flows
- **cli** --- Credential storage, key material handling, authentication
- **mobile** --- Native crypto bindings, secure storage, authentication
- **desktop** --- Sync daemon security, credential management, virtual drive access control
- **Infrastructure** --- TLS configuration, server hardening, network security

### Out of scope

- Denial of service attacks
- Social engineering or phishing
- Issues in third-party dependencies (report these upstream; let us know so we can update)
- Issues requiring physical access to a user's device
- Automated scanner output without a demonstrated exploit

## Recognition

We believe in giving credit where it is due. With your permission, we will acknowledge your contribution in our release notes and on a future security acknowledgments page. We do not currently offer monetary bounties, but we are open to discussing this as the project grows.

## Disclosure policy

We follow coordinated disclosure. We ask that you:

1. Give us reasonable time to investigate and fix the issue before any public disclosure.
2. Make a good-faith effort to avoid accessing or modifying other users' data.
3. Do not exploit the vulnerability beyond what is necessary to demonstrate it.

We commit to not pursuing legal action against researchers who follow this policy.

## Supported versions

We support the latest released version of each repository. Security fixes are not backported to older versions.

## Contact

- **Security reports:** [security@beebeeb.io](mailto:security@beebeeb.io)
- **General inquiries:** [hello@beebeeb.io](mailto:hello@beebeeb.io)
- **Operator:** Initlabs B.V. (KvK 95157565), Wijchen, Netherlands
