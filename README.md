# strongSwan_fail2ban
fail2ban configuration files for filtering bad strongSwan authentication attempts; Regexes are based on a IPSec RSA + XAUTH login scheme.

I needed to implement a mechanism for filtering authentications attempts to my personal VPN, and since no filters for strongSwan existed, i decided to share my work.

Not the best looking Regexes on the web, but they work just fine.

Note: Since the filter regexes are based on strongswan logs to /var/log/syslog, the verbosity of the charon daemon must be taken into account while setting the maxlines parameter on the fail2ban filter. The regexes used in this implementation are based on the following charon verbosity setting:

  charondebug ="cfg 2, ike 2, knl 3, net 2, esp 2, dmn 2, mgr 2"
