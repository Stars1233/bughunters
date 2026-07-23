The Google Cloud Vulnerability Reward Program (VRP) greatly values the
contributions of security researchers in helping us secure Google Cloud. To
improve transparency and guide your research efforts, we have analyzed
historical reports submitted to the Cloud VRP that were closed as invalid (e.g.
Working as Intended (WAI), Infeasible, or Obsolete).

Using an AI-powered tool, we processed and clustered these past Cloud VRP
reports to identify recurring patterns and the most common reasons for rejection
across various Google Cloud products. This article presents these insights to
help researchers understand what types of findings, while sometimes appearing to
be security vulnerabilities, do not meet the criteria for a reward under the
Google Cloud VRP. By sharing this information, our goal is to help you avoid
spending time on issues we don't consider vulnerabilities and enable both
researchers and our triage teams to focus on truly impactful security flaws.

Please remember that the
[official Google Cloud VRP rules](/about/rules/google-friends/cloud-vulnerability-reward-program-rules)
are always the authoritative source for program scope and rewards.

We plan to update this document periodically. Last update: 2026-04-20.

## AppSheet

*   Vulnerabilities identified in customer-owned or customer-configured AppSheet
    applications are considered out of scope. Under the shared responsibility
    model, customers are responsible for the security of the applications they
    build, including managing access keys, API configurations, and data sharing
    settings. (7 reports closed)
*   The exposure of certain information in API responses, such as an application
    owner's email address or API keys for client-side functionality, is
    considered intended behavior. This information is either necessary for the
    application's features (like displaying terms of service) or is not
    considered sensitive enough to constitute a security vulnerability. (3
    reports closed)
*   The ability for users to see who else is currently accessing a shared
    resource is an intended collaborative feature, similar to other Google
    products, and is not a security vulnerability. (2 reports closed)
*   The ability for users, including those with low-privilege roles, to create
    resources (such as databases or applications) within their own accounts is
    intended functionality and correctly counts against their own resource
    quotas. (2 reports closed)

## Apigee API Platform

*   Reports of exposed credentials were found to be invalid because the
    associated accounts were disabled or inactive, rendering the keys
    non-functional and posing no security risk. (2 reports closed)
*   Reports were considered invalid because the affected asset was a third-party
    site or resource (such as a community forum or a resource hosted on another
    cloud provider) not owned or operated by Google, making it out of scope. (3
    reports closed)

## Artifact Registry

*   Reports of theoretical supply chain risks, such as dangling references to
    unclaimed container registry projects in documentation or open-source
    repositories, do not meet the threshold for a security vulnerability. These
    scenarios are considered hypothetical and do not represent a direct,
    exploitable flaw in the product itself. (4 reports closed)

## BigQuery

*   Reports of unauthorized actions were found to be invalid because the
    behavior observed was consistent with the permissions granted by the user's
    existing high-level roles, such as 'Editor' or 'Viewer'. Actions like
    managing resources or viewing job metadata within a project are intended
    capabilities of these roles and do not represent a privilege escalation. (5
    reports closed)
