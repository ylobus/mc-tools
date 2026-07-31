# mc-tools

A self-hosted **Blender extensions repository** for MightyCanvas tools, served as a
static site over GitHub Pages. It lets any team member install and update all our
Blender tools from inside Blender, no matter where they are.

## Add the repository in Blender

1. `Edit → Preferences → Get Extensions → Repositories → [ + ] → Add Remote Repository`
2. Paste the URL:

   ```
   https://ylobus.github.io/mc-tools/extensions/index.json
   ```

3. Enable it, then **Refresh** — the tools appear under *Get Extensions*, ready to install.

## What's here

```
mc-tools/
├─ .nojekyll                 # disable Jekyll so files are served verbatim
└─ extensions/
   ├─ index.json             # the repository listing Blender reads
   └─ *.zip                  # built extension packages, one per tool/version
```

## How the listing is generated

Each tool lives in its own source repo and publishes its built `.zip` here. After the
zips change, regenerate `index.json` with Blender's command-line tool:

```
blender --command extension server-generate --repo-dir ./extensions
```

`index.json` uses **relative** archive URLs, so the `.zip` files must stay next to it.
