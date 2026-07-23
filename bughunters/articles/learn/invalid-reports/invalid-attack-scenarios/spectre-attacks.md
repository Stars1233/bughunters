Google protects its web applications against Spectre attacks by using a variety
of HTTP response headers like:

*   Cross-Origin-Resource-Policy
*   X-Content-Type-Options
*   Cross-Origin-Opener-Policy
*   X-Frame-Options

Further defense mechanisms include the use of SameSite cookies and Fetch
metadata request headers.

Finally, Google also attempts to protect Chrome extensions by isolating data
from content scripts.

## Conclusion

When receiving vulnerability reports on Spectre attacks, we will evaluate if
they provide new information that we are not already aware of, and reward
accordingly. As such, not all vulnerability reports will qualify for a reward as
part of the VRP.
