An attacker can always trick an end user into running attacker-supplied code,
e.g. by enticing victims to paste commands into their terminal, enter JavaScript
into their browser developer tools, forward sensitive tokens to attackers, or
take many other actions which they might not understand, but which have security
impact. Since AI-powered applications often enable natural language interactions
with the users, these same attacks can also be executed through those
applications. When we think about VRP reports, we often consider who the victim
and the attacker are, and what impacts the victim. In a "single-user scope"
scenario, where an attacker and victim are the same account, this security
boundary does not exist.

## Conclusion

When submitting an AI related report, it’s important to keep in mind the
following points:

-   **Self-pwn**: If an issue only triggers when a user intentionally types,
    pastes, or agrees to running a command, they are effectively “attacking”
    themselves. Such methods are effectively safety control bypasses rather than
    security issues.

-   **Safety guardrails bypasses**: See our
    [Safety guardrails bypasses](/learn/invalid-reports/ai-products/safety-guardrails)
    page. Please report inappropriate content using in-product links so our AI
    safety teams can address the issue – issues of this type are not considered
    security issues and will be rejected by the
    [AI VRP](/about/rules/google-friends/ai-vulnerability-reward-program-rules).

-   **Framing**: Always format your report to clearly distinguish actions taken
    by an attacker (initiating an exploit) and a victim (suffering impact from
    the exploit). If the attacker and the victim are the same user, the report
    will likely be closed.

-   **Interaction**: Valid attack scenarios should require minimal interaction
    from the victim. If a victim needs only say “hi” to an
    [LLM](https://en.wikipedia.org/wiki/Large_language_model) to trigger a rogue
    action or data exfiltration, this is likely a valid VRP report.

-   **Single-user saved context**: Many AI tools, including Gemini, “remember”
    interactions from one user session to the next. On its own, this is expected
    behavior; users can clear this history (e.g.,
    [Gemini saved info](https://gemini.google.com/saved-info)).
