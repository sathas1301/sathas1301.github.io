---
title: "subdomain takeover"
date: 2025-09-30 10:00:00 +1000
categories: [Blog]
tags: [introduction, appsec, cloudsecurity, bugbounty]
comments: true
---

Recently I have came across this issue and found out that this is not as complex as it sounds. 

# Why and how it happens?**
Did you set an **A, CNAME,MX,NS or TXT** record for a domain which is tied to a resource and forgot about it when migrated away?

---
In simple terms there is no resource tied to the record for DNS record, guess what can happen -> attacker creates that resource and uses that domain to serve what ever he want.

# examples: 
There is a subdomain **test.abc.com** which a company used for GitHub pages and removed pages later. Now an attacker checks this domain and finds that there is nothing being served for test.abc.com, and uses the custom domain to host his own GitHub pages. That's all the attack is. Now its up to his imagination how he reap benefits from it.
---
Check this beautiful repository  https://github.com/EdOve rflow/can-i-take-over-xyz to find if a service is vulnerable or not

Doing bug bounty and want an automated way - refer https://github.com/yahoo/SubdomainSleuth - Nothing works 100% so check for false positives or create your own automation tool.

