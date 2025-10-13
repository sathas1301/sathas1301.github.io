---
title: "What the TUF is gittuf"
date: 2025-10-06 10:00:00 +1000
categories: [Blog]
tags: [gittuf, git, supplychainsecurity, tuf]
comments: true
---


gittuf is a security layer for git which adapts TUF(The Update Framework) features

---
**TUF**  
- Secures software update/download process
- key distribution, rotation and revocation
- role-based delegations

**Why gittuf?**  
- Remove single source of trust on git server  
- Independently verify policies without trusting forge   
- Verifiable way to authenticate developers - Already there in git  
- log of repo activity - not git log - who pushed what to which part of repo - Repository policy - verifiable and transparent representation of repo policy  
- Policy protections usually built on top of repository by forges like github/gitlab but not into repo, hence gittuf to resuce 

**What it provides**  
- Repository Activity
- reference
- refs/gittuf/reference-state-log
- every commit is signed and recorded
- Repository policy
- reference - refs/gittuf/policy
- tracked by RSL - singed policy metadata
- branch, tag, file, folder protection
- Key management

**Main concepts**  
- Root of Trust: Main key which controls delegations and key rotation
- Delegations: Allows root or policy role the ability to delegate authority
- Thresholds Signatures: Min number of signatures required for a git commit, merge or release which prevents single point failure.
- Policy file: Contains rules for branch, tags, merges, etc
- Reference state log: Append only record of repo state over time
- Rules: Are conditions for a git action defined in policy file
- Attestation: It is a signed statement about a git object

**Use cases**  
- Audit projects for policies set by forges by enabling gittuf
- Protect critical branches by defining rules which prevents malicious pushes
- Role based controls
- Release artifacts verifiability
- Key rotation when compromised
