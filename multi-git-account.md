## 1. Generate ssh key for new account
```
ssh-keygen -t rsa -C "phong.hd1989@gmail.com" -f "id_rsa_phonghd"
```

## 2. Add theses line into ~/.ssh/config

```
# main account
Host github.com
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_rsa

# secondary account
Host secondary.github.com
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_rsa_secondary
```
