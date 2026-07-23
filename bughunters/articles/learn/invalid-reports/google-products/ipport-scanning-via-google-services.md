Occasionally, we receive reports about Google products that issue network
requests to third-party services, with an attacker-controlled destination IP
address/port number. The attack scenario usually mentions a Google product
acting as a proxy to perform an IP/port scanning attack.

If the accessed IP addresses are public, we don't consider this to be a
vulnerability in itself. In fact, oftentimes it's a legitimate product feature.
For example, a feed-grabbing application needs to access feeds under a certain
user-specified URL. If the only gain for attackers is the ability to hide their
IP address, there are various other ways to achieve this goal (e.g. Tor). In
addition, the vast majority of proxy services we have include the original
user's IP anyway.

If the concern is Denial of Service, using Google services to port scan is
probably suboptimal as several [insanely fast](https://zmap.io/) port scanners
exist and it's up to the target endpoint to appropriately react to the incoming
traffic.

## Conclusion

Reports based on 'IP/Port scanning via Google services' scenarios such as the
ones described above generally don't qualify for credit or rewards in the
context of the Google VRP. That said, there are two notable exceptions:

*   If you are consistently able to get us to send repeated requests at a high
    rate, please let us know. For the purpose of being a good network citizen,
    we prefer to fix such issues.
*   If you're able to fingerprint our **internal** networks through public
    services, or use special protocol handlers like `file://` to access files
    (use
    [SSRF bible](https://docs.google.com/document/d/1v1TkWZtrhzRLy0bYXBcdLUedXGb9njTNIJXa3u9akHM/edit)
    for inspiration), we'd like to know. It's most likely a vulnerability
    ($$$!).

When in doubt, please send us the report and we'll promptly review it.
