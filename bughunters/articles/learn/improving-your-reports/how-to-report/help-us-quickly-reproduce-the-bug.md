Google has a lot of web properties to defend. There are hundreds, if not
thousands of individual apps, a multitude of different account types,
permissions, and sharing settings. Some of the services come in many flavors –
one for mobile users, another for desktop systems, and yet another with a bunch
of experimental features that are being made available to a few selected
testers.

In fact, you may be more familiar with the tested application than the member of
the Google Security Team who happens to be handling your report this time.

In this spirit, please make it easy for us to reproduce and confirm bugs!
Reports like the following one are really confusing:

*Hi Google! There's an XSS in Google Fuzzy Bunnies. When the attacker submits
JavaScript code to the server, it will execute.*

You don't necessarily have to write an essay; for example, for most types of
reflected XSS, providing a repro URL is sufficient:

*Hi Google! There's a reflected XSS in Google Fuzzy Bunnies. To reproduce, visit
`https://fuzzy-bunnies.google.com/bunny_dispenser?bunny_type="><script>alert(document.domain)</script>`*

Even in more complicated cases, we need just the bare minimum of information
required to reproduce the bug:

*Hi Google! I found an XSS vulnerability in Google Fuzzy Bunnies.*

*Steps to reproduce:*

1.  *Go to `https://fuzzy-bunnies.google.com/bunny_contact_form`*
2.  *Click "Chat with a bunny specialist".*
3.  *Insert `"><img src=x onerror=alert(document.domain);// >` in the text
    field.*
4.  *Click "send".*

Tip: Try to **repeat the attack** by following your description. This helps you
catch any omissions and avoid a time-consuming back-and-forth with our team.

With this improved version of the bug report, it is easy for us to determine
that this is a nasty bug. But as we can reproduce it easily without circling
back to you, we can fix it quickly, get you a reward, and end up with more time
to devote to other important bugs!
