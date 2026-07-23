There are many different types of identifiers that are used in URLs all over the
internet to reference resources, and sometimes these referenced resources are
meant to be private. In order to ensure that only authorized users can access
private resources, developers have different options: they can implement
authorization through account sessions, or, alternatively, through passwords and
other secrets.

A very common vulnerability type related to this area is referred to as “IDOR”
(Insecure Direct Object Reference). If an attacker can access a sensitive
private resource simply by knowing its ID, it *might* be an IDOR vulnerability.
However, and this is vital, there also needs to be a clear path for the attacker
to discover the needed ID.

For example, unlisted YouTube videos are identified by a string consisting of 11
characters (for example: `v=ekT65PmCNvk`). If you know this ID, you can access
the video. But, this does not constitute an IDOR vulnerability in itself because
it fails the second test – is there a way for an attacker to discover the ID? If
you think of the secret video ID `ekT65PmCNvk` as a kind of password, then it
should become clear that it is actually a very secure eleven-character-long
password. This means that an attacker cannot simply guess arbitrary video IDs,
and that this is not a security vulnerability.

## Conclusion

When looking for vulnerabilities related to secrets and random IDs in URLs,
always think of how an attacker would get to know the secret in the first place.
Especially for attacks that require guessing a secret, it can quickly become
impossible to do so in a realistic timeframe. Accordingly, reports describing
vulnerabilities based on guessing complex random IDs are almost always not
eligible for reward or credit.
