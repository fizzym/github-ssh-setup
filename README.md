# github-ssh-setup


### Description
Instructions on how to set-up SSH keys on GitHub from Linux

### Instructions
1) Create keys using ed25519 encryption:
```
ssh-keygen -t ed25519 -C "username@hostname"
```
For ```hostname``` use the hostname which will be used to access with this key.

For filename of the key pair use ```id_encryption_username_github``` (i.e. ```~/home/fizzym/.ssh/id_ed25519_fizzym_github```)


2) Add keys to ssh-agent:
```
# Start the ssh-agent
eval "$(ssh-agent -s)"
# Add key to the agent
ssh-add ~/.ssh/id_ed25519_fizzym_github
```

3) Upload the ***PUBLIC*** key (not the private key):
```
xclip -selection clipboard -i ~/.ssh/id_ed25519_fizzym_github.pub 
```
Past the public key in the "Settings"->"SSH and GPG keys".

4) Reconfigure remote url in local repositories
```
git remote set-url origin git@github.com:[user_name]/[repository_name].git
```

You can now push and pull without requiring a password.
