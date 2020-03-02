## Config SSH - Yubikey

Add these lines into ~/.restart-gpg-agent
```
#!/bin/bash
echo "kill gpg-agent"
code=0
while [ 1 -ne $code ]; do
	killall gpg-agent
	code=$?
	sleep 1
done
echo "kill ssh"
killall ssh
echo "kill ssh muxers"
for pid in `ps -ef | grep ssh | grep -v grep | awk '{print $2}'`; do
	kill $pid
done
echo "restart gpg-agent"
eval $(gpg-agent --daemon)
echo
echo "All done. Now unplug / replug the NEO token."
echo
```

Add these lines into ~/.zshrc
```
# Enable gpg-agent if it is not running
GPG_AGENT_SOCKET="${XDG_RUNTIME_DIR}/gnupg/S.gpg-agent.ssh"
if [ ! -S $GPG_AGENT_SOCKET ]; then
  gpg-agent --daemon >/dev/null 2>&1
  export GPG_TTY=$(tty)
fi

# Set SSH to use gpg-agent if it is configured to do so
GNUPGCONFIG=${GNUPGHOME:-"$HOME/.gnupg/gpg-agent.conf"}
if grep -q enable-ssh-support "$GNUPGCONFIG"; then
  unset SSH_AGENT_PID
  export SSH_AUTH_SOCK=$GPG_AGENT_SOCKET
fi
 
alias restart-gpg-agent="source ~/.restart-gpg-agent"
```
