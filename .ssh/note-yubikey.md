### Key generation
To avoid differences with `ssh-keygen -K`, specify application to avoid key confusion
```bash
ssh-keygen -t ed25519-sk -O resident -O verify-required -O application=ssh:rink2025_solo1 -C "ssh:rink2025_solo1"
```

### Once
```bash
sudo apt install -y gnupg gnupg-agent scdaemon pcscd
ssh-keygen -K
```

### .bashrc
```bash
if [ "$SSH_AGENT_PID" = "" ]; then
        eval "$(ssh-agent -s)"
fi

function cleanup()
{
        eval "$(ssh-agent -k)"
}
trap cleanup EXIT
```

### Windows (gpg-agent.conf)
```
enable-ssh-support
enable-win32-openssh-support
use-standard-socket
default-cache-ttl 600
max-cache-ttl 7200
```
