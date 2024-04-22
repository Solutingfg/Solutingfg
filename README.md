- 👋 Hi, I’m @Solutingfg
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Solutingfg/Solutingfg is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

# HOWTO Configure Git with proxy

## Git Configuration
```
git config --global http.proxy http://<USERNAME>@<PROXY_FQDN>:<PROXY_PORT>
git config --global http.https://github.com.sslVerify false
git config --global credential.<PROXY_FQDN>.provider github
```

To get ride of "warning: auto-detection of host provider took too long (>2000ms)"
> git config --global credential.<PROXY_FQDN>.provider github

## Or local repo configuration
```
git config --local http.proxy http://<USERNAME>@<PROXY_FQDN>:<PROXY_PORT>
git config --local http.https://github.com.sslVerify false
git config --local credential.<PROXY_FQDN>.provider github
```

## ~~HTTPS not needed~~
```
#git config --global https.proxy http://<USERNAME>@<PROXY_FQDN>:<PROXY_PORT>
#git config --global credential.github.com.provider github
```

# OR

## Environment :
```
export HTTPS_PROXY=http://<USERNAME>@<PROXY_FQDN>:<PROXY_PORT>
export GIT_SSL_NO_VERIFY=true
```

## Check Config
```
git config -l --show-scope
git config -l --show-origin
```

## TEST
### To speed up "warning: auto-detection of host provider took too long (>2000ms)"
```
git config --local credential.autoDetectTimeout 100
git config --unset credential.autoDetectTimeout
```

### .gitconfig
```
[http]
	proxy = http://<USERNAME>@<PROXY_FQDN>:<PROXY_PORT>
[http "https://github.com"]
	sslVerify = false
[credential "<PROXY_FQDN>"]
	provider = github
```
