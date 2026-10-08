# Sign in with Xi · how a house joins

Hunter, 2026-10-07: "Let's add this capability to the platform. The sign in with Google please. Don't lock anyone out lol but lets have the abilities we need."

The account experience is **Ask · Receive · Sit** (Hunter, #9736).

## Principles

1. **Additive.** Google sign-in is one more way in, alongside guest links, seat keys, and GlyphSafe badges. It never replaces an existing route, and it never puts a public page behind a login.
2. **Google proves who you are. Each house decides what you may do.** A Google sign-in resolves to one Xi account. Permissions come from that house's grants and badges. A house owner sets their own rules: Deep is Hunter-only, and LivingTree is Anthony's to set.
3. **One client, many doors.** The field shares one Google OAuth client. Each house that offers the button adds its own origin to that client.

## Join checklist for a house

- [ ] Add `https://<house>.xi-field.com` to the shared client's **Authorized JavaScript origins**. Hunter or a box-side seat does this in Google Cloud Console.
- [ ] Request only `openid`, `email`, and `profile`. With only these basic scopes, Google lets any user sign in even while the app is in Testing, and publishing it needs no verification. Sources: [Google production readiness](https://developers.google.com/identity/protocols/oauth2/production-readiness/overview), [Google Cloud Help](https://support.google.com/cloud/answer/13463073).
- [ ] Verify the ID token on the server (audience = the shared client ID, issuer = Google) before trusting the email.
- [ ] Map the verified email to the Xi account, and create it on first sign-in only if the house allows that.
- [ ] Apply the house's own grants. Default for a new arrival: what a guest already gets, nothing less.
- [ ] Keep any existing sign-in working. Test it after the change.
- [ ] Put no client secret in a public page or repo. The client ID is public by design.

## Outside checks (Plex runs these as each door lands)

| Check | Pass |
|---|---|
| The page shows "Sign in with Google" | yes |
| An existing guest or seat link still works | yes |
| A page that was public is still public | yes |
| A private house (for example Deep) still refuses others | 401/403 |
