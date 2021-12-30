# Svelte Pokedex
This is based on a tutorial by Scott Q Quick, the link is here: https://www.youtube.com/watch?v=UU7MgYIbtAk. I switched out the pokemon images for the "official-artwork" type, created a gigantic Pokemon detail view that looks like a playing card, and fetched some additional information from the API. I also added a few CSS styles like a background gradient, and imported the UnoCSS Engine, which is amaze balls, link to that engine here: https://github.com/antfu/unocss.


## Developing

npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

Before creating a production version of your app, install an [adapter](https://kit.svelte.dev/docs#adapters) for your target environment. Then:

```bash
npm run build
```

> You can preview the built app with `npm run preview`, regardless of whether you installed an adapter. This should _not_ be used to serve your app in production.
