RANCID Scripts for EdgeOS by Ubiquiti
======

Ubiquiti scripts for Rancid.  Forked from
https://bitbucket.org/aquerubin/rancid-vyatta
https://github.com/damianfantini/rancid and
https://github.com/natecarlson/vyatta-rancid

Vyatta is almost the same as EdgeOS... but not quite, hence the fork.

Includes:

* vlogin - basic login script, confirmed to work with EdgeOS
* vyos.pm - the Rancid wrapper module to actually grab the configs
* rancid.types.conf - additional device type configuration

To integrate into your RANCID install:

* Copy vlogin to your 'bin' directory
* Copy vyos.pm to your PERL5LIB rancid directory
* Append rancid.types.conf to your existing rancid.types.conf file (or create it if it doesn't exist)
* Add a new device to your 'router.db', with the vendor of 'vyos'
* NOTE: You may have to go through the painful process of updating your Perl Installations Socket module to use this package if you are running on RedHat / CentOS 6. If you get a strange error in your rancid error logs like: 
"inet_pton" is not exported by the Socket module
That means that you'll need to update Socket.
* Also, the timing on password authentication is spotty at best, I recommend working around this by using key-based SSH auth on your EdgeOS routers. You then can put entries in your .cloginrc like the below:
add user HOST rancid 
add password HOST FAKEPASSNOTUSED
add method HOST ssh
