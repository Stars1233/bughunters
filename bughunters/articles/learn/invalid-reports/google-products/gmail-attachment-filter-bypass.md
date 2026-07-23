Some bug hunters report that they are able to upload files considered to be
malicious to our services. A common example is the ability to upload denylisted
file types as Gmail attachments by, for example, compressing the file multiple
times, or by changing the file extension.

Gmail service file attachment scanners aim to prevent these kinds of attacks on
Gmail users, but are necessarily imperfect. There will always be a combination
of operating system and applications used by certain users that make certain
file types executable (for example, PHP files or script files of various
languages may execute arbitrary commands if the user has a given interpreter
installed). Similarly, seemingly benign image or video files may trigger memory
corruption vulnerabilities in image or video parsers.

We don't consider the Gmail attachment filter (or similar solutions in other
Google services) to be a sufficient protection mechanism against such attacks.
While these filters may defend against simple vectors, they are not designed to
be comprehensive solutions protecting against all files downloaded off the
internet, especially if social engineering is used to trick a victim into
executing the payload.

## Conclusion

Reports pointing out Gmail attachment filter bypasses are rarely accepted by
Google VRP. As always, a realistic attack scenario and the affected user base
are taken into consideration when evaluating this kind of report.
