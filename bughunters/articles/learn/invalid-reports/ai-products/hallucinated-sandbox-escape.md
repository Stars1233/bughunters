Gemini is a
[large language model](https://en.wikipedia.org/wiki/Large_language_model) (LLM)
that has built-in support for responding to and even executing Linux Operating
System-related commands, as well as understanding certain URLs and data sources
the user is looking for. **All** commands are executed in a sandbox, so we would
expect any exploit to contain a [gVisor](https://gvisor.dev/) sandbox escape.

If you would like to learn more about sandbox security, we recommend
investigating gVisor directly instead of trying to interact with it through a
Gemini interface. Modern LLMs are trained on a vast amount of shell execution
logs in various operating systems, and are thus really effective in simulating
code execution. Attempting to bypass a code execution sandbox only through
Gemini makes your research harder, as you never know what the systems actually
executed, and what is just a result of a very convincing hallucination.

## Do/Don't Report

Here are some simple examples to guide your hacking journey:

Do report:

*   A standalone gVisor sandbox escape, if you can demonstrate it against
    Gemini.
*   A vulnerability in Google AI Studio that allows code execution when a victim
    clicks a link, which can exfiltrate their credentials.
*   If Antigravity runs code when an untrusted Git repo is loaded.

Do **not** report:

*   Any vulnerability where an AI model said a vulnerability was present or
    exploitable, and you did not verify. Be careful as code and comments can
    also contain hallucinations.
*   If AI Studio or other tools generated or deployed insecure
    code/configuration at your request.
*   If Antigravity or other tools run code when a victim types a prompt
    including a direct instruction like "please run this code".

## Conclusion

If you believe you have found a code execution sandbox escape in Gemini or
similar vulnerabilities, we expect you will be able to form your attack against
a gVisor Docker container, or give otherwise convincing evidence of having
achieved a sandbox escape and thus accessing another user's session data in the
form of **irrefutable**, **technical** data. If you cannot do this, your report
will be closed.

### References

*   gVisor: [Security and Vulnerability Reporting](https://gvisor.dev/security/)
*   gVisor:
    [Docker Quick Start](https://gvisor.dev/docs/user_guide/quick_start/docker/)
*   Gemini API docs:
    [Code execution](https://ai.google.dev/gemini-api/docs/code-execution)
