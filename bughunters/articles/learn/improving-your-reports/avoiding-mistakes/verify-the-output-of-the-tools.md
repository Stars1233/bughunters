Bug hunters frequently use a variety of tools that automate the job of finding
vulnerabilities. These tools come in various flavors, like automated scanners,
fuzzers, or even short proof-of-concept scripts. Properly configured tools can
be indispensable and help quickly identifying bugs that would have been very
hard to find manually. At the same time, the output of these tools is not
perfect: it can almost never be taken at face value and must be reviewed and
verified by you, the researcher. In other words, make
"[trust, but verify](https://en.wikipedia.org/wiki/Trust,_but_verify)" your
motto!

While we always work hard to understand and analyze incoming reports, you can
help greatly by verifying scan results and providing a realistic attack scenario
in your vulnerability reports:

*   When working with automated tools, always double-check their output and make
    sure that the findings are not
    [false positives](https://en.wikipedia.org/wiki/False_positives_and_false_negatives#False_positive_error).
*   As a rule, before sending a report, try to really understand the way in
    which the vulnerability is supposed to work and how our services could be
    affected by it – and capture these aspects in your report. Such high-quality
    reporting makes it far more likely for your bug to be processed efficiently.

## Commonly reported false positives

Some examples of false positives we've observed in the past:

*   **Google servers vulnerable to [CRIME](https://en.wikipedia.org/wiki/CRIME),
    [BEAST](https://en.wikipedia.org/wiki/Transport_Layer_Security#BEAST_attack)
    or [POODLE](https://en.wikipedia.org/wiki/POODLE)** – Some automated
    scanners incorrectly detect that servers at www.google.com or other popular
    Google domains are vulnerable to CRIME, BEAST, or POODLE. That's pretty
    unlikely, as we have various mitigations in place. Read more about this in
    [Commonly reported SSL/TLS vulnerabilities](/learn/invalid-reports/network-protocols/6114200428216320).

*   **SQL injection** – For example, one automated tool "detected" an SQL
    vulnerability in this "PHP script":

    `http://www.youtube.com/foo/a-script.php?id=1%22%20UNION%20ALL%20SELECT%20null,null,1,null,null/\*`

    The thing is, YouTube does not use PHP. In fact, the supposedly vulnerable
    location does not exist at all. The tool probably noticed that the string
    passed in the URL is reflected somewhere in the HTML code, and incorrectly
    inferred the presence of a security bug. The reporter spent a lot of time
    writing up the report and explaining the implications of SQL flaws, but
    neglected to verify the presence of the underlying bug (even by simply
    visiting the page). It is always heartbreaking to put a lot of effort into a
    report and then have it rejected, so be sure to confirm the issue first!

    In fact, the stats we gather show that looking for SQL injection issues in
    core Google products is probably not the best investment of a bughunter's
    time. In 2014, we received over 80 SQL injection reports, but none of them
    resulted in a reward or credit.

*   **XSRF** – Some reporters rely on automated heuristics to detect if an HTML
    form is prone to XSRF. Alas, due to the nature of this vulnerability,
    writing a truly robust automated check is very difficult. The output from a
    scanner always needs to be manually verified – a fact
    [acknowledged](http://releases.portswigger.net/2014/11/v1608.html) by the
    authors of such tools. We often get reports with XSRF proof-of-concept code
    copied and pasted from an automated report, only to realize that the snippet
    actually
    [contains an XSRF token... just with a less obvious name](/learn/invalid-reports/web-platform/csrf-clickjacking/5910900768505856).

*   **Output from scanners analyzing HTTP headers** – Many scanners check HTTP
    request and response headers – and flag the presence or absence of certain
    values as a potential security risk. Unfortunately, such tools tend to be
    extremely noisy: not every cookie needs to be httpOnly, not every resource
    needs to be served with
    [*X-Frame-Options*](/learn/invalid-reports/web-platform/csrf-clickjacking/4895052285083648),
    and not every HTML5 CORS header (e.g. *Access-Control-Allow-Origin: \**) is
    a problem, especially if set on a static file that is meant to be accessible
    publicly.

## Conclusion

To reiterate: “Trust, but verify”. It's much easier for us to triage your report
if you've verified the bug and provided a viable
[attack scenario](/learn/improve-your-reports/how-to-report/6379261818306560).
If there does not appear to be a realistic security impact, it is likely the
report will not qualify for a reward or credit.

Sending multiple incomplete reports containing unverified findings from
automatic tools in hope of a reward is actually a bad bughunting strategy, and
it's better to invest your time in searching for the next, valid bug.
