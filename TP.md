# Practical work

## Mail Transfer agent

The goal of this practical work is to send a mail to a remote domain using postix.

### Question 1 : setUp

Create 3 machine, with static IP on a private intern network.

 - server-dns-mail-1
 - server-mail-2
 - client

### Question 2 : DNS

On *server-dns-mail-1*  :

 - install **bind9**
 - Edit configuration so that it forwards requests to *8.8.8.8*
 - Add zone *domaina.com*
 - Add zone *domainb.com*
 - NS entry for each zone is *server-dns-mail-1*
 - MX for zone *domaina.com* is *server-dns-mail-1*
 - Domain name for *server-dns-mail-1* is *mx.domaina.com*
 - MX for zone *domainb.com* is *server-mail-2*
 - Domain name for *server-dns-mail-2* is *mx.domainb.com*
 - configure your three servers to use *server-dns-mail-1* as a DNS server (editing */etc/resolv.conf*)

### Question 3 : Postfix

Install **postfix** on *server-dns-mail-1* and *server-mail-2*

 - *server-dns-mail-1* should manage mails for *domaina.com*
 - *server-mail-2* should manage mails for *domainb.com*

Add a local user named *user* on each server.

### Question 4 : Sending the mail

On client, send a mail to *user@domaina.com* uing *user@domainb.com* as a FROM address and transiting threw *mx.domainb.com* 

### Question 5 : Installing Cyrus

Install Cyrus on **server-mail-2**. You should be able to access your mails as user@domainb.com.

Install **roundcube** on server-mail-2 and access your IMAP mails threw it.
