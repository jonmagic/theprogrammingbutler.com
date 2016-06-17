---
layout: post
title: Make Asterisk use Gmail for emailing faxes
---

While [Asterisk](http://www.asterisk.org/) provides a simple way to
replace sendmail when sending voicemails, the incoming fax portion of
Asterisk is not so easily reconfigured. By studying how it handled an
incoming fax from the Asterisk <span class="caps"><span
class="caps">CLI</span> I</span> was able to find this perl script:
[/var/lib/asterisk/bin/fax-process.pl](https://gist.github.com/184641/ddea153508f3373cf2f99ac8ba79fe99ce6fc2fd).

This script uses Net::<span class="caps">SMTP</span> to send its faxes
as attachments via email. We (and by we I mean
[Daniel](http://www.behindlogic.com)) rewired the perl script to use
Net::<span class="caps">SMTP</span>::<span class="caps">SSL</span>
instead and made it work with gmail!

There were a few libraries I had to install via cpan:\

-   force install F/FL/<span
    class="caps">FLORA</span>/Net\_SSLeay.pm-1.30.tar.gz
-   install S/SU/<span class="caps">SULLR</span>/IO-Socket-<span
    class="caps">SSL</span>-1.30.tar.gz
-   install <span class="caps"><span
    class="caps">GBARR</span></span>/Authen-<span
    class="caps">SASL</span>-2.12.tar.gz
-   install C/CW/<span class="caps">CWEST</span>/Net-<span
    class="caps">SMTP</span>-<span class="caps">SSL</span>-1.01.tar.gz

And finally here is the rewritten script!
<http://gist.github.com/184654>
