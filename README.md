# My personal website and blog !

This website was developped using Astro with its blog template :

```
npm create astro@latest -- --template blog
```

## Project Structure

Inside of this Astro project, you'll see the following folders and files:

```
├── public/
│   ├── images/
│   ├── heroes/
│   └── posts/
├── src/
│   ├── components/
│   ├── layouts/
│   └── pages/
├── astro.config.mjs
├── README.md
├── package.json
├── yarn.lock
└── tsconfig.json
```

Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

Any static assets, like images, can be placed in the `public/` directory.

## Commands

All commands are run from the root of the project, from a terminal:

| Command                 | Action                                           |
| :---------------------- | :----------------------------------------------- |
| `yarn install`          | Installs dependencies                            |
| `yarn start`            | Starts local dev server at `localhost:3000`      |
| `yarn build`            | Build your production site to `./dist/`          |
| `yarn astro ...`        | Run CLI commands like `astro add`, `astro check` |
| `yarn astro --help`     | Get help using the Astro CLI                     |