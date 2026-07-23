While we control all content served from `*.google.com`, `*.youtube.com` and
`*.blogger.com`, it quickly gets more complicated for other domains. Not
everything with a Google logo actually belongs to us. Some web applications are
operated by different companies (vendors and partners), and we can’t authorize
testing those.

Some common out-of-scope sites are:

*   zagat.com
*   adscape.com (it’s not our acquisition)
*   sketchup.com (we sold this in 2012)
*   youtube-creatorcommunity.com
*   community.nest.com
*   training.nest.com
*   advertisercommunity.com
*   cloudconnect.goog
*   localguidesconnect.com
*   googlemerchandisestore.com
*   community.apigee.com
*   community.appsheet.com

## Conclusion

**The above list is not comprehensive**. As a rule of thumb, to determine that a
web application can be security tested under Google VRP, please:

1.  Check in whois that the **IP address** points to Google
1.  Check in DNS that the **domain name** belongs to Google
1.  Check for Google or Google acquisition **branding**

Unfortunately, there are exceptions to the above rules. For example, sometimes a
vendor operates a web application in our IP space, on our domain, and with our
branding (sorry for that, but that’s just the way it is). When in doubt, please
ask us first, and we can quickly verify if a given web application is in scope
for the Google VRP.
