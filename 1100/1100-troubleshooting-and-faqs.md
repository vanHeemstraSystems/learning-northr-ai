# 1100 — Troubleshooting and FAQs

Practical “when it breaks” notes for northr.ai.

---

## Google Calendar integration fails with: “Edge function returned a non 2xx return status”

This usually means the frontend called a backend “edge function” (often for OAuth token exchange / calendar sync),
and the backend returned an error. The UI message is generic — you need the **actual response body** to know why.

### 1) Get the real error message (fastest path)

In your browser (Chrome/Edge/Brave):

1. Open northr.ai
2. Open DevTools:
   - Mac: `Cmd` + `Option` + `I`
3. Go to **Network**
4. Retry connecting Google Calendar
5. Click the **failed request** (red)
6. Inspect:
   - **Status code** (401/403/429/500)
   - **Response/Preview** (often contains JSON like `{"error": "...", "message": "...", "code": "..."}`)
   - **Request URL** and any **Request ID** header (if present)

If the response body mentions things like `invalid_grant`, `redirect_uri_mismatch`, `access_denied`,
`rate_limit`, or `token expired`, jump to the matching fix below.

### 2) Common fixes (most likely first)

- **Popups blocked**
  - Allow popups for northr.ai and retry the connect flow.
- **Third-party cookies blocked**
  - Temporarily allow third‑party cookies (or add an exception for northr.ai) and retry.
- **Extensions interfering**
  - Disable ad blockers / privacy extensions (uBlock, Ghostery, Brave Shields) for northr.ai.
  - Retry in an Incognito/Private window with extensions disabled.
- **Multiple Google accounts**
  - Log out of extra Google accounts (or use an Incognito window).
  - Retry, ensuring you pick the correct account (`wvanheemstra@googlemail.com`).
- **Permissions not granted**
  - If you denied access during OAuth, remove the app from your Google account permissions and reconnect:
    - Google Account → **Security** → **Third‑party access** → remove northr.ai (wording may vary)
- **Corporate/VPN/network filtering**
  - Try from a different network (mobile hotspot) or disable VPN temporarily.

### 2a) Specific case: `{"error":"No organization membership found"}` (HTTP 400)

If the failed request returns a JSON error like:

```json
{"error":"No organization membership found"}
```

This is **not** a Google OAuth problem. It means northr.ai’s backend doesn’t see your user as belonging to any
organization/workspace context required for the integration (often shown as `context: "work_readonly"` in the payload).

**Fix:**

1. In northr.ai, go to **Settings** (or your profile menu).
2. Look for **Organization / Workspace / Team**.
3. Do one of the following:
   - **Create a workspace/organization** (solo workspace counts), or
   - **Accept an invite** to an existing workspace/organization, or
   - **Switch workspace** to the one you intended to use for integrations.
4. After you have an active workspace/org selected, retry **Settings → Integrations → Google Calendar**.

**Also check for account mismatch:**

- If you’re logged into northr.ai with one email (e.g. your auth session) but connecting Google Calendar with another,
  try logging out and logging back in using the account you want as your primary (then reconnect).

**When contacting support, include:**

- The request URL (often ends in something like `/functions/v1/nango-auth-callback`)
- The timestamp
- The `sb-request-id` response header value (request ID)

### 3) What it means for your planning

- Without the integration working, northr.ai cannot reliably **see calendar constraints**.
- Workaround: you can still schedule via Google Calendar manually and keep your weekly plan in Git.

### 4) Workaround (keeps momentum)

Import `.ics` time blocks into Google Calendar and treat them as your “source of truth” for time blocks:

- Example: `plan/week/2026-03-10-document-northrai-github.ics`

Then (in northr.ai), make sure the **task/outcome** exists and you do a **check-in** to drive adaptation.

---

## Creating a schedule entry fails (Save) with HTTP 500 and `PostgREST; error=42P17`

Symptom:

- You can **connect** Google Calendar successfully, but when you try to **add a schedule event** in northr.ai (e.g. Monday 08:00–08:15 “Breakfast”) and click **Save**, it fails.
- In DevTools → Network, the failing request looks like:
  - `POST /rest/v1/family_schedules?select=*`
  - **500 Internal Server Error**
  - Response header: `proxy-status: PostgREST; error=42P17`

Interpretation:

- This is a **backend/database** failure in northr.ai’s API layer (PostgREST/Supabase), not an OAuth/Google Calendar issue.

Workarounds (keep moving):

- Create the event directly in **Google Calendar** (or import an `.ics` from this repo) and let northr.ai treat it as a **calendar constraint** (busy time).
- If you need “Breakfast” as a recurring block, create it as a recurring Google Calendar event in the **Northr** calendar.

When contacting support, include:

- Request URL (example): `.../rest/v1/family_schedules?select=*`
- Status: **500**
- `proxy-status: PostgREST; error=42P17`
- The **`sb-request-id`** response header value (example you saw: `019cd859-b4a8-7b86-b973-641606aa7881`)

---

## Next

→ See the [repository README](../README.md) for the full learning path.
