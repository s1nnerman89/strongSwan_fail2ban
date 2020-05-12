# strongSwan_fail2ban
fail2ban configuration files for filtering bad strongSwan authentication attempts; Regexes are based on a IPSec RSA + XAUTH login scheme.

I needed to implement a mechanism for filtering authentications attempts to my personal VPN, and since no filters for strongSwan existed, i decided to share my work.

Not the best looking Regexes on the web, but they work just fine.
