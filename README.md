# Mechadex


Mechadex is a prototype for an interactive database of common game mechanics, styled with a periodic table aesthetic.
<img width="1600" height="805" alt="image" src="https://github.com/user-attachments/assets/efbea67f-0830-4ff9-859e-740447888541" />

> [!NOTE]
> If you're here because you want to add or edit a mechanic on Mechadex, please go to the separate [mechanics repository](https://github.com/Mechadex/mechanics). This repository is for the source code of Mechadex.

***

* All mechanics for Mechadex are stored in [this repository](https://github.com/Mechadex/mechanics).

* It's made with SvelteKit, and it uses Lunr for search indexing.
* There is no "backend", because it just fetches a pre-built search index (directly from Github) from the mechanics repository initially. It fetches individual mechanics when needed. There might be some issues with that, namely Github banning me forever because I'm using their generous servers for free. But I figure 1 active user a month won't raise any eyebrows. 

* Mechadex is very, to put it simply, scrappy. So the code behind it is far scrappier. There's also the fact that I'm a complete beginner to web development.

## How it works
Mechadex fetches `build/concise_index.json` from the mechanics repository on page load. That contains basic info on every mechanic and is used to render the mechanic cards on the home page. 

Searching must work for fields that aren't loaded initially, like the long Description, so Lunr builds a proper search index using Github Actions. This search index is also loaded on page load. Lunr.js takes over and allows searching to work.

When a mechanic clicked, `[mechanic category]/[mechanic symbol]/mechanic.yaml` is loaded from the mechanics repository, and that contains all the info for that mechanic. This is cached in session storage so it doesn't have to be loaded again for that session. It doesn't use local storage because then cache invalidation becomes an issue and it takes less than a second to load a single YAML file on a decent internet connection.
## Using this locally

You can self-host Mechadex if you really want to. Install Node.js first, then open your terminal (Command Prompt or Bash or anything.)

Run:
```bash
git clone https://github.com/Mechadex/mechadex.github.io
cd mechadex.github.io
npm install
```

### Developing

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

### Building

To create a production version of your app:

```bash
npm run build
```

You can preview the production build with `npm run preview`.

> To deploy your app, you may need to install an [adapter](https://kit.svelte.dev/docs/adapters) for your target environment.
