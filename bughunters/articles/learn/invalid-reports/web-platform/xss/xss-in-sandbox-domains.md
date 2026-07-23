Google uses a range of [sandbox
domains](https://security.googleblog.com/2012/08/content-hosting-for-modern-web.html)
to safely host various types of user-generated content. Many of these sandboxes
are specifically meant to isolate user-uploaded HTML, JavaScript, or Flash
applets. This approach ensures that user-uploaded content can't access any user
data and thus mitigates potential security risks through XSS.

For this reason, we recommend using
[`alert(document.domain)`](/learn/invalid-reports/web-platform/xss/5108550411747328)
instead of `alert(1)` as your default XSS payload, as `alert(document.domain)`
returns the domain where the XSS is injected. This allows you to verify if you
are injecting script on a sandbox domain, which is not considered to be a
security vulnerability.

## Conclusion

If you are injecting script in subdomains of (sandbox) domains such as:

*   `*.doubleclick.net`
*   `*.googleusercontent.com`
*   `*.googlecode.com`
*   `*.codespot.com`
*   `*.feedburner.com`
*   `*.googleadservices.com`
*   `*.googledrive.com`
*   `*.googlegroups.com`
*   `*.{your-blog-name}.blogspot.com`
*   `*.{your-app-name}.appspot.com`
*   `firebasestorage.googleapis.com`
*   `*.storage.googleapis.com`
*   `*.adscape.com`
*   `*.cloud.goog`
*   `*.freebaseapps.com`
*   `*.gmodules.com`
*   `*.googlezip.net`
*   `*.translate.goog`

...we won't file a bug based on your report, unless you can come up with an
attack scenario where the injected code gains access to sensitive user data.
