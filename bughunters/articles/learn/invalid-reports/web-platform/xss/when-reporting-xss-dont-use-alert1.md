Let's admit, we all like seeing this:

![alert(1)](https://storage.googleapis.com/bughunters-article-images/alert1.png)

While *alert(1)* is the standard way of confirming that your attempt to inject
JavaScript code into a web application succeeded in some way, it does not tell
you **where exactly** that injection took place. That's particularly important
for Google services because we use
[sandbox domains](/learn/invalid-reports/web-platform/xss/6619189462433792) to
safely render some of the content we get from our users or retrieve from the
Internet. So, we always recommend that our reporters use
*alert(document.domain)* instead. When you do this, you may end up seeing:

![alert('translate.googleusercontent.com')](https://storage.googleapis.com/bughunters-article-images/alert1_2.png)

The domain *translate.googleusercontent.com* is a sandbox domain used
specifically to display translated documents from all over the Internet – so
this report won't qualify for a reward! What you really want to see is this:

![alert('www.google.com')](https://storage.googleapis.com/bughunters-article-images/alert1_3.png)

## Conclusion

Knowing the domain helps us tremendously when triaging new reports, especially
if they happen to be in services such as Translate, Blogger, Drive, or Ads – all
of which make heavy use of sandbox domains to host user content without creating
security risks. For this reason:

1.  Always use *alert(document.domain)* instead of *alert(1)*.
2.  Check the location of your finding against the list of
    [sandbox domains](/learn/invalid-reports/web-platform/xss/6619189462433792)
    to ensure your finding doesn't apply to a sandbox domain.
