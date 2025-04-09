# XFT AUTH SERVER


### SEQUENCE
1. User visits Website A.
2. Website A redirects to Auth Server login.
3. User enters credentials on Auth Server.
4. Auth Server verifies, issues JWT, redirects to callback.
5. Website A validates JWT and sets session.
6. For Website B, existing Auth Server session reissues JWT for access.



### SYSTEM DESIGN




```mermaid
graph LR
    subgraph "Auth Server"
        Auth_Backend[Auth Backend]
        User_Database[User Database]
        Auth_Backend --> User_Database
    end

    subgraph "Website A"
        WebsiteA_Frontend[Frontend]
        WebsiteA_Backend[Backend]
        WebsiteA_Frontend --> WebsiteA_Backend
    end

    subgraph "Website B"
        WebsiteB_Frontend[Frontend]
        WebsiteB_Backend[Backend]
        WebsiteB_Frontend --> WebsiteB_Backend
    end

    Browser --> WebsiteA_Frontend
    Browser --> WebsiteB_Frontend
    Browser --> Auth_Backend
    WebsiteA_Backend --> Auth_Backend
    WebsiteB_Backend --> Auth_Backend
```

```mermaid
graph LR
    Browser -->|Click Sign Up| Website[Website]
    Website -->|Redirect with callback| Auth_Server[auth.xft.finance]
    Auth_Server -->|Serve Login Page| Browser
    Auth_Server -->|Verify Credentials| User_DB[User Database]
    Auth_Server -->|Issue JWT| Browser
    Browser -->|Redirect with JWT| Website
    Website -->|Validate Token| Auth_Server
```

