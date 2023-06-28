# Broken Authentication And Session Management
## Focus Area
- O Auth
- JWT
- Login Form
- Forgot Password
- Broken Implimentation

### O-AUth
- Typical O- AUth Flow

```python
from flask import Flask, redirect, url_for, request, session
from google.auth.transport import requests
from google.oauth2 import id_token

app = Flask(__name__)
app.secret_key = 'your_secret_key'  

CLIENT_ID = 'your_client_id'  
REDIRECT_URI = 'http://localhost:5000/callback'  

@app.route('/')
def home():
    return 'Welcome to the homepage!'

@app.route('/login')
def login():
   
    authorization_url, state = requests.authorization_url(
        'https://accounts.google.com/o/oauth2/v2/auth',
        access_type='offline',
        prompt='consent',
        client_id=CLIENT_ID,
        redirect_uri=REDIRECT_URI,
        scope=['openid', 'email', 'profile']
    )

    # Store the state in the session for validation later
    session['state'] = state

    # Redirect the user to the authorization URL
    return redirect(authorization_url)

# Route for handling the Google OAuth callback
@app.route('/callback')
def callback():
    # Validate the state to prevent CSRF attacks
    if request.args.get('state') != session['state']:
        return 'Invalid state parameter', 400

    # Exchange the authorization code for an access token
    token = requests.fetch_token(
        'https://accounts.google.com/o/oauth2/token',
        client_secret='your_client_secret',  # Replace with your own client secret
        authorization_response=request.url,
        redirect_uri=REDIRECT_URI
    )

    # Verify the ID token to get the user's information
    idinfo = id_token.verify_oauth2_token(
        token['id_token'], requests.Request(), CLIENT_ID
    )

    # Store the user's information in the session or authenticate the user
    session['user_id'] = idinfo['sub']
    session['email'] = idinfo['email']

    # Redirect the user to a protected page or perform any other required actions
    return redirect(url_for('protected'))

# Route for a protected page that requires authentication
@app.route('/protected')
def protected():
    # Check if the user is authenticated
    if 'user_id' in session:
        return f'Hello, {session["email"]}! This is a protected page.'
    else:
        return 'You are not authenticated.'

# Route for logging out
@app.route('/logout')
def logout():
    # Clear the session data
    session.clear()
    return 'You have been logged out.'

if __name__ == '__main__':
    app.run(debug=True)

```

### O-Auth Issues
-Improper validation of redirect URI
```bash
[x] Is Subdomain Allowed
[X] Is There Any Open Redirect Flaws
[X] Is There Any Xss Flaws
[X] If There is any flaw can that endpoing be used to steal token
[x] Any external link is leaking the token ? eg : image loading , script loading
```
- CSRF
  ```bash
[x] Is there any account squatting issue using O-auth
[X] Can i use my incomplete o auth flow to trigger victim into Linking his account
```
- Account Squatting
```bash
  [X] If i sign up using victim email and then he signs up using O-Auth can i access his account again
```
- Reusability of an OAuth access token
  ```bash
  [X] Complete O- auth Flow  Then Using same access token after logging out
```
- Is there anything controlleble from client side


### Commo JWT Attcks
- None ALgo
- Algo Confusion
- 

### Login Form
- Rate Limit
- Weak Login Function
- SQL i and NosqlI and ldap
- FOrced Browsing Try to go directly to the dashboard URL without solving the 2FA. If not success try adding the referral header to the 2FA page url while going to dashboard.
- Parameter Pollution
- Break Authentication Flow / Response manipulation

### Forgot Passwd
- OTP Bruteforce
- Token Predictibility
- Weak Cryptography
- Link Is valid even after email change
- COde Leaked In Response


## Session
- No Session Validation After Any Change (Logout, Reset Passwd , ETc)
- Same session assigned after login 
- predict Session ID
- Same Looking Application - Create and login in one app use cookie in 2nd app
- Use multiple session id in cookie

## Broken Implimentation
- Enable 2fa doesn't expire previous session
- Password Can Be Reset Without 2Fa
- No 2FA required for disabling 2FA.
-  After login to victim's account, generate the backup code generation request from your browser. You may able to get the backup codes of victim.
-  Create an account with victim@gmail.com (If there is no email verification). Now enable 2FA in the account. So now victim can't create an account.



#### Links 
```bash
https://book.hacktricks.xyz/pentesting-web/login-bypass
https://book.hacktricks.xyz/pentesting-web/login-bypass/sql-login-bypass
https://medium.com/@surendirans7777/2fa-bypass-techniques-32ec135fb7fe

```

