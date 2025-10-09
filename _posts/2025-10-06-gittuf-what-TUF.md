---
title: "Everything I understood about gittuf(WIP)"
date: 2025-10-06 10:00:00 +1000
categories: [Blog]
tags: [gittuf, git, supplychainsecurity, tuf]
comments: true
---

**Why?**
Remove single source of trust on git server
Independently verify policies without trusting forge
verifiable way to authenticate developers - Already there in git
log of repo activity - not git log - who pushed what to which part of repo - **Reference state log**
Repository policy - verifiable and transparent representation of repo policy
policy protections built on top of repository by froges like github/gitlab but not into repo

**What it provides**
Repository Activity
-> reference - refs/gittuf/reference-state-log
every commit is signed and recorded
Repository policy
-> reference - refs/gittug/policy
tracked by RSL - singed policy metadata
branch, tag, file, folder protection
Key management

**Main concepts**
Root of Trust
delegations - ability to grant trust for a namespace
Thresholds - min number of signatures
signing key
policy file
reference state log
rules

**Use cases**
-> Audit projects for failed policies set by forges by enabling gittuf
-> Protect critical branches by defining rules which prevents malicious pushes

**TUF**
key distribution, rotation and revocation
delegations
