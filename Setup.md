
```
ubuntu@ip-172-31-22-219:~$ export ARCH=$(case $(uname -m) in x86_64) echo -n amd64 ;; aarch64) echo -n arm64 ;; *) echo -n $(uname -m) ;; esac)
ubuntu@ip-172-31-22-219:~$ echo $ARCH
amd64

ubuntu@ip-172-31-22-219:~$ export OS=$(uname | awk '{print tolower($0)}')
ubuntu@ip-172-31-22-219:~$ echo $OS
linux

ubuntu@ip-172-31-22-219:~$ echo $OPERATOR_SDK_DL_URL
https://github.com/operator-framework/operator-sdk/releases/download/v1.15.0

ubuntu@ip-172-31-22-219:~$ curl -LO ${OPERATOR_SDK_DL_URL}/operator-sdk_${OS}_${ARCH}
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   663  100   663    0     0   5618      0 --:--:-- --:--:-- --:--:--  5618
100 73.6M  100 73.6M    0     0  56.3M      0  0:00:01  0:00:01 --:--:-- 74.8M

ubuntu@ip-172-31-22-219:~$ gpg --keyserver keyserver.ubuntu.com --recv-keys 052996E2A20B5C7E
gpg: keybox '/home/ubuntu/.gnupg/pubring.kbx' created
gpg: /home/ubuntu/.gnupg/trustdb.gpg: trustdb created
gpg: key 052996E2A20B5C7E: public key "Operator SDK (release) <cncf-operator-sdk@cncf.io>" imported
gpg: Total number processed: 1
gpg:               imported: 1

ubuntu@ip-172-31-22-219:~$ curl -LO ${OPERATOR_SDK_DL_URL}/checksums.txt
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   652  100   652    0     0   5174      0 --:--:-- --:--:-- --:--:--  5174
100  1399  100  1399    0     0   7402      0 --:--:-- --:--:-- --:--:--  7402

ubuntu@ip-172-31-22-219:~$ grep operator-sdk_${OS}_${ARCH} checksums.txt | sha256sum -c -
operator-sdk_linux_amd64: OK
ubuntu@ip-172-31-22-219:~$ chmod +x operator-sdk_${OS}_${ARCH} && sudo mv operator-sdk_${OS}_${ARCH} /usr/local/bin/operator-sdk

ubuntu@ip-172-31-22-219:~$ operator-sdk version
operator-sdk version: "v1.15.0", commit: "f6326e832a8a5e5453d0ad25e86714a0de2c0fc8", kubernetes version: "1.21", go version: "go1.16.10", GOOS: "linux", GOARCH: "amd64"


```

```
ubuntu@ip-172-31-22-219:~$ curl -LO https://go.dev/dl/go1.17.5.linux-amd64.tar.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    75  100    75    0     0    903      0 --:--:-- --:--:-- --:--:--   903
100  128M  100  128M    0     0  74.5M      0  0:00:01  0:00:01 --:--:-- 86.3M

ubuntu@ip-172-31-22-219:~$ ls -l go1.17.5.linux-amd64.tar.gz
-rw-rw-r-- 1 ubuntu ubuntu 134808667 Dec 19 08:57 go1.17.5.linux-amd64.tar.gz

root@ip-172-31-22-219:/home/ubuntu#  tar -C /usr/local -xzf go1.17.5.linux-amd64.tar.gz
root@ip-172-31-22-219:/usr/bin# export PATH=$PATH:/usr/local/go/bin
root@ip-172-31-22-219:/usr/bin# go version
go version go1.17.5 linux/amd64


```
