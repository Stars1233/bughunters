Part of what makes
[large language models](https://en.wikipedia.org/wiki/Large_language_model)
(LLMs) so useful is that they're creative tools that can address many different
language tasks. Unfortunately, this also means that LLMs can generate output
that you don't expect, including text that's offensive, insensitive, or
factually incorrect. Preventing these outcomes in modern LLM products is
notoriously difficult because these "vulnerabilities" aren't just bugs in the
code – they are fundamental features of how neural networks process language.

Unlike traditional software, where you can separate the *logic* (the code) from
the *data* (the user input), LLMs treat both as the same thing: a sequence of
tokens to be predicted. In a standard computer program, "input" is just data for
the code to process. In an LLM, the input *becomes* the code. Because the model
uses the same mechanism to understand your instructions ("Don't swear") and your
data ("Write a story about a pirate"), a clever user can blend the two.

Safety filters usually try to draw a "border" around bad topics (e.g., instruct
a model not to mention suicide or not to generate NSFW content). However,
because LLMs don't store raw facts, but only perform mathematical operations on
multi-dimensional spaces with those concepts encoded inside, there are infinite
"backdoors" or paths to the same concept encoded differently.

On top of that, LLMs are trained on publicly available data, which is full of
swearing, political polarization, and harmful content. While there are
techniques to mask that content via reinforcement learning, they don't erase the
harmful knowledge and biases; they just teach the model to *prefer* not to use
it. The harmful data is still reachable "under the surface."

In products based on LLMs this results in whole classes of issues that we can
label as *safety guardrail bypasses*. These can take various forms, where the
user can trick the product into generating:

*   Hate speech & harassment,
*   Violent content,
*   Toxic bias & stereotype amplification,
*   High-harm instructions,
*   Instructions for illegal activities,
*   Suggestions of self-harm,
*   Inappropriate medical advice, including mental health advice,
*   NSFW content,
*   Fabricated facts & hallucinations,
*   Malicious code,
*   Unqualified advice,

and so on (the list is not exhaustive).

Demonstrating these results may sometimes be as simple as just using the API, or
as elaborate as requiring an involved technique of developing a "jailbreak",
inducing a model to undo its safety guardrails.

## Conclusion

These safety guardrail bypass findings are valuable for product teams, and
**should be reported using the appropriate feedback functionality of the product
that you found them in**. That way your findings may be later used to gradually
improve the product.

They are, however, not security vulnerabilities we can simply patch & verify.
**Safety guardrail bypasses in our AI products are not in scope of the
[AI VRP](/about/rules/google-friends/ai-vulnerability-reward-program-rules)**,
regardless of how serious, creative, or easy the exploit is. **All submissions
of issues in this class will be rejected and will not be rewarded.**
