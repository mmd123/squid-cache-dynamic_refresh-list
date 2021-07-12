# squid-cache-dynamic_refresh-list
List of dynamic_refresh patterns to use with squid3, and pfsense, I had a hard time finding things online, so I figured I'd make a collaborative github repo for just this purpose.

This list, is directly designed to be used with the pfsense squid package, however these refresh patterns should also work without using the pfsense specific squid package.
I am unable to confirm if they will work with a regular squid package on say ubuntu, however, because of the fact that these are directly designed for use with pfsense and squid together, but they should be the same formatting, so feel free to try if you so desire.

To use the custom refresh patten with squid in pfsense navigate to  
Services - Squid Proxy Server – Local Cache  
Clear Disk Cache NOW or else you may get issues (You must do this everytime you change the refresh patten)  
In Dynamic and Update Content enable Cache Dynamic Content  
Under Custom refresh_patterns paste in the refresh_patterns  
Save 

Sometimes the squid cache has to be reset if you have errors.
https://docs.netgate.com/pfsense/en/latest/troubleshooting/squid.html

squid -k shutdown
rm -rf /var/squid/cache
squid -z
squid
squid -k parse (look to see if there are errors in the custom refresh_patterns).

Note: Normally https content cannot be cache because the content is encrypted and therefore cannot be cached. You can try and cache https content using ssl a man in the middle attack however you may get connection issues.
