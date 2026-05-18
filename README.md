# somewhere — a geography of memory

A shared memory map for three people. Pin moments to places, build a bloom map of shared geography.

## setup

### 1. create your github repo

Make a new **public** repo. Upload both files:
- `memory-map.html`
- `memories.json`

Enable **GitHub Pages**: repo Settings → Pages → deploy from branch `main`, root `/`.

### 2. configure the app

Open `memory-map.html` and edit the config block near the top of the `<script>`:

```js
const GH_OWNER  = 'your-github-username';
const GH_REPO   = 'your-repo-name';
const GH_FILE   = 'memories.json';
const GH_BRANCH = 'main';
```

Optionally rename the three identities and their colors:

```js
const IDENTITIES = [
  { id: 'A', color: '#c4471a', nameKey: 'somewhere_name_A', defaultName: 'alice' },
  { id: 'B', color: '#2e6e9e', nameKey: 'somewhere_name_B', defaultName: 'bob' },
  { id: 'C', color: '#4a7c59', nameKey: 'somewhere_name_C', defaultName: 'carmen' },
];
```

Commit and push.

### 3. create one shared github token

Only **one** token is needed — whoever sets up the repo creates it and shares it with the other two:

1. github.com → Settings → Developer settings → Personal access tokens → Fine-grained tokens
2. **Generate new token**
3. Repository access: **Only select repositories** → choose your repo
4. Permissions: **Contents** → **Read and write**
5. Generate, copy, share with your group

Each person pastes the token the **first time they save a memory** — a prompt appears once. It's stored in their browser's localStorage and never committed to the repo.

### 4. use it

- Open your GitHub Pages URL
- Pick your identity (names are editable inline — your chosen name saves to your browser)
- The app remembers who you are on return visits
- Add memories — they save directly to `memories.json` in the repo
- Click ↺ to pull the latest from anyone else
- Switch to **Bloom Map** to see the shared geography

### notes

- Token entered once per device, stored in localStorage only
- If two people save simultaneously, second write wins — hit ↺ to sync
- Photos aren't stored in the repo (GitHub API limits) — text, location, date, tags all save fine
