An attack scenario is essentially a brief summary of:

*   Who wants to exploit a particular vulnerability,
*   For what gain, and
*   in what way.

The goal isn't to simply go over the
[reproduction steps](/learn/improve-your-reports/how-to-report/6029551655976960)
of the bug itself, but rather to explain the way the entire exploitation process
would play out.

For some vulnerabilities, such as an XSS bug on www.google.com, the attack
venues and the risk are pretty clear. But when reporting more esoteric and
complex problems, it helps us to have a good analysis of this sort. For example,
we received a report showing that our implementation of
[SAML](https://en.wikipedia.org/wiki/Security_Assertion_Markup_Language) is
non-compliant with a particular aspect of the 300-page specification for the
protocol; we had to scratch our heads for a long time to figure out the
implications of that report!

Sometimes, writing an attack scenario helps you discover that a particular issue
has less impact than you initially thought, perhaps because the attacker would
need to start at a privilege level where nothing new is gained by leveraging the
bug. The opposite can also be true: even the most seasoned security researchers
sometimes realize that the bug they found is more serious than it seemed as soon
as they write down the full attack scenario.

To illustrate this point, consider the following reproduction steps:

*Hi Google! I found a vulnerability in all Chrome extensions. Steps to
reproduce:*

1.  *Install any Chrome extension.*
2.  *Get the ID of the extension from the page at chrome://extensions/.*
3.  *Go to ~/.config/google-chrome/Default/Extensions/{ID here}.*
4.  *Find a JavaScript file containing the code of the extension.*
5.  *Backdoor the extension with the following script: [...] The extension can
    now exploit arbitrary pages and e.g. extract your Gmail messages to get your
    passwords from third-party pages.*

Trying to write an attack scenario quickly reveals a flaw of this report:

*Attack scenario*

1.  *Attacker gets access to the victim's computer, being logged as the targeted
    user.*
2.  *Attacker runs these commands to gain access to...um...*

Of course, if the attacker is
[in that starting position](/learn/invalid-reports/invalid-attack-scenarios/6576292268605440),
they could just install malware on the machine. Backdooring an extension is also
possible – but this is not particularly interesting or unique.

Here are some tips for writing great attack scenarios:

1.  Think about the **starting position the attacker** is in. What do they
    already have access to, and what is still beyond their reach?
2.  Articulate **assumptions about the victim**. For example, do they need to be
    particularly gullible? If so, does your attack make them substantially more
    vulnerable, or are they doomed either way?
3.  Think about any other **prerequisites for the attack** and their broader
    ramifications. For example, if the attack depends on outdated software, how
    does it compare to exploiting known security bugs in the outdated program?
4.  Write down what the attacker and the victim must do, **step by step** and in
    the right order. This is particularly important if there are multiple
    parties or accounts involved.
5.  Always **re-read the summary** and make sure that it's easy to follow :-).

Finding coding flaws is fun, but being able to think about and clearly
articulate complex attack scenarios is what really makes a successful bug hunter
– so any time invested in writing down attack scenarios pays off in the long
run. Many of us have a background in security research and can attest to
that fact :-).
