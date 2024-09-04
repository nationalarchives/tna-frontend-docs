# Cookies

The principles of cookie handling are:

- Create cookies on the client side (apart from session cookies)
- Update cookies on the client side (apart from session cookies)
- Reject by default (don't assume acceptance and don't add tracking until after they agree)

## Policies

As standard we should use at least these three classes of cookies:

- `essential` - we don't need to ask permission for these
- `usage` - analytics, tracking, data gathering
- `settings` - configured options for the site (e.g. default results view or static light/dark mode)

## Process

### First visit

```mermaid
sequenceDiagram
    User->>Browser: Request page
    Browser->>Server: HTTP request with no cookies
    Server->>Browser: Rendered HTML with cookie banner and no analytics
    Browser->>User: Accept cookies?
    alt Accept
        User->>Browser: Accept cookies
        Browser->>Browser: Create cookie policy with all accepted
        Browser->>Browser: Add analytics code with JavaScript
    else Reject
        User->>Browser: Reject cookies
        Browser->>Browser: Create cookie policy with all rejected
    end
    opt Next request
        User->>Browser: Request page
        Browser->>Server: HTTP request with cookie policy
        Server->>Browser: Rendered HTML with analytics but no cookie banner
    end
```

### Repeat visit

```mermaid
sequenceDiagram
    User->>Browser: Request page
    Browser->>Server: HTTP request with cookie policy
    Server->>Browser: Rendered HTML with analytics but no cookie banner
```

## Cookie library

When you load in the tna-frontend JavaScript, it comes with a [cookie library](https://github.com/nationalarchives/tna-frontend/blob/main/src/nationalarchives/lib/cookies.mjs).

This is loaded into the `window` object as `TNAFrontend.Cookies`:

```JavaScript
// Initialise a new Cookie instance
const cookies = new TNAFrontend.Cookies();

// Log all the cookies to the console
console.log(cookies.all);
```

### Functions

- `cookies.all` - Returns all the cookies
- `cookies.exists(key)` - Returns `true` if a cookie exists with the name `key`
- `cookies.hasValue(key, value)` - Returns `true` if the cookie with the name `key` is equal to `value`
- `cookies.get(key)` - Returns the cookie with the name `key`
- `cookies.set(key, value, maxAge, path)` - Set a cookie (max age default is one year, default path is `/`)
- `cookies.delete(key)` - Deletes the cookie with the name `key`
- `cookies.allPolicies` - Returns all the cookie policies
- `cookies.acceptPolicy(policy)` - Accepts the policy with the name `policy`
- `cookies.rejectPolicy(policy)` - Rejects the policy with the name `policy`
- `cookies.setPolicy(policy, accepted)` - Accepts or rejects the policy with the name `policy` depending on the value of `accepted`
- `cookies.acceptAllPolicies()` - Accepts all policies
- `cookies.rejectAllPolicies()` - Rejects all policies
- `cookies.isPolicyAccepted(policy)` - Returns `true` or `false` depending on whether the policy has been accepted
