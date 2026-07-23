We occasionally receive reports mentioning that a
[reCAPTCHA](https://www.google.com/recaptcha/intro/index.html) challenge
presented to users when, for example, they create a Google account, can be
bypassed or that an invalid answer to a challenge is accepted. For instance,
when users enter an incorrect response, or select an incorrect image, they still
pass the challenge. While this behavior might be surprising, it's actually
working as intended, and is a technically interesting product feature of
reCAPTCHA.

reCAPTCHA’s risk engine evaluates a wide range of signals to distinguish humans
from bots. It is an adaptive CAPTCHA challenge system: the more abusive your
behavior becomes, the harder the challenges will be. reCAPTCHA’s verification
model uses several factors to determine the probability that a user is a human,
not just the answer provided. We allow humans to make mistakes when solving a
challenge, while punishing bad bots even if they submit a correct answer.

It is expected that, if the system determines you're likely a human, it accepts
your answer despite knowing that it's invalid. In fact, this feature is
necessary to be able to combat spam effectively – if we were to always require a
correct answer, it would be easier to create an automated solution to bypass
reCAPTCHA challenges. By accepting invalid answers (and sometimes rejecting
valid ones!), creating this kind of bypass is much more complicated for
spammers.

## Conclusion

Because of their nature, testing reCAPTCHA bypasses manually is quite difficult.
However, if you're able to create an automated bot that can consistently bypass
reCAPTCHA challenges in a large number of cases, please let us know!
