In various Google products, it's possible to give other users access to certain
resources. For example, in Blogger you can invite other users to
[administer your blog](https://support.google.com/blogger/answer/42673), and in
Drive you can share your files. These sorts of features often work by generating
a URL with a token, and sending that URL to another user. When the URL is
accessed, the user is granted the appropriate access.

Sometimes, we are notified about cases where the URL has been shared with a
Google account (its intended recipient), but the link also works when opened
from a different account — giving that other (unintended) user access to
whatever was shared.

Is this a vulnerability? It depends. Reports of this type are always evaluated
in the context of the affected application and the resource being shared. Often,
the behavior is intended and well documented (for example, YouTube's
[unlisted videos](https://support.google.com/youtube/answer/157177) or Google
Drive's [Share using a link](https://support.google.com/drive/answer/2494822)
feature) — in these cases, “it’s not a bug, it’s a feature.” Sometimes, though,
things are not that clear.

When evaluating the severity of a reported issue, we take the following
technical factors into consideration (at a minimum):

*   Does the URL expire? For how long is the “attack window” open?
*   Can the URL be used only once?
*   Is it an https:// URL?
*   What is the token for?
*   Is the token short enough to be brute-forced?

Some non-technical factors are also considered. For example, when the URL is
created, what do we say to the user? Can they
[reasonably](https://en.wikipedia.org/wiki/Reasonable_person) expect that the
URL might be shared and forwarded to other users? How is this aspect documented
in the product help, support articles, or UI text?

## Conclusion

All of the factors mentioned above help us assess the impact of the issue and
determine what a successful attack would require. For example, if the URL
expires after use and is sent to the recipient's email address, the attack
scenario requires either an account compromise at the time of sharing, or an
untrustworthy owner who shares the URL. In such cases, even linking the URL to
the intended recipient’s email address wouldn't help, because the attacker might
leverage the compromised account or cooperate with the mischievous user.

If you encounter URLs with tokens that provide access to other users’ resources,
please take these factors into consideration and let us know the results of your
investigation. We're looking forward to your report!
