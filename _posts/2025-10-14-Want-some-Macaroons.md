---
title: "Want some Macaroons?"
date: 2025-10-14 10:00:00 +1000
categories: [Blog]
tags: [identity, appsec, tokens, macaroons, jwt, google]
comments: true
---

Sorry, you are not actually getting any macarons to eat here!   

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
`Macaroons` came and solved dynamic claim modification problem where single token can be used for multiple claims/restrictions which they call `caveats`.   
Imagine a single token being valid for multiple principals/identities, each service adds its own conditions/caveats which allows or denies access to the principals. This delegation is the main feature offered by Macaroons.   
Macaroon has a `Root Key` which is used for both issuing and verifying it and the caveats are signed and chained accordingly.

<mark>Don't get me wrong about statement about future. Token standard you want to use depends on the system and usecase you are working with, Macaroon cannot be the solution for every usecase. Also, there are a lot of emerging trends like Quantum-Resistant Tokens, AI-enhanced tokens</mark>.

To simplify,   
**JWT** is Static proof of who you are what you can do (Because JWT is used for both Authentication and Authorization)   
**Macaroons** are Dynamic proof of what you can do under all conditions (Macaroons is mainly for Authorization)    

## Problems   
Well, its not all rainbows and unicorns right!
- Same old token leakage issues
- As Macaroons are stateless, revocation is not straight forward
- Increase in token size as more caveats are added
- Biggest problem is the sharing of root key to verifiers, insecure sharing/storage can compromise the Macaroon.
