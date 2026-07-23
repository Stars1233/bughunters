Many of the out-of-scope reports we see involve Gemini or other
[large language models](https://en.wikipedia.org/wiki/Large_language_model)
(LLMs) hallucinating that they are granting some sort of unique privilege
escalation or access to data or a theoretical vulnerability that no one else
has. These can fall into a few different categories including:

*   **‘Do Anything Now’ framing:** Telling the user that the system has access
    to internal systems, administrative passwords, and super-admin global
    privileges. Requires a very high bar of proof. The fact is that most of the
    time, the LLM is showing you what it thinks you want to see when you prompt
    it to give you access. For example, if Gemini claims you have root access to
    Google’s production systems and can read our CEO’s emails, it's probably
    hallucinating.
*   **Speculative vulnerabilities:** Telling the user about a vulnerability
    inherent in the system that definitely exists even though it can't really be
    shown with a Proof of Concept. Therein lies the catch: to qualify for a
    reward, reports of technical vulnerabilities must include a working and
    reproducible Proof of Concept, whether it’s a prompt or a code snippet.
*   **Resource usage:** Getting an individual session to stop responding is not
    uncommon; draining Google servers is both extremely unlikely and in cases
    where it does occur, there are systems in place to detect and mitigate
    excessive resource drain. Therefore,
    hallucinations that claim to exhaust Google resources and rack up millions
    of dollars in charges are almost always completely fabricated.

## Conclusion

As we've said elsewhere, it’s ultimately **you who are responsible for what is
in your report**. If something sounds too good to be true, it probably is.

And keep this in mind: Taking what an LLM says for granted, and not verifying
the findings in the report you’re submitting is a
[Code of Conduct](/about/rules/other/6009584292331520/code-of-conduct-for-our-vulnerability-reward-programs)
violation, and we will
[react](/about/rules/other/code-of-conduct-for-our-vulnerability-reward-programs#enforcement)
to repeated violations.

### References


*   Gemini Apps help center:
    [Getting the Most from Gemini: Understanding its Knowledge and Creativity](https://support.google.com/gemini/community-guide/309961349/getting-the-most-from-gemini-understanding-its-knowledge-and-creativity?hl=en)
