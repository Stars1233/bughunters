An "abuse risk" can be defined as a product feature that can cause unexpected
damage to a user or platform when leveraged in an unexpected manner. Abuse risks
arise when a product doesn't have sufficient guardrails in place to protect its
features from being (mis)used in a malicious way.

For example, the ability to import your contacts into a social network app to
see which one of your friends is using the app is considered a feature. But,
this feature can become an abuse risk if there isn't a quota in place on the
amount of contact lookups that can be performed within the app during a given
timeframe. Without any restrictions in place, malicious actors could use this
feature to build a large database of users for their spam campaigns.

Contrary to security vulnerabilities, where an identified loophole requires a
fix, abuse risks are often inherent to product features. That means that
oftentimes, features shouldn't be disabled, but that these product features
require protections mitigating their exploitation at scale.

## Preventing abuse in the design phase

When we design our products, there are always multiple reviews, where we aim to
prevent or mitigate each abuse risk that may exist before they launch. During
these reviews, our product abuse, privacy and security experts that work across
many different teams within Google, define the threat model for each new product
or feature launch to ensure that the product launches with the safest and best
user experience.

Even though new product launches are subjected to multiple reviews, sometimes
there are abuse cases that we may not have thought of. Thanks to the
collaboration with our security community we can identify and fix these issues
before our adversaries get the chance to exploit these abuse risks.

## How we assess abuse risk reports

For any given report submitted to Google’s VRP, we initially triage whether the
report is a security vulnerability, a significant abuse risk, or a non-issue. If
a report describes an issue which doesn’t fall under the traditional definition
of a security vulnerability, but is still an issue that could potentially harm
our users or products, then that report is triaged to our product abuse experts
that work within Google’s Trust & Safety Team.

When we decide to not “accept” a report in our program, the most common reason
is that we don't see the critical severity of the proposed attack scenario. If
you see something that we may have missed, then please feel free to respond with
a more detailed attack scenario. We read all responses to our bugs, even if they
are closed.

The most important thing to consider when writing the attack scenario for an
abuse risk, is to consider how the process would play out and what the overall
damage would be to a user or platform. Reports that don't have a clear victim or
abuse scenario and where the attack only affects the attacker’s own user
experience will most likely be out of scope. Please bear in mind that we only
consider attacks that can be scaled up or have privacy consequences as a
significant abuse risk. One-off instances of abuse are not in scope. Common
issues that fall under this category are reports related to SPAM, content, or
refund abuse.

In regards to a reward amount, the impact of an abuse risk is measured
against the number of users at risk and the user privacy at issue. Abuse risks
that are highly scalable, and therefore have more potential users affected, are
considered high risk. Similarly, reports touching on user privacy, meaning that
the issue could result in the leak of personal data of users, are also rated as
a higher impact abuse risk based upon the sensitivity of the user data. Overall,
each report is assessed against the given likelihood of a successful attack,
plus the impact of a reproducible attack scenario against our users and
platforms.

For full details on qualifying vulnerabilities and reward amounts, see the
[Abuse VRP rules](/about/rules/google-friends/5238081279623168/abuse-vulnerability-reward-program-rules).
