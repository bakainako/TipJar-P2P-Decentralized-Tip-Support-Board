# TipJar P2P — Skill File

## Agent Instructions

This skill file teaches agents how to interact with the TipJar P2P creator board built on Intercom.

---

## What This App Does

TipJar P2P is a peer-to-peer creator tipping board. Creators post their work; supporters send TNK tips via Intercom P2P sidechannels directly to creator Trac wallet addresses.

---

## Agent Capabilities

### 1. Post a Creator Entry

**Trigger phrases:** "post my work", "add a creator post", "submit to tipjar"

**Required fields:**
- `name` — creator handle or name
- `category` — one of: Art, Music, Code, Writing, Video, Research, Design, Other
- `title` — title of the work (max 80 chars)
- `desc` — short description (max 500 chars)
- `trac` — Trac wallet address to receive tips

**Action:** Call `submitPost()` with the above fields filled in the UI form, or inject directly into the `posts` array in localStorage under key `tipjar_posts`.

---

### 2. Send a Tip

**Trigger phrases:** "tip a creator", "send TNK to creator", "support this post"

**Required fields:**
- `postId` — ID of the post to tip
- `amount` — TNK amount (integer, minimum 1)
- `message` — optional message to creator

**Action:** Call `sendTip()` after setting `tipAmount` and optionally `tipMessage`. The tip is routed via Intercom P2P sidechannel to the creator's Trac address stored on the post.

---

### 3. Browse / Filter Posts

**Trigger phrases:** "show me art posts", "filter by code", "list all creators"

**Action:** Call `filterCat(category, btn)` with the desired category string. Valid values: `'All'`, `'Art'`, `'Music'`, `'Code'`, `'Writing'`, `'Video'`, `'Research'`, `'Design'`.

---

### 4. Read Stats

**Trigger phrases:** "how many tips", "total TNK tipped", "how many creators"

**Action:** Read from:
- `document.getElementById('stat-posts').textContent` — total posts
- `document.getElementById('stat-tips').textContent` — total tips sent
- `document.getElementById('stat-tnk').textContent` — total TNK tipped
- `document.getElementById('stat-creators').textContent` — unique creators

---

## Data Schema

### Post Object
```json
{
  "id": 1700000000000,
  "name": "creator_handle",
  "category": "Art",
  "title": "My Artwork Title",
  "desc": "Description of the work",
  "trac": "trac1q...",
  "tipTotal": 0,
  "tipCount": 0,
  "time": 1700000000000
}
```

### Tip Object
```json
{
  "postId": 1700000000000,
  "amount": 500,
  "message": "Keep creating!",
  "time": 1700000000000
}
```

---

## localStorage Keys

| Key | Value |
|---|---|
| `tipjar_posts` | JSON array of Post objects |
| `tipjar_tips` | JSON array of Tip objects |

---

## Intercom P2P Integration Notes

- Tips are routed via Intercom sidechannels to the recipient Trac address
- Each post stores one Trac address (the creator's receiving address)
- Tip confirmation is P2P — no server involved
- This app is a fork of [Trac-Systems/intercom](https://github.com/Trac-Systems/intercom)

---

## Error Handling

| Error | Agent Response |
|---|---|
| Missing required field | Prompt user for missing info before submitting |
| Invalid Trac address | Warn that address may be invalid; ask to double-check |
| Tip amount < 1 | Reject and ask for a valid positive integer |
| Post not found | Inform user the post ID does not exist |
