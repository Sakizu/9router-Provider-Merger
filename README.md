# 9router-Provider-Merger

A single-file, browser-based JSON editor for managing 9router provider connections (`9router-backup-*.json`). No build step, no server — just open `editor.html`.

## Features

- **Load / Save** — open a `9router-backup-*.json` file, edit it, and export the result
- **Export Backup** — save a timestamped backup copy without altering the working file
- **Merge Provider** — import connections from another backup JSON and merge selected providers into the current data
  - Skips duplicates by connection ID
  - Auto-renames connections with conflicting names (`Server A` → `Server A 1`, `Server A 2`, ...)
- **Toggle Active** — enable/disable a single connection, or all at once
- **Search & Filter** — filter by name, email, provider, or active/inactive status
- **Delete** — remove a connection with confirmation

## Usage

1. Open `editor.html` in any modern browser
2. Click **Load JSON** and select your `9router-backup-*.json` file
3. Edit connections directly in the UI
4. To merge another backup: **Merge Provider** → select file → choose providers → review preview → **Merge Now**
5. Click **Save JSON** to export the updated file

## Data format

Expects a JSON file with the shape:

```json
{
  "providerConnections": [
    {
      "id": "unique-id",
      "provider": "provider-name",
      "name": "Connection Name",
      "email": "optional@example.com",
      "apiKey": "optional",
      "accessToken": "optional",
      "isActive": true,
      "priority": 1,
      "testStatus": "optional",
      "createdAt": "ISO date",
      "lastUsedAt": "ISO date"
    }
  ]
}
```

## Notes

- Runs entirely client-side — no data leaves the browser.
- Connections may include API keys / access tokens. Keep backup JSON files and this repo **private**; do not commit real credentials.
- Responsive layout — works on desktop and mobile.

## License

Internal tool — license TBD.