*   Claims of Insecure Direct Object Reference (IDOR) were not reproducible or
    described intended behavior. The API endpoints were found to correctly
    enforce authorization checks, and in some cases, the behavior (such as
    creating a 'Personal' query in another project's context) was a documented
    feature. (4 reports closed)

## Cloud Build

*   The ability to execute user-provided code, access the instance metadata
    server, or use the permissions of the attached service account within a
    build environment is intended functionality. Cloud Build is designed to run
    arbitrary commands as a core feature, and the security model assumes that
    users with the ability to define build steps are authorized to execute code
    in that context. (5 reports closed)

## Cloud Dataproc

*   The service not verifying that staging and temporary Cloud Storage buckets
    reside within the same project as the cluster is a known design choice. This
    allows an attacker with knowledge of the predictable bucket naming
    convention to potentially intercept data if they can pre-create those
    buckets. (2 reports closed)
*   The use of hashing algorithms (such as SHA-1) that are flagged by security
    scanners is considered a known configuration choice rather than an
    exploitable vulnerability, unless a practical and reproducible exploit is
    demonstrated. (2 reports closed)

## Cloud Identity and Access Management

*   Access tokens remaining valid for their full, short-lived duration even
    after the underlying IAM policy that authorized their creation has been
    revoked is intended behavior. IAM policies control the minting of new
    tokens, not the lifecycle of already-issued bearer tokens. (2 reports
    closed)

## Cloud Run

*   Claims of a sandbox escape were considered invalid because the container
    environment in Cloud Run is not treated as a security boundary. (2 reports
    closed)
*   Vulnerabilities found in customer-deployed applications, such as open
    redirects or Server-Side Request Forgery (SSRF), are considered out of
    scope. Under the shared responsibility model, customers are responsible for
    the security of their own code and configurations. (2 reports closed)

## Cloud SDK - Client Libraries

*   Reports identifying a vulnerable third-party dependency are considered
    invalid without a functional proof-of-concept demonstrating that the
    vulnerability is exploitable within the context of the Google Cloud product.
    (4 reports closed)
*   The libraries are client-side tools, and the responsibility for validating
    user-provided input (like bucket names) or managing local system resources
    lies with the developer integrating the library, not the library itself. (2
    reports closed)

## Cloud SDK - Google Cloud CLI

*   Attack scenarios that require the attacker to already have local access to
    the victim's machine or the ability to perform a man-in-the-middle (MITM)
    attack are considered out of scope. Such prerequisites mean the system is
    already compromised, rendering the specific vulnerability in the tool
    redundant. (4 reports closed)
*   The use of installation methods like `curl | bash` or downloading components
    without explicit checksums is a standard, documented process for the tool.
    These reports are considered hardening advice rather than actionable
    security vulnerabilities. (3 reports closed)

## Cloud Shell

*   Claims of a container escape are considered invalid because the Cloud Shell
    environment runs in a dedicated, single-tenant virtual machine for each
    user. The container is not intended to be a security boundary, and gaining
    access to the underlying VM does not impact other users or Google's
    infrastructure. (14 reports closed)
*   The execution of third-party code or scripts within a Cloud Shell session is
    an intended capability of the service. The security model assumes that users
    are responsible for the code they choose to run in their own isolated
    environment. (2 reports closed)
*   Running resource-intensive software, such as cryptocurrency miners, is
    treated as a policy or abuse violation rather than a technical security
    vulnerability. (2 reports closed)

## Cloud Storage

*   Stored Cross-Site Scripting (XSS) vulnerabilities resulting from uploading
    malicious files (e.g., SVG) are considered invalid. The execution occurs on
    sandboxed domains (like *.storage.googleapis.com) that are intentionally
    isolated from sensitive user data and authentication cookies by the
    Same-Origin Policy, which is an intended security control. (7 reports
    closed)
*   Publicly accessible buckets containing sensitive data were determined to be
    misconfigurations by the Google Cloud customer who owns the bucket. Under
    the shared responsibility model, customers are responsible for their own
    data security and access control configurations, making these issues out of
    scope. (5 reports closed)
*   Claims of bypassing access controls were found to be based on a
    misunderstanding of how Cloud Storage security features work. The observed
    behaviors were consistent with the documented interaction between IAM
    policies, bucket-level permissions, signed URLs, and public access settings.
    (5 reports closed)
*   Buckets being configured for public access is not a vulnerability when it is
    intentional, such as for distributing public software artifacts, open-source
    data, or website assets. (5 reports closed)
*   The ability to list objects in a public bucket without authentication is
    intended functionality. Public buckets are designed to allow unauthenticated
    access to their contents if the bucket's IAM policy or ACLs are configured
    to permit it. (3 reports closed)
*   The ability to infer a bucket's existence or location by probing public
    endpoints is intended behavior and is not considered a security risk, as
    bucket names and locations are not treated as secret information. (2 reports
    closed)

## Cloud Workstations

*   Accessing service account keys or instance metadata from within a
    workstation environment is intended behavior. These single-user, sandboxed
    workspaces are designed to provide the necessary credentials for the user to
    perform their development tasks. (3 reports closed)

## Compute Engine

*   Vulnerabilities found in third-party software (e.g., open Jenkins
    dashboards, outdated Apache, misconfigured Grafana) running on
    customer-owned virtual machine instances are out of scope. Under the shared
    responsibility model, customers are responsible for securing the
    applications they deploy. (25 reports closed)
*   Reports on vulnerabilities in low-level components like KVM or QEMU were
    considered invalid because they either did not meet the security impact
    threshold, were theoretical, or lacked a reproducible proof-of-concept
    demonstrating an exploit within the Google Cloud environment. (6 reports
    closed)
*   Accessing the instance metadata server from within a VM is intended
    behavior. A vulnerability in a user-deployed application (like SSRF) that
    allows access to the metadata server is a flaw in that application, not in
    the metadata service itself. (5 reports closed)
*   Theoretical hardware-level vulnerabilities, such as CPU side-channel
    attacks, are inherent characteristics of modern processors and do not meet
    the threshold for a VRP-qualifying software bug in the cloud platform. (2
    reports closed)
*   The persistence of an established SSH session after IAM permissions have
    been revoked is the expected and documented behavior of the SSH protocol and
    its integration with OS Login. (2 reports closed)

## Dialogflow

*   Claims of Insecure Direct Object Reference (IDOR) or unauthorized data
    access were found to be not reproducible. During testing, the API endpoints
    correctly enforced permissions and returned an empty response or an error
    when access was attempted without proper authorization. (3 reports closed)
*   The ability for a malicious application to use granted OAuth scopes to
    perform actions on a user's behalf is the intended behavior of the OAuth 2.0
    framework. The security model relies on the user making an informed decision
    when granting permissions to a third-party application. (2 reports closed)
*   The ability for users with project-level viewer roles to see IAM policy
    information, including the email addresses of other project members, is an
    intended and documented feature of the platform's access control model. (2
    reports closed)

