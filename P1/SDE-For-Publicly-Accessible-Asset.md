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

## Reports
- [Report1](https://hackerone.com/reports/1912671)
- [Report2](https://hackerone.com/reports/1153817)
- [Report3](https://hackerone.com/reports/273726)
- [Report4](https://hackerone.com/reports/775123)

##### Reminder
Have to link a fuzzing wordlist latter
