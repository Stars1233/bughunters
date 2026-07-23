NotebookLM Chat is an evolution of NotebookLM released in May 2026. It is
intended to extend NotebookLM functionality to perform complex, economically
useful tasks E2E, and enhances NotebookLM’s existing capabilities as an
information tool. For full transparency and to keep external security
researchers hunting bugs in Google products informed, this article outlines some
vulnerabilities in the new features that we are currently aware of and are
working to fix.

Important: Reports regarding the known security vulnerabilities outlined on this
page will be treated as duplicates and are not eligible for reward under
Google’s VRP program rules.

## Known issues

### Lack of URL Sanitization leading to Data Exfiltration

Scope: NotebookLM browsing feature

Description: NotebookLM's new release has a browsing functionality that fetches
websites while performing research. An attacker can influence this mechanism
through malicious content (e.g. malicious sources) to fetch arbitrary pages. The
URLs of these pages may be constructed by the LLM which can lead to data leakage
from already added sources or chat history.

Impact: Data exfiltration
