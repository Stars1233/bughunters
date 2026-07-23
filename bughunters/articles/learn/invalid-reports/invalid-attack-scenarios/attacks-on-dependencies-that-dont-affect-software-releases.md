We sometimes receive submissions that describe attacks hijacking the
dependencies of our open-source packages. For example, a bughunter might
register a package in an external package manager registry (like npm, or PyPI),
add code that executes when the package is installed, and then notice that their
code executed in systems related to Google. Another example would be claiming a
GCS bucket used as part of a build process. These attacks are sometimes referred
to as dependency confusion, or typosquatting.

Such submissions may be in scope for one of our VRPs, but only if the dependency
confusion can demonstrably affect the end products that those programs cover.

For example, in the
[Google OSS VRP](/about/rules/6521337925468160/google-open-source-software-vulnerability-reward-program-rules)
we are interested in vulnerabilities that lead to a compromise of build
artifacts from 1st-party open source projects distributed to our users. For most
of our projects, the software release pipelines are automated, for example by
using GitHub Actions. Similarly, releases of our web services or Cloud products
in scope for the
[Google and Alphabet VRP](/about/rules/6625378258649088/google-and-alphabet-vulnerability-reward-program-vrp-rules)
are performed outside of the developers’ workstations, and our workflows are
built to ensure that a single compromised developer machine cannot impact our
build system. For more information, read about our
[BeyondCorp](https://cloud.google.com/beyondcorp/) zero-trust model efforts.

## Conclusion

Reports detailing dependency confusion or typosquatting attacks that demonstrate
a compromise of a developer's device, or a workflow that only builds and tests
the software without releasing it, will typically not qualify for a reward. To
affect our product releases, the code from the hijacked dependency must be
executed in the automated release pipelines, otherwise the issue can’t affect
the end product.

Since researching dependency confusion attacks requires executing code in
unknown systems, we ask you to take special care not to violate the rules of the
respective programs. Please don't attempt to hack individual users without their
prior permission. Do not attempt to exfiltrate information beyond what is
required to demonstrate the bug, don't install backdoors, and don't remove
unrelated data from compromised systems. Don't make modifications if you believe
that what you are doing might be disruptive, or you do not completely understand
the implications of a change.
