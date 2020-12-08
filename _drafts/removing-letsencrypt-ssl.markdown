---
title: "Removing letsencrypt for domains"
layout: post
date: 2020-12-07
categories: devops dns ssl
---


### Removing letsencryp ssl for domains



```
rm -rf /etc/letsencrypt/live/${DOMAIN}
rm -rf /etc/letsencrypt/renewal/${DOMAIN}.conf
rm -rf /etc/letsencrypt/archive/${DOMAIN}
```


### In case apache2 stops working

```
apachectl stop
/etc/init.d/apache2 start
```
