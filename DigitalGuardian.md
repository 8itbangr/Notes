---
tags:
    - macos
    - .bash_profile
    - Digital Guardian
---

 # Disable/enable Digital Guardian

Usual symptom is that a search in VSCode locks machine up

In .bash_profile:
    alias dgstop='sudo /usr/local/dgagent/dgctl --stop --password=G1veM3Freed0m'
    alias dgstart='sudo /usr/local/dgagent/dgctl --start --password=G1veM3Freed0m'alias dgstop='sudo /usr/local/dgagent/dgctl --stop --password=G1veM3Freed0m'
    alias dgstart='sudo /usr/local/dgagent/dgctl --start --password=G1veM3Freed0m'
