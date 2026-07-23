According to the definition [here](https://en.wikipedia.org/wiki/API_key):

*An **application programming interface (API) key** is a unique identifier used
to authenticate a user, developer, or calling program to an API.*

Does that mean that any API key you've discovered can automatically be
considered to be a security-relevant issue, and that reporting it to Google
means you will be rewarded? Unfortunately, it's not quite that easy, as not all
API keys are meant to be private. For example, Google uses (public) API keys for
quota controls and to identify client-side applications.

But how can you distinguish public from private API keys? As a rule of thumb,
public API keys at Google generally begin with the string "AIza", making them
easy to identify. However, the most relevant criteria for deciding if a leaked
API key is a security issue, is if the API key could be exploited for malicious
purposes. If you can connect a convincing
[attack scenario](/learn/improve-your-reports/how-to-report/6379261818306560) to
the API key leak, then you have likely found a valid issue.

## Conclusion

Not every API key is meant to be a secret. Accordingly, we won't by default
reward submissions reporting leaks of APIs. If, however, you have found a leaked
API which grants access to private information (like another user's data) or
otherwise constitutes a security issue that could potentially be exploited by a
malicious actor, we look forward to reading your report.
