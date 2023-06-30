# Sensitive Data Exposure For Publicly Accessible Asset
## How to test
- Check for sensitive data in cookie fields
- Tokens that are leaked publicly
- Passwords disclosed in JS files
- Access to the sensitive API calls without proper authorization
- PII and Health records publicly available
- password database uses unsalted hashes
- Check for pages that contain sensitive information being cached
- Unencrypted communication on login pages
- Endpoint Related To Used CMS/Framework
- Use Github Dorking Or GitRob Tool
- Use Google Dorking

## Reports
- [Report1](https://hackerone.com/reports/1912671)
- [Report2](https://hackerone.com/reports/1153817)
- [Report3](https://hackerone.com/reports/273726)
- [Report4](https://hackerone.com/reports/775123)

## Some Google Dorks
- site:docs.google.com inurl:"/d/" "example.com"
- site:onedrive.live.com "example.com"
- site:dropbox.com/s "example.com"
- site:box.com/s "example.com"
- site:dev.azure.com "example.com"
- site:http://sharepoint.com "example.com"
- site:digitaloceanspaces.com "example.com"
- site:firebaseio.com "example"
- site:jfrog.io "example"
- site:http://s3-external-1.amazonaws.com "example.com"
- site:http://s3.dualstack.us-east-1.amazonaws.com "example.com"
- site:pastebin.com
- site:jsfiddle.net
- site:codebeautify.org
- site:codepen.io "tesla.com"
#### [More Dorks](https://github.com/TakSec/google-dorks-bug-bounty)
##### Reminder
Have to link a fuzzing wordlist latter
