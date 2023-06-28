# Server Side Misconfiguration Use Of Default Credentials
- It is a misconfiguration where you just have to check which framework is used.
- Then check that framework's default credentials from documentation
- Now Try To log In


# How to find and exploit
- Same Domain / Subdomain But Different Port
- Same Domain / Subdomain But Different Endpoint
- May Be Ip Address 
- Valid Endpoint Or Resource From Wayback

```bash
cat alive-subd.txt | gau | anew urls.txt
cat alive-subd.txt | waybackurls | anew urls.txt
cat alive-subs.txt | hakrawler | anew urls.txt
httpx -l alive-sub.txt -p 22,25,80,443,3306 -probe | anew check-them.txt
cat urls.txt | grep -f scope.txt | httpx -fc 404 | anew alivelinks.txt # Some urls might be out of scope
cat alivelinks.txt | httpx -ss -srd screenshots # Now CHeck Them Manually
cat check-them.txt | httpx -ss -srd screenshots
```


# Now Found Some Login Pages WHat Next
- Intruder + Wordlist
- Now or unknown software ? Check Documentation
###  [Default Credential Wordlist](https://github.com/danielmiessler/SecLists/tree/master/Passwords/Default-Credentials)
