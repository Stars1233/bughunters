<font color="#4285F4"><b>As of April 9, 2026, this program is in a freeze for an
indefinite amount of time and is currently not processing any new requests
(<a href="https://github.com/google/tsunami-security-scanner-plugins/issues/819">details</a>).
Existing accepted requests will continue being processed and paid
out.</b></font>

Earn rewards by patching Tsunami security scanners for vulnerability detection.

Since September 2021, we are rewarding contribution to our open source security
scanner: Tsunami. We hope this program will allow us to quickly extend the
detection capabilities of the scanner, and all the users of the scanner will
benefit from this program to uncover more vulnerabilities in their network
infrastructure.

## Qualifying contributions

### Vulnerability detectors

The Tsunami scanner has an extensible plugin system for extending its detection
capability. For a vulnerability detector contribution to be considered in-scope,
it has to satisfy the following criteria:

-   **The vulnerability should have a HIGH or CRITICAL severity rating if there
    is already a CVE ID assigned (CVSS score >= 7.0).** If there is no severity
    assigned yet, the Tsunami scanner team will perform the triage and determine
    the severity. This usually includes vulnerabilities like Remote Code
    Executions (RCEs), arbitrary file uploading, security misconfigurations that
    result in exposure of sensitive admin panels, and so on.
-   **The vulnerability should be relatively new and have already been
    patched.** The vulnerabilities should have been identified in the last 2
    years and patches for the vulnerabilities should have already been
    published.
-   **The vulnerability should have a relatively large impact radius.** The
    software affected by a vulnerability should be widely adopted by the
    industry. Or the vulnerability should be actively utilized by attackers. We
    appreciate that this information might not always be available, but you can
    find example software that we care most about in the following list. And you
    should contact us beforehand if this list doesn't include the software
    you'll be working on.
    -   Web and mail servers, e.g. Apache httpd, lightttpd, nginx, Sendmail,
        Postfix, etc.
    -   Database and database like applications, e.g. MySQL, PostgreSQL, Redis,
        Memcached, etc.
    -   Application frameworks, e.g. Django, Flask, Spring Framework, Apache
        Struts, etc.
    -   CMS platforms, e.g. WordPress, Joomla, Drupal, Magento, OpenCart, etc.
    -   CI/CD platforms, e.g. Drone, Jenkins, Travis, GoCD, Gitlab, etc.
    -   Cluster management software, e.g. Kubernetes, Docker, Apache Hadoop,
        Hashicorp Consul / Nomad, VMWare, etc.
    -   Coding notebooks, e.g. Jupyter Notebook / Lab, Apache Zeppelin,
        Polynote, etc.
    -   Control panels, e.g. phpMyAdmin, Adminer, Ajenti, etc.
    -   Configuration management tools, e.g. Ansible, SaltStack, Puppet, etc.
-   **The vulnerability should be remotely exploitable without authentication
    and user interaction.** Tsunami scanner works as a blackbox testing tool and
    reaches the scan target by either IP addresses or hostnames. No prior
    knowledge of the authentication system should be required for the detector
    to work properly.
-   **The detector should provide a reliable false-positive free detection
    report.** One philosophy of the Tsunami scanner is to always provide
    vulnerability detections with high confidence. New detectors should follow
    the same philosophy and generate high quality reports.
-   **The detector should have good unit test coverage.** Google's open source
    projects should be thoroughly tested and there is no exception for the
    Tsunami project. Unit testing makes sure the detector works using fake data.
-   **The detection capability should be easy to verify using both vulnerable
    and fixed Docker images.** Tsunami scanner verifies its detection
    capabilities using a testbed. The testbed deploys vulnerable Docker images
    to a remote Kubernetes cluster and our integration pipeline keeps scanning
    the cluster for verification. When making detector contributions, a
    vulnerable Docker image as well as its Kubernetes deployment script should
    also be included. And, if applicable, a patched/fixed instance of the same
    application should also be provided for countermeasure.

### InternetCTF: From Vulnerability Disclosure to Vulnerability Detection

