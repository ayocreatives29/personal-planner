# Firebase Security

The GitHub Pages app uses Firebase Auth before opening Realtime Database listeners.

Before applying locked Realtime Database rules:

1. In Firebase Console, enable Authentication > Sign-in method > Google.
2. Add `ayocreatives29.github.io` to Authentication > Settings > Authorized domains.
3. Apply `database.rules.json` to Realtime Database rules.

For a stricter personal-only database, replace both rule expressions with your Google account email:

```json
{
  "rules": {
    ".read": "auth != null && auth.token.email == 'YOUR_EMAIL@gmail.com'",
    ".write": "auth != null && auth.token.email == 'YOUR_EMAIL@gmail.com'"
  }
}
```

Calendar note: the app opens prefilled Google Calendar event pages for tasks. This does not require a separate Google Calendar developer setup.
