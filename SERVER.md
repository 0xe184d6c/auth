# XFT AUTH SERVER

### DEPENDENCIES
```
npm install express jsonwebtoken body-parser firebase firebase-admin cookie-parser cors express-session
```


### FLOW
1. User clicks login on xft.finance
2. Redirects to auth.xft.finance
3. User authenticates with Google
4. Sets secure cross-domain cookie
5. Redirects back to xft.finance
6. Main site verifies session with auth server

