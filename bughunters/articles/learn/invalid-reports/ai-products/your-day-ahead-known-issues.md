Your Day Ahead is an agentic day planner released in May 2026 as part of the
Gemini App. For full transparency and to keep external security researchers
hunting bugs in Google products informed, this article outlines some
vulnerabilities in the new Your Day Ahead feature that we are currently aware of
and are working to fix.

Important: Reports regarding the known security vulnerabilities outlined on this
page will be treated as duplicates and are not eligible for reward under
Google’s VRP program rules.

## Known issues

### Security Policy Bypass Using Generated Cards

Scope: Gemini App's Your Day Ahead agent feature

Description: Your Day Ahead pregenerates prompts - personalized daily plans -
based on untrusted data sources such as emails. The generated prompt is then
surfaced as a card (or multiple) on which the user can click to activate. This
prompt may be attacker controlled and used to leak sensitive data or bypass
policies.

Impact: Data exfiltration or rogue action through prompt injection

Your Day Ahead generates prompts based on various data sources which means
unwanted data might end up in the first prompt and as such may be used for a)
model misalignment; b) exfiltration. While models are instructed to avoid the
issue, there’s no enforcement currently.
