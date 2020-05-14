# strongSwan_fail2ban

fail2ban configuration files for filtering bad strongSwan authentication attempts; Regexes are based on a IPSec RSA + XAUTH login scheme (strongswan_ikev1, employed for legacy iOS devices) and a more modern and robust scenario based on RSA pubkey and EAP-TLS login scheme (strongswan_ikev2).

I needed to implement a mechanism for filtering authentications attempts to my personal VPN, and since no filters for strongSwan existed, i decided to share my work.

Not the best looking Regexes on the web, but they work just fine and should take care of almost all different login attempt scenarios (mismatched certificate, mismatched protocol, wrong PSK, etc).

Note 1: The filters parse logs saved by strongswan on a custom log file (/var/log/charon/charon.log); this was made with the scope of preventing too much spam to syslog, and also for robustness of fail2ban filter itself. Creating a separate logfile for strongswan (remembering to include it in the strongswan apparmor profile, to prevent 'permission denied' errors) is highly encouraged. 

Note 2: Since the filter regexes are based on strongswan logs to /var/log/charon/charon.log, the verbosity of the charon daemon must be taken into account while setting the maxlines parameter on the fail2ban filter. The regexes used in this implementation are based on the following charon verbosity setting:

  charondebug ="cfg 0, ike 2, knl 2, net 2, esp 2, dmn 2, mgr 2"
  
Note 3: English is not my main language, i apologize for eventual errors or if this readme is hard to read.

All feedback is appreciated.
