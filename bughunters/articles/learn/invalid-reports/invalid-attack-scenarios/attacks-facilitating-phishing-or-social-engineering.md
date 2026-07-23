Social engineering attacks very rarely meet the bar for reward or credit. For a
social engineering attack to be accepted by the panel, the attack scenario needs
to be extremely clear and convincing. This usually involves chaining several
vulnerabilities into an attack that even you yourself would fall for.

A significant number of incoming vulnerability reports fall into a specific
category: issues with the sole purpose of facilitating social engineering
attacks against Google users. For example:

*   An
    [open redirect](/learn/invalid-reports/web-platform/navigation/6680364896223232)
    can send victims to a phishing page, abusing their trust in a Google domain.
*   A Google URL can
    [trigger a file download](/learn/invalid-reports/web-platform/navigation/6436972052348928),
    where the attacker controls the file content. Victims might download and
    open a file that executes code on their devices.
*   [Attacker-controlled text](/learn/invalid-reports/invalid-attack-scenarios/5748155129528320)
    can be displayed on a Google-owned website, enticing users to visit a
    phishing website.
*   A Google application can be linked to an external URL that, when opened,
    [replaces](/learn/invalid-reports/web-platform/navigation/5825028803002368)
    the original Google page (e.g. tabnabbing).
*   An attacker can send emails to Google users and control parts of the email
    messages, starting a phishing campaign.
*   Some emails sent from spoofed addresses are not detected as spam by Gmail.

## Conclusion

Although we agree that issues like the ones listed above have an impact on
security, we've decided that Google's Vulnerability Reward Program should focus
on technical problems that endanger our users' data (like XSS and authorization
issues), while these subtler and harder-to-solve issues are addressed in other
ways.

We might reconsider this approach in the future, but for now, without the data
and metrics to measure the efficacy of these changes, we have to depend on our
intuition and experience. And our instincts tell us that, for average users, the
changes aren't worth the cost. For example, we think that even if there were no
open redirects, a similar percentage of users could still be successfully
phished from [deceptive domain
names](https://en.wikipedia.org/wiki/IDN_homograph_attack) — so fixing
individual open redirects is simply ineffective for addressing phishing in
general. If you have research data that shows otherwise, please let us know. For
now, we think [Security
Keys](https://support.google.com/accounts/answer/6103523?hl=en), [Safe
Browsing](https://transparencyreport.google.com/safe-browsing/overview), and
[Password
Alert](https://googleblog.blogspot.com/2015/04/protect-your-google-account-with.html)
are better positioned to help protect our users.

We hope this clarification won't discourage you from submitting bug reports — we
look forward to seeing what you find!
