Valid VRP reports about data exfiltration must concern data that is demonstrably
unknown to the attacker through other means. This generally includes sensitive
user data or confidential proprietary information. Also, since
[large language models](https://en.wikipedia.org/wiki/Large_language_model)
(LLMs) are non-deterministic, the attack must also be reproducible multiple
times (thus making it more probable that real data was leaked and not that a
hallucination occurred).

When you report data exfiltration, please make sure your report addresses these
points:

1.  **Reproducibility**: You must provide evidence that specific and verifiable
    data could be repeatedly compromised.

2.  **Validity**: You should demonstrate why the data exfiltrated is very
    unlikely to be a
    [hallucination](https://en.wikipedia.org/wiki/Hallucination_\(artificial_intelligence\))
    (also see our dedicated article on
    [hallucinated sandbox escapes](/learn/invalid-reports/ai-products/hallucinated-sandbox-escape)).
    For example, try to exfiltrate non-shared data from your second test account
    isolated from the first one. Be skeptical about AI suggesting that it can
    access proprietary Google information: try exfiltrating from multiple
    accounts, looking for differences in outputs, search for data occurrence in
    public sources etc.

3.  **Methodology**: You need to show a method an attacker could use to access
    sensitive user information and exfiltrate the information.

4.  **Sensitivity**: The data must be private (e.g. SPII) or otherwise
    unobtainable (e.g., proprietary), and unknown to the attacker (e.g., not
    already shared somehow).

If you're able to exfiltrate sensitive information from a victim account to an
attacker account, please send us a report. Some examples of sensitive
information:

*   A victim's private email content (including email drafts)
*   A victim’s non-shared calendar entries (including details or contacts)
*   A victim's private browser history or search activity

Some examples of non-qualifying data (do **not** report these):

*   Public Information: Display names, profile pictures, posts on public forums
*   Prior Access: The ability for an attacker to view data they could already
    access through other means or permissions in the past

A note on revealing **model preambles and system instructions**: Extracting
fabricated or publicly known system prompts or preamble instructions should not
be reported to the VRP. While interesting for research, this data is often
hallucinated or consists of the well-known basics, and does not constitute a
leak of proprietary information. The exception is if a preamble contains leaked,
non-hallucinated credentials or secrets that clearly comprise proprietary
information.

## Conclusion

Reports demonstrating data exfiltration are only valid in cases where the
exfiltrated data is unknown to the attacker and cannot be gained through other
means, e.g. sensitive user data or confidential proprietary information. In
addition, since LLMs are non-deterministic, you must verify that the attack can
be reproduced multiple times.

### References

*   Google Account help center:
    [Control what others see about you across Google services](https://support.google.com/accounts/answer/6304920)
