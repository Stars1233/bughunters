<font color="#4285F4"><b>As of July 6, 2026, this program is in a freeze for an
indefinite amount of time and is currently not processing any new requests
(<a href="https://github.com/google/osv-scalibr/issues/1949">details</a>).</b>
All existing accepted contributions will continue to be reviewed.</font>

Earn rewards by patching [OSV-SCALIBR](https://github.com/google/osv-scalibr),
Google's filesystem scanner for software inventory extraction capabilities.

In August 2025, we launched the Patch Rewards Program to reward plugin
contributions to OSV-SCALIBR, our open source filesystem scanner. The goal of
this program is to allow us to quickly extend its scanning capabilities and
enable users to benefit from this program by uncovering more vulnerabilities
in their servers and artifacts.

Note: The program has previously also accepted vulnerability and secret detector
contributions. Acceptance of these plugin types is discontinued and the
program's new focus is solely on software inventory extraction capabilities.

## Application process

Since you as a participant and the OSV-SCALIBR team will need to work together
closely on your contributions, we'll use
[GitHub Issues on our GitHub Repository](https://github.com/google/osv-scalibr/issues)
as the main collaboration channel.

Important: Please don't submit more than 5 pending proposals at a time. See the
[FAQ section](/about/rules/open-source/6436351477940224/osv-scalibr-patch-rewards-program-rules#frequently-asked-questions)
for more details.

The following list summarizes the expected end-to-end process:

1.  Participants first need to submit a new GitHub Issue with the `PRP:Request`
    tag to kick-off the process. Participants should include as many details as
    possible in the request, including details of the new software inventory.
    OSV-SCALIBR team members will evaluate the request and determine whether it
    is in scope for this reward program.
2.  If your request is in scope, you'll be notified in the Issue thread with
    instructions on how to submit the request to our internal panel using our
    [submission form](/report/tsunami). The team might decide to accept your
    contribution but direct you to submit it as a patch for
    [Tsunami](/about/rules/open-source/5067456626688000/tsunami-patch-rewards-program-rules)
    instead of OSV-SCALIBR.
3.  Meanwhile, you can start working on the implementation of the inventory
    extractor. OSV-SCALIBR team members will work with you closely during this
    phase to provide prompt code reviews and feedback on your work.
4.  Once the patch is completed, the OSV-SCALIBR team will perform the final
    evaluation of the quality of your patch and determine the final reward
    amount. You'll be notified by email once the reward amount has been
    determined.

## Qualifying contributions

For the OSV-SCALIBR Patch Reward Program, we currently accept inventory
extractors as contributions.

Note that in the past we have also accepted vulnerability detectors and secret
detectors. Acceptance of contributions under these categories is discontinued.

### Software inventory extractors

OSV-SCALIBR utilizes software inventory extractor plugins to find out which
applications are currently installed on the filesystem. This allows us to
identify vulnerable software by matching the software list against vuln feeds
such as OSV.dev. See the list of currently supported inventory types
[here](https://github.com/google/osv-scalibr/blob/main/docs/supported_inventory_types.md).

We invite you to contribute plugins to extend SCALIBR's software extraction
capabilities. Extraction plugins have to meet the following criteria to be in
scope for the PRP:

*   **The new inventory type should be widely used and have public vulnerability
    feeds.** The extractor should close gaps in identifying software from
    distribution methods that are widely used publicly, and that have public
    vulnerability feeds (e.g. OSV.dev, security.gentoo.org/glsa, GHSA):
    *   **Open source package managers** for OS or language packages (e.g. dpkg,
        npm).
    *   **Compiled binaries:** The extractor should be able to detect a large
        number of binaries from a single group (e.g. JAR files, Golang binaries,
        Rust-PE binaries).
*   **The contribution adds significant improvements to existing extraction.**
    In addition to covering new inventory types, we also accept contributions
    that add to extraction capabilities for existing inventory types as long as
    they greatly improve accuracy or add significant new coverage for previously
    missed software.
*   **The new extraction logic is performant.** OSV-SCALIBR is designed to run
    on people's laptops and hosts with limited resources such as available
    memory. Any new extraction capability should make sure we don't perform
    expensive operations that might require a lot of I/O or memory usage.
*   **The extractor should have good unit test coverage.** Just as for our
    detectors, any new extractor plugins (or new capabilities in existing
    plugins) should be thoroughly tested with unit tests using fake data.
*   **The extraction capability should be easy to verify using Docker images.**
    As part of the contribution, a Docker image containing examples of the given
    software type should be attached to showcase how the new extraction
    capabilities work. In cases where this is not possible (e.g. the plugin is
    for commercial software), the contribution should include instructions on
    how the plugin can be tested on e.g. a trial version of the software.

## Reward amounts

The reward amount usually depends on the prevalence of the software type being
covered, as well as the quality of the plugins written.

The final amount will always be chosen at the discretion of our reward panel.
The following points outline the usual maximum reward amounts:

### Software inventory extractors

The reward amount varies based on the type of vulnerabilities that the new
extraction capability allows us to find through vuln matching:

*   Up to **$2,000** for extraction capabilities that can be matched to an OSV
    ecosystem, with corresponding OSV.dev vulnerability records.
*   Up to **$1,337** for extraction capabilities for widely used software
    distribution systems that have a public vulnerability feed, but no OSV
    ecosystem or no OSV.dev vulnerability records.

## Code of conduct

To ensure a healthy and productive relationship between participants and the
Google teams interacting with them, we have defined a
[Code of Conduct](/about/rules/other/6009584292331520/code-of-conduct-for-our-vulnerability-reward-programs)
laying out the expected behaviors from both sides.

Thank you in advance for familiarizing yourself with this code and adhering to
its provisions!

## Frequently asked questions

*Q: What if someone else also submitted a proposed plugin for the same
software?*

A: We will accept the proposal of the person who first submitted it. In such
cases, we will recommend you find a different plugin to work on instead.
However, if the person who submitted the first proposal ends up dropping their
work, you will be given the opportunity to pick it up and be rewarded for it
(see next question for more details).

*Q: What if someone dropped their work in the middle of the process?*

A: OSV-SCALIBR team members will continuously sanitize all the tracking GitHub
Issues for this program. Any issue that is silent for 1 week will be marked as
inactive using the `PRP:Inactive` tag. Anyone can pick up the remaining work
related to an inactive issue. The final reward might be split between all the
contributors of the issue, based on the scale of contributions.

*Q: How many pending proposals can I have in parallel?*

A: Please don't submit more than 5 proposals at a time, including the ones you
are currently working on. If a participant has more than 5 pending or active
proposals at a time, the later ones will have the `PRP:Inactive` tag applied,
allowing other contributors to work on them.

*Q: How will I get paid?*

A: You will be paid through our established VRP payment process. We'll ask you
for your contact details after your submissions are selected for the program,
and our payment team will work with you to finalize the payment.

## Historical reward amounts

Previously, the OSV-SCALIBR PRP has also accepted vulnerability and secret
detectors. Acceptance of new contributions in this area is discontinued.
Existing accepted contributions will be merged in and rewarded according to the
following legacy reward guidelines:

### Vulnerability detectors

-   Up to **$3,133.7** for "wishlist" detectors.
-   Up to **$2,000** for detecting a larger class of security risk on the
    artifact going beyond software version comparison for individual CVEs.
-   Up to **$1,500** for other contributions.

### Secret detectors

A single submission is typically expected to encompass the most relevant secret
types of a given platform (e.g.
[most commonly used GitHub PATs](https://github.com/google/osv-scalibr/tree/main/veles/secrets/github),
not just one PAT type).

#### Secrets requiring simple detection methods

This includes simple applications of existing helper libraries, e.g. regexp
searches and simple HTTP request-based validation.

*   Up to **$700** for detection with validation.
*   Up to **$300** for detection without validation.

#### Secrets requiring complex detection methods

*   Up to **$1,500** for detection with validation.
*   Up to **$700** for detection without validation.

## Legal points

The same disclaimers apply as for the
[general Google VRP program](/about/rules/google-friends/6625378258649088/google-and-alphabet-vulnerability-reward-program-vrp-rules#legal-points).

## Changelog

*   2026-07-06: Froze the program. All existing accepted contributions
    will continue to be reviewed.
*   2026-04-09: Scoped out vulnerability and secret detectors from the program.
*   2026-04-02: Updated acceptance criteria for extractors.
*   2026-02-12: Further clarifications on reward calculation for secret
    detectors.
*   2026-01-16: Updated criteria for vuln detector submissions.
*   2026-01-07: Added clarification on reward amount calculation.
*   2025-08-29: Added risk-related criteria for secret scanning submissions,
    removed the "critical, emergent vulns" category from reward amounts for
    inventory extractors since it was difficult/impossible to reach.
*   2025-08-12: Added rule limiting the maximum number of proposals per
    participant.
*   2025-08-06: Initial version.
