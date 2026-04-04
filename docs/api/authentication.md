# Authentication

Maysano uses session-based authentication. Users authenticate once through login, and subsequent API requests are authorized through session cookies.

---

## Authentication Flow

1. **Register** — Create a new account with email and password.
2. **Login** — Authenticate with email and password to establish a session.
3. **Session** — The server issues a session cookie that authenticates subsequent requests.
4. **Logout** — Destroy the session and invalidate the cookie.

---

## Auth Endpoints

| Method | Endpoint | Description | Auth Required |
|---|---|---|---|
| `POST` | `/api/register` | Create a new user account | No |
| `POST` | `/api/login` | Authenticate and create session | No |
| `POST` | `/api/logout` | Destroy current session | Yes |
| `GET` | `/api/user` | Get current authenticated user | Yes |
| `POST` | `/api/change-password` | Change password for current user | Yes |

---

## Registration

Create a new account by providing:

| Field | Required | Description |
|---|---|---|
| `email` | Yes | Email address (must be unique) |
| `password` | Yes | Password (hashed before storage) |
| `firstName` | No | User's first name |
| `lastName` | No | User's last name |

On success, the user is automatically logged in and a session is established.

---

## Login

Authenticate with email and password. On success:

- A server-side session is created in the PostgreSQL session store.
- A session cookie is set in the response.
- The session cookie is included automatically in all subsequent requests from the browser.

---

## Password Management

Password changes require:

| Field | Description |
|---|---|
| `currentPassword` | The user's current password (for verification) |
| `newPassword` | The desired new password |

Passwords are hashed before storage. The platform never stores or transmits plaintext passwords.

---

## Protected Endpoints

All `/api/*` endpoints except registration, login, and public routes require a valid session. Requests without a valid session cookie receive a `401 Unauthorized` response.

The `isAuthenticated` middleware verifies the session on every protected request.

---

## Session Management

Sessions are stored in PostgreSQL using `connect-pg-simple`. This ensures:

- Sessions persist across server restarts.
- Sessions can be managed (listed, invalidated) through the database.
- Session data is server-side — the cookie contains only the session ID.

---

## What Authentication Does Not Cover

- **OAuth/OIDC for API consumers.** The current authentication model is designed for platform users, not for programmatic API consumers.
- **API keys.** The platform does not currently issue API keys for external integrations.
- **Multi-factor authentication (MFA).** MFA is not currently implemented.
- **Single sign-on (SSO).** SSO integration is not included in the base platform.
