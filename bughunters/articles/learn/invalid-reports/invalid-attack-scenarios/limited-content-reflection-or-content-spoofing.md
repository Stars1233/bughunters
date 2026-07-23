Sometimes, bug hunters share reports describing how they reflected content into
a Google web application in a specific, limited way. For example, they might
display a text message in the body of a page. OWASP uses the names
["Content Spoofing" or "Text injection"](https://www.owasp.org/index.php/Content_Spoofing)
to describe this kind of issue.

If the reflected content is limited (in other words, it's just text, or a safe
subset of HTML that cannot result in XSS), we don't consider it a vulnerability
in itself under our VRP. In web applications, it's useful – and sometimes
necessary – to reflect some parameter values in HTTP responses. Typical
locations that allow you to reflect content are:

*   Error messages which are passed as a GET/POST parameter
*   404 pages
*   Search result pages
*   Web pages that send an email message from a *@(google|youtube|...).com*
    address with partially-controlled message content

Web applications often reflect the content posted by a user, and as long as
there is proper escaping or sanitization to prevent attacks such as XSS and
referrer leaks, that's an acceptable risk for us.

A commonly-reported
[attack scenario](/learn/improve-your-reports/how-to-report/6379261818306560) uses
content reflection to start a social engineering attack. For example, the
attacker displays a Google page with controlled content, and convinces the
victims to perform some actions, exploiting their belief that the message is
authored by Google. Even considering this vector, most of the time we believe
the security impact is too low for us to file a bug and issue a reward. Our
reasoning is that social engineering attacks will (unfortunately) continue to
work regardless, as the attacker might instead send a phishing email with a
spoofed *From:* address with a similar success rate.

To put that into context, social engineering attacks very rarely meet the bar
for reward or credit. For a social engineering attack to be accepted by the
panel, the attack scenario needs to be extremely clear and convincing. This
usually involves chaining several vulnerabilities into an attack that even you
yourself would fall for.

## Conclusion

We made a conscious decision to focus on solving the more pressing problems that
endanger our users' data (like XSS or authorization issues) first, and address
the more subtle issues later. Reports pointing out limited content reflection
usually do not qualify for a reward or credit under Google VRP.
