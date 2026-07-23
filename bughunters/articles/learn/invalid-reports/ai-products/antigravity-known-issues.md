[Antigravity](https://antigravity.google/) released a new AI-first coding agent
in November 2025. For full transparency and to keep external security
researchers hunting bugs in Google products informed, this article outlines some
vulnerabilities in the new Antigravity product that we are currently aware of
and are working to fix.

As a general rule, Antigravity reports where the attacker already has local
code execution or the ability to edit files locally will be closed as "Invalid"
and are not eligible for reward under Google’s VRP program rules. For more
information, see our
[Invalid Reports page on this topic](/learn/invalid-reports/invalid-attack-scenarios/attacks-working-only-when-sharing-local-account-with-the-attacker).

Important: Reports regarding the known security vulnerabilities outlined on this
page will be treated as duplicates and are not eligible for reward under
Google’s VRP program rules.

## Known issues

### Data exfiltration through indirect prompt injection

Scope: Antigravity agent (the browser-use agent within Antigravity is out of
scope for this known issues article)

Description: Working with untrusted data can affect how the agent behaves. When
source code, or any other processed content, contains untrusted input,
Antigravity's agent can be influenced to follow those instructions instead of
the user's.

Impact: Data exfiltration through prompt injection via multiple vectors like
Markdown, tool invocation, etc.

Antigravity agent has access to files. While it is cautious in accessing
sensitive files, there’s no enforcement. In addition, the agent is able to
create and render markdown content. Thus, the agent can be influenced to leak
data from files on the user's computer in maliciously constructed URLs rendered
in Markdown or by other means.

### Code execution

Scope: Antigravity agent (the browser-use agent within Antigravity is out of
scope for this known issues article) with *Terminal -> Auto Execution Policy*
set to *Auto/Turbo* (if *Terminal -> Auto Execution Policy* is **Off** please
file a report).

Description: Working with untrusted data can affect how the agent behaves. When
source code, or any other processed content, contains untrusted input,
Antigravity's agent can be influenced to execute commands.

Impact: Code execution through prompt injection

Antigravity agent has permission to execute commands. While it is cautious when
executing commands, it can be influenced to run malicious commands.

