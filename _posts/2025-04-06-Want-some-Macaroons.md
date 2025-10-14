---
title: "Want some Macaroons? (WIP)"
date: 2025-14-10 10:00:00 +1000
categories: [Blog]
tags: [introduction, appsec, cloudsecurity]
comments: true
---

Sorry, you are not actually getting any macarons here!   

What I want to discuss here is the `Macaroons` which are tokens used for authorization. You immediately think that there are already JWTs for it why create something new again!   

Its not me, blame Google for it :)     

For us to understand why there is a new authorization token standard, we have to go back to the old days.   

## Long back
Once up on a time there used be a `Client & Server` and a login page where user logs in and client(browser) gets a session ID which is stored in cookie and sent to server for every request.   

**Problem**: With microservices and complex network architectures on the backend, sharing the session information across servers is a challenge.

## Contemporary
Then came along `JWTs` which introduced **stateless authentication** where any server can just verify the token with public key.   

**Problem**: Once JWT token is issued, it cannot be change the claims done by client dynamically unless a new token is minted by Auth server.

## Future
`Macaroons` came and solve dynamic claim modification problem where single token can be used for multiple claims/restrictions which they call `caveats`.   
Imagine a single token being valid for multiple services access, each service adds its own conditions/caveats which allows or denies access.

To simplify,   
**JWT**= Static proof of who you are what you can do (Because JWT is used for both Authentication and Authorization)   
**Macaroons**= Dynamic proof of what you can do under all conditions (Macaroons is mainly for Authorization)    

## Examples
