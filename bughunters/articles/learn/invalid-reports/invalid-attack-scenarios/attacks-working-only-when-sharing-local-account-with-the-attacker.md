A lot of vulnerability reports mention issues that can only be exploited when
both the attacker and the victim use the same local user account on a single
device (for example when logging in to your Google account on a computer in a
public library, or in an internet cafe). In such a case, the attacker and the
victim are both logged in to the same operating system user account and may even
share the same browser profile.

Reporters point out that in such setups, the attacker may be able to:

*   Recover a password entered into a website
*   Reveal multiple passwords from the browser's Password Manager
*   Extract sensitive information from the files stored in a browser profile
    directory, or in the browser cache
*   Capture cookies or anti-CSRF tokens transmitted in the encrypted HTTPS
    stream (by using the proxy) and reuse them even after the victim has already
    logged out

Technically, it's all true. But in a more general sense, sharing the same device
& OS account with a sufficiently skilled, malicious user poses an inherent
security risk. That's why it's customary to share your phone or computer only
with people you trust. Sure, there are several countermeasures which can help
minimize casual attacks, such as always making sure you log out of your browser
account, clearing your cookies, etc. That said, in most cases, it's impossible
to prevent a motivated attacker from causing damage if you allow them to use
your OS account.

Even if Google web applications and browsers were hardened to prevent the above
attacks, evildoers could still:

*   Install a malicious keylogger browser extension to exfiltrate all passwords
*   Scan the memory to extract pieces of browsing history
*   Simply replace the browser with a malicious look-alike (e.g. making the log
    out functionality do nothing)
*   Install any other malware
*   Install a CA certificate and setup an HTTP proxy to be able to decrypt your
    network traffic and reuse the tokens while you're still logged in

Because the operating system itself does not protect against attackers with this
level of access, any fix we could implement would be easy to bypass. We hold the
belief that it's impossible to win this
[arms race](https://en.wikipedia.org/wiki/Arms_race) without significantly
changing how the web, browsers, or operating systems work. This view is shared
by the Chrome Security Team, in fact, they've already
[written about it](https://chromium.googlesource.com/chromium/src/+/main/docs/security/faq.md#Why-arent-physically_local-attacks-in-Chromes-threat-model).

## Conclusion

Unless you have identified an attack that substantially undermines these
assumptions, reports pointing out vulnerabilities that can only be exploited
when the attacker is logged in to the same OS account as the victim will almost
certainly not qualify for a reward or credit.
