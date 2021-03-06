What's Parsero?
===============
Parsero is a free script written in Python which reads the Robots.txt
file of a web server and looks at the Disallow entries. The Disallow
entries tell the search engines what directories or files hosted on a
web server mustn't be indexed. For example, "Disallow: /portal/login"
means that the content on www.example.com/portal/login it's not allowed
to be indexed by crawlers like Google, Bing, Yahoo... This is the way
the administrator have to not share sensitive or private information
with the search engines.

But sometimes these paths typed in the Disallows entries are directly
accessible by the users without using a search engine, just visiting
the URL and the Path, and sometimes they are not available to be visited
by anybody. Because it is really common that the administrators write
a lot of Disallows and some of them are available and some of them are
not, you can use Parsero in order to check the HTTP status code of each
Disallow entry in order to check automatically if these directories are
available or not.

Also, the fact the administrator write a robots.txt, it doesn't mean
that the files or directories typed in the Dissallow entries will not
be indexed by Bing, Google, Yahoo, etc. For this reason, Parsero is
capable of searching in Bing to locate content indexed without the web
administrator authorization. Parsero will check the HTTP status code in
the same way for each Bing result.

When you execute Parsero, you can see the HTTP status codes. For example,
the codes bellow:

    200 OK          The request has succeeded.
    403 Forbidden   The server understood the request, but is refusing to fulfill it.
    404 Not Found   The server hasn't found anything matching the Request-URI.
    302 Found       The requested resource resides temporarily under a different URI.
    ...

You can get all the latest info about Parsero from 
http://www.behindthefirewalls.com/search/?q=parsero

Installing
==========
There are three ways to install Parsero easily. 

By using setup.py script

	sudo setup.py install
	
By using pip3

	sudo apt-get install python3-pip
	sudo pip3 install parsero
	
In Kali Linux

	sudo apt-get update
	sudo apt-get install parsero


Usage
=====

    $ parsero -h
        
    usage: parsero.py [-h] [-u URL] [-o] [-sb]
	
    optional arguments:
    -h, --help  show this help message and exit
    -u URL      Type the URL which will be analyzed
    -o          Show only the "HTTP 200" status code
    -sb         Search in Bing indexed Disallows
    -f FILE     Scan a list of domains from a list

Example
=======
	 
    root@kali:~# parsero -u www.example.com -sb

         ____                               
        |  _ \ __ _ _ __ ___  ___ _ __ ___  
        | |_) / _` | '__/ __|/ _ \ '__/ _ \ 
        |  __/ (_| | |  \__ \  __/ | | (_) |
        |_|   \__,_|_|  |___/\___|_|  \___/ 

	Starting Parsero v0.75 (https://github.com/behindthefirewalls/Parsero) at 05/22/14 11:12:55
	Parsero scan report for example.com
	http://example.com/download.php 302 Moved Temporarily
	http://example.com/raw.php 302 Moved Temporarily
	http://example.com/embed_js.php 200 OK
	http://example.com/embed.php 200 OK
	http://example.com/print.php 302 Moved Temporarily
	http://example.com/diff.php 302 Moved Temporarily
	http://example.com/share.php 404 Not Found
	http://example.com/report.php 302 Moved Temporarily
	http://example.com/embed_iframe.php 200 OK
                                             
	[+] 9 links have been analyzed and 3 of them are available!!!
                                             
	Searching the Disallows entries in Bing
                                             
	http://www.bing.com/search?q=site:http://example.com/download.php
	http://www.bing.com/search?q=site:http://example.com/raw.php
 	- example.com/raw.php/contact?i=KR9c2erd 200 OK
 	- example.com/raw.php/legal.aspx 302 Moved Temporarily
 	- example.com/raw.php/points?i=KR9c2erd 200 OK
	- example.com/raw.php/image/sqrn11sp3C/zayn-tshirt-one-direction?i=... 302 Moved Temporarily
	http://www.bing.com/search?q=site:http://example.com/embed_js.php
	http://www.bing.com/search?q=site:http://example.com/embed.php
	http://www.bing.com/search?q=site:http://example.com/print.php
	http://www.bing.com/search?q=site:http://example.com/diff.php
	http://www.bing.com/search?q=site:http://example.com/share.php
	http://www.bing.com/search?q=site:http://example.com/report.php
	http://www.bing.com/search?q=site:http://example.com/embed_iframe.php
                                             
	Finished in 7.290362596511841 seconds 

Disclaimer
==========
The use of this tool is your responsability. Use parsero to audit your
own servers or servers you are allowed to scan. I hereby disclaim any
responsibility for actions taken with this tool.

Author
======

* Javier Nieto <javier.nieto at behindthefirewalls.com> 
* Twitter: @behindfirewalls
* Web: http://www.behindthefirewalls.com

Credits
=======
I'd like thank to @cor3dump3d from http://www.devconsole.info for his support
and help.
