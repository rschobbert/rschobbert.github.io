---
title: "Passing REMOTE_USER to application after authenticating with apache basic authentication"
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - apache
  - authentication
  - configuration
---

In this post, I document a small issue we had on a customer site, where parts of an application is authenticated with file based basic authentication, and we needed to pass the REMOTE_USER variable to a JSP page for further processing. As there is a lot of wrong or outdated information out there , I thought I quickly describe our issue and how I solved it.

<!--more-->

Further resources:
* [apache 2.4 docs](https://httpd.apache.org/docs/2.4/)

The problem was, that just by securing a location with basic authentication, the RequestHeader REMOTE_USER was not automatically added to the request. So I was looking for a way to achieve this in the <Location> block. I found a lot of examples with using mod_rewrite and rewriting the request. But that didn't work, at least not the way I tried.

Basically the site conf looked like this:
```apache
<VirtualHost 123.456.789.012:80>
        ServerName some.server.net
        DocumentRoot /var/www/html/

        <Location /restricted/check.php>
                AuthType Basic
                AuthBasicProvider file
                AuthUserFile /var/www/.mypasswd
                AuthName "BasicAuth"
                Require valid-user

                RequestHeader set REMOTE_USER expr=%{REMOTE_USER}
        </Location>
</VirtualHost>
```