## Firebase Platform

*   Claims of sandbox escapes or privilege escalation within Firebase Studio
    (formerly Project IDX) are considered invalid because these services provide
    users with a dedicated, single-tenant development environment. The container
    or VM is not a security boundary, and users are intended to have full
    control, including root access, over their own isolated workspace. (13
    reports closed)
*   Reports of command injection vulnerabilities were considered invalid because
    the attack scenarios required social engineering or a pre-compromised
    environment. An attacker would need to trick a developer into taking an
    explicit action, such as running a command on a maliciously named directory
    or entering a payload into their own terminal. (5 reports closed)
*   The persistence of user access for a short period after permissions have
    been revoked is expected behavior due to eventual consistency and
    propagation delays in distributed IAM systems. (5 reports closed)
*   Publicly accessible data in Firebase services (like Realtime Database) or
    associated Cloud Storage buckets is the result of customer misconfiguration.
    Customers are responsible for setting appropriate security rules and access
    policies for their own resources. (5 reports closed)
*   Firebase API keys are designed to be public identifiers for a project and
    are not used for authorization. Reports demonstrating that these keys can be
    used to identify a project or perform public operations are describing
    intended behavior. (4 reports closed)
*   Hardcoded GitHub OAuth credentials found in open-source tool repositories
    were intended for local development only. The associated OAuth application
    is restricted to a `localhost` redirect URI, which prevents the credentials
    from being exploited in a remote attack. (3 reports closed)
*   Reports identifying a vulnerable third-party dependency in an open-source
    project are considered invalid without a proof-of-concept demonstrating that
    the vulnerability is exploitable within the context of the Firebase product.
    (2 reports closed)
*   The security model for shared workspaces in Firebase Studio relies on trust.
    Documentation explicitly warns that shared users get full access to the VM
    and its environment, and workspaces should only be shared with trusted
    individuals. (2 reports closed)

## Gemini CLI

*   Command execution is considered intended behavior when it requires explicit
    user approval. The tool's security model relies on the user to review and
    consent to actions via confirmation prompts, the use of permissive flags
    (like `--yolo`), or by explicitly allowing command prefixes. (6 reports
    closed)
*   The tool is designed to execute user-provided scripts and commands. It is
    not responsible for the security of the script's content, and reports
    demonstrating that a user can run an insecure script (e.g., one using
    `shell=True` or `eval`) are describing intended functionality. (4 reports
    closed)
*   Claims of prompt injection from local files were considered invalid because
    the attack scenario requires the attacker to already have control over the
    victim's local environment to place the malicious file, which is a
    prerequisite that falls outside the product's threat model. (2 reports
    closed)

## Google Cloud Console

*   Claims of Cross-Site Scripting (XSS) were determined to be invalid because
    the application correctly implements security controls like Content Security
    Policy (CSP), output encoding, and sanitization, which prevent the execution
    of arbitrary scripts. (7 reports closed)
*   Claims of Insecure Direct Object Reference (IDOR) or unauthorized data
    access were found to be not reproducible. The API endpoints correctly
    enforced permissions, typically returning an empty list or an authorization
    error for unauthorized requests. (5 reports closed)
