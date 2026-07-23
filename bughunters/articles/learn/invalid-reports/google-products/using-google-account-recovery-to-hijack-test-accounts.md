Occasionally, we receive reports suggesting a flaw in one of Google's
[account recovery](https://accounts.google.com/signin/recovery), password reset,
or password change flows. Typically, bug hunters stumble upon unexpected
behavior when attempting to recover their own test account. When they contact
us, they are dismayed to find that their report is dismissed as "not a bug".
Why? Let's discuss this in detail.

At Google, we're dedicated to offering meaningful security protections to our
users. To achieve this goal, we strive to understand the existing threat
landscape. Account access is no different: we routinely
[research](http://conferences2.sigcomm.org/imc/2014/papers/p347.pdf) and
[present](https://youtu.be/W2a4fRalshI) how hijacking attacks are engineered.
What we observe in the wild is that automated attacks are the most common form
of account hijacking. Accordingly, one of our major goals is to stop
industrial-scale hijacking operations in their tracks.

In contrast, detecting one-off hijacking attacks by people who know the victim
personally or have access to the victim's devices is a much more nuanced task.
Although this task is supported by an ever-growing range of complex heuristics,
it continues to be a difficult balancing act. Ultimately, successfully stopping
a targeted attack is only possible if the user activates
[Advanced Protection](https://landing.google.com/advancedprotection/).

Other methods can reduce the risk of a targeted attack, but do not provide the
same level of security as the Advanced Protection functionality:

*   Enabling [2-Step Verification](https://www.google.com/landing/2step/)
*   Configuring [recovery options](https://myaccount.google.com/security)
*   Using unique and complex passwords
*   Not sharing their computer with people they do not trust

Crucially, our defenses don't stop at the moment hijacking occurs. For example,
we know that a typical hijacker will actively work to lock out the rightful
owner as soon as they gain control of the victim's account. For this reason,
allowing speedy and seamless recovery is essential for our users to minimize the
damage done to their accounts. In that spirit, we try to facilitate the recovery
process, sometimes accepting a misstep or two, if we can determine with a
reasonably high probability that it is the original account owner who is making
the request.

On the downside, this behavior makes it harder to identify and validate security
issues when researching the account recovery flow. For example, attempting to
recover a test account from the same IP or the same browser as the one used to
create it is subject to less rigorous checks, but this is not a bug. Rather,
account recovery is actually working as intended – after all, the researcher
*is* the owner of the test account.

## Conclusion

If you report unexpected behavior when attempting to recover your own test
account, we won't file a bug based on your report for the reasons outlined
above.

However, if you believe that you have discovered a genuine account recovery bug,
please let us know – and remember to explain how the behavior you observed could
be exploited by describing the related
[attack scenario](/learn/improve-your-reports/how-to-report/6379261818306560).

Of course, we'd like to stress that you should **never** attempt to hijack or
recover accounts of other Google users without their permission – even if it's
just a test.