Find new vulnerabilities in the secure versions of Open Source Software hosted
at [InternetCTF](https://capturetheflag.withgoogle.com/internet), and prove your
work by exfiltrating the root flag configured with each application. After
submitting a flag and reporting the vulnerability to the upstream project owner,
we will reserve 1 week for you to work on a new Tsunami plugin for this
vulnerability. If you successfully submit a Tsunami plugin within this time
window of 1 week, you will be eligible for a patch reward of up to $10k.

## Application process

### General Patch Reward Process

Since you as a participant and the Tsunami scanner team will need to work
together closely for your contributions, we'll use
[GitHub Issues on our GitHub Repository](https://github.com/google/tsunami-security-scanner-plugins/issues)
as the main collaboration channel. The following list summarizes the expected
end-to-end process:

1.  Participants first need to submit a new GitHub Issue using the `Path Reward
    Program` template. Participants should include as many details as possible
    in the request, including links to the announcement of the vulnerability,
    technical details of the exploits, and severity ratings. Tsunami scanner
    team members will evaluate the request and determine whether it is in scope
    for this reward program.
1.  If your request is in scope, you'll be notified in the Issue thread with
    instructions on how to submit the request to our internal panel using our
    [submission form](/report/tsunami).
1.  Once the request is accepted, you can start working on the implementations.
    Tsunami scanner team members will work with you closely during this phase to
    provide prompt code reviews and feedback on your work.
1.  Once the patch is done, the Tsunami scanner team will do the final
    evaluation of the quality of your patch and determine the final reward
    amount. You'll be notified by email when the reward amount is determined.

### InternetCTF Patch Reward Process

1.  Exfiltrate the root flag from securely configured applications hosted on
    [InternetCTF](https://capturetheflag.withgoogle.com/internet).
2.  Fill in the **initial stage** of the
    [InternetCTF submission form](https://docs.google.com/forms/d/e/1FAIpQLSesBR3zNpaXaZ3vgN2lc1ulclaBjH-ZBSuDS9Hsyf4T8XHT9g/viewform?usp=sf_link)
    with your root flag.
3.  Report the vulnerability to the upstream project owner.
4.  \[Optional\] Provide a security patch for this vulnerability and claim a
    reward via the
    [Patch Rewards Program](https://bughunters.google.com/open-source-security/patch-rewards).
5.  Wait for the public disclosure of the vulnerability.
6.  Once the vulnerability is publicly disclosed, update the existing form
    submission and update the **second stage** of the form with vulnerability
    details. Upon submitting the second stage of the form, we will reserve 1
    week for you to work on a new Tsunami plugin for this vulnerability.
    *   Follow the steps in the
        [General Patch Reward Process](https://bughunters.google.com/about/rules/open-source/5067456626688000/tsunami-patch-rewards-program-rules#general-patch-reward-process)
        section. Please label your GitHub issue with `internetctf` for
        visibility.
7.  Once the Tsunami plugin has been accepted, update the existing submission
    and fill in the **third stage** of the form. The Tsunami team will do the
    final evaluation of your patch and determine the final reward amount. You'll
    be notified by email when the reward amount is determined.

## Reward amounts

The reward amount usually depends on the time sensitivity and the severity of
the vulnerability, as well as the quality of the contribution. The final amount
will always be chosen at the discretion of our reward panel. The following
points outlines the usual reward amounts:

### General Tsunami Patch Reward

-   Up to **$3,133.7** for "wishlist" detectors.
-   Up to **$2,000** for exposed administration interfaces and weak credentials
    detectors.
-   Up to **$1,500** for other contributions.

#### What is a wishlist detector?

This is a detector for a vulnerability that Google cares deeply about.
We understand that this is outside of the control of the contributors but this
is generally based on internal priorities.

We will generally make it explicit that a contribution falls in that category
but on the other hand, we might request that the detector is completed in a
faster timeline (less than a week) to justify the higher payout. Sometimes we
will release a wishlist to the public – if you pick up an item from that
wishlist, you are guaranteed to fall into this category.

### InternetCTF Tsunami Patch Reward

-   Up to **$10,000** for 0-day vulnerabilities within 1-week after the
    vulnerability report made to the upstream project owner.

We also offer the option to donate the rewards to charity. Rewards unclaimed
after 12 months will be automatically donated to a charity of our choosing.

## Code of conduct

To ensure a healthy and productive relationship between participants and the
Google teams interacting with them, we have defined a
[Code of Conduct](/about/rules/other/6009584292331520/code-of-conduct-for-our-vulnerability-reward-programs)
laying out the expected behaviors from both sides.

Thank you in advance for familiarizing yourself with this code and adhering to
its provisions!

## Frequently asked questions

*Q: What if someone else also submitted the patch for the same vulnerability?*
A: You will qualify for a reward only if you were the first person to finish the
detector for the same vulnerability.

*Q: What if someone dropped their work in the middle of the process?* A: Tsunami
scanner team members will continuously sanitize all the tracking GitHub Issues
for this program. Any issue that is silent for 1 week will be marked as inactive
using the `PRP:Inactive` tag. Anyone can pick up the remaining work related to
an inactive issue. The final reward might be split between all the contributors
of the issue, based on the scale of contributions.

*Q: How will I get paid?* A: You will be paid through our established VRP
payment process. We'll ask you for your contact details after your requests are
selected for the program, and our payment team will work with you to finalize
the payment.

## Legal

We are unable to receive reports and/or issue rewards to individuals or entities
that are on sanctions lists, or who are in territories subject to sanctions
(e.g., Cuba, Iran, North Korea, Syria, Crimea, and the so-called Donetsk
People's Republic and Luhansk People's Republic). Additionally, due to
administrative difficulties, we no longer issue rewards to individuals or
entities located in Russia or Belarus.

You are responsible for any tax implications depending on your country of
residency and citizenship. There may be additional restrictions on your ability
to enter depending upon your local law.

If Google Payments is your selected payment option and you're not a US resident
for income tax purposes, you confirm that any services you provide to Google
won't be performed in the US. If you ever plan to provide services in the US,
please let us know in writing at least 90 days beforehand by emailing
STCnotices@google.com.

This is not a competition, it is an experimental and discretionary rewards
program. We reserve the right to cancel the program at any time. Paying rewards
is entirely at our discretion.

Please make sure your work does not violate any law(s) and does not disrupt or
compromise any data that does not belong to you.
