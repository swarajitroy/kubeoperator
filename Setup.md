
```
ubuntu@ip-172-31-22-219:~$ export ARCH=$(case $(uname -m) in x86_64) echo -n amd64 ;; aarch64) echo -n arm64 ;; *) echo -n $(uname -m) ;; esac)
ubuntu@ip-172-31-22-219:~$ echo $ARCH
amd64

ubuntu@ip-172-31-22-219:~$ export OS=$(uname | awk '{print tolower($0)}')
ubuntu@ip-172-31-22-219:~$ echo $OS
linux


```
