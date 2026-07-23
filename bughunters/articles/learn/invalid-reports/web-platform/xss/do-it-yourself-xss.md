We receive a steady stream of reports from users who manually alter the HTML
documents returned by our services (for example, with Firebug, Zed Attack Proxy,
Burp Proxy, or Chrome Developer Tools) and inject `alert(1)` or equivalent
JavaScript statements:

![Code execution via Developer Tools](https://storage.googleapis.com/bughunters-article-images/devtools.png)

Note that the ability to inject code is not a bug; browsers allow users to alter
HTML or execute JavaScript locally in the context of any application.

## Conclusion

If you report an XSS injection issue of the type described above, we won't file a
bug based on your report, as we do not consider this to be a security bug.

Why? If an attacker can convince the victim to manually paste JavaScript code
into Chrome Developer Tools, there is nothing that a web application could do to
prevent the attack. As usual, when in doubt about the security relevance of an
issue, try to think about a realistic
[attack scenario](/learn/improve-your-reports/how-to-report/6379261818306560): List the steps that an
evildoer would need to complete in order to gain access to the data of another
user.