*   Actions performed were consistent with the user's existing permissions and
    did not represent a bypass. The behavior observed was an intended function
    of the platform's Identity and Access Management (IAM) and resource
    management model. (3 reports closed)
*   Public API keys found in the console's client-side code are intended for
    public use. They are used to identify the calling application for quota and
    billing purposes and do not grant elevated privileges or access to sensitive
    user data. (3 reports closed)
*   Manipulating client-side UI elements using browser developer tools does not
    bypass server-side authorization checks, which are the authoritative source
    for security enforcement. (2 reports closed)
*   Open redirects are considered out of scope for the vulnerability reward
    program unless they can be chained with another vulnerability to demonstrate
    a higher security impact. (2 reports closed)
*   Viewing certain metadata, such as other users' emails in a shared project or
    non-sensitive usage signals, is considered intended behavior for
    collaborative platforms and does not meet the threshold for a security
    vulnerability. (2 reports closed)

## Google Kubernetes Engine

*   The behavior reported is by design and documented; users are responsible for
    managing permissions and security configurations (such as migrating to
    Workload Identity on existing node pools) within their own clusters. (2
    reports closed)
*   Exposed credentials or API keys found in public repositories were
    intentionally included for public demonstration or testing purposes. The
    keys were scoped with minimal, non-sensitive permissions and posed no
    security risk. (2 reports closed)

## Google SecOps SIEM

*   Stored Cross-Site Scripting (XSS) vulnerabilities are considered invalid
    when the user-controlled content is rendered within a sandboxed domain
    (e.g., `usercontent.goog`). These domains are intentionally isolated from
    the main application's data and authentication context by the Same-Origin
    Policy, neutralizing the threat. (3 reports closed)

## Google SecOps SOAR

*   The ability for custom scripts running in the IDE to access integration
    secrets or service account tokens is an intended architectural behavior,
    allowing for powerful and flexible automation within the platform. (3
    reports closed)
*   The ability to impersonate a service account is not a vulnerability when it
    requires an explicit, privileged administrative action to grant the
    necessary 'Service Account Token Creator' role. This is a documented and
    expected configuration for enabling workload identity features. (2 reports
    closed)
*   Reports were considered invalid because the affected domain was identified
    as a dangling DNS record and was not part of Google-controlled
    infrastructure. (2 reports closed)

## Looker

*   Reports based on the output of automated security scanners, such as the
    presence of outdated software versions or missing HTTP security headers, are
    considered invalid without a functional proof-of-concept that demonstrates
    an actual, exploitable vulnerability. (5 reports closed)
*   Claims of Server-Side Request Forgery (SSRF) were considered invalid because
    the ability for an administrator to configure connections to various
    internal or external services is a core, intended feature of the product. (2
    reports closed)

## Looker Studio Free

*   The ability for users to grant consent for data sources is a standard
    feature for enabling third-party visualizations and is not an authorization
    bypass. (2 reports closed)
*   Certain API endpoints are intended to be accessible to all users, including
    those with free accounts, as they are part of the product's standard, core
    functionality (such as the CSV connector). (2 reports closed)
*   Server-Side Request Forgery (SSRF) claims were rejected because the ability
    for a data visualization tool to fetch external resources is intended
    functionality. (2 reports closed)

## N/A

*   The reported asset, such as `googlecloudcommunity.com`, was found to be a
    third-party website operated by a vendor (e.g., Khoros) and not owned or
    managed by Google, making it out of scope for the program. (6 reports
    closed)

## Vertex AI Platform

*   Attack scenarios that require a user to manually execute untrusted code or
    open a malicious file (e.g., a crafted notebook) are not considered
    platform-level vulnerabilities. The security model assumes users will not
    run code from untrusted sources without review. (2 reports closed)
*   Claims of Server-Side Request Forgery (SSRF) were found to be duplicates of
    previous reports or lacked a reproducible proof-of-concept demonstrating a
    security impact. (2 reports closed)
*   Reports of unauthorized access or action bypasses were found to be invalid,
    as the behavior was a result of the testing account having the necessary
    permissions, or the resources being tested were public and did not require
    project-specific authorization. (2 reports closed)
*   Path traversal vulnerabilities were considered invalid because the attack
    scenario required the attacker to already have privileged access to the host
    machine where the code was being executed, making the vulnerability
    redundant. (2 reports closed)
*   Accessing the instance metadata server from within a notebook or other
    workload is intended behavior, as the credentials are required for the
    environment to interact with other Google Cloud services. (2 reports closed)
