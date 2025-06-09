# GPT Prompts Website

This site is built using [Docusaurus](https://docusaurus.io/) and will host a collection of useful prompts for language models.

## Project URL

You can view the site at [https://atarashiineko.github.io/toy_projects/](https://atarashiineko.github.io/toy_projects/).

## Installation

```bash
npm install
```

## Local Development

```bash
npm start
```

This command starts a local development server and opens up a browser window. Most changes are reflected live without having to restart the server.

## Build

```bash
npm run build
```

This command generates static content into the `build` directory and can be served using any static contents hosting service.

## Deployment

Using SSH:

```bash
USE_SSH=true npm run deploy
```

Not using SSH:

```bash
GIT_USER=<Your GitHub username> npm run deploy
```

If you are using GitHub pages for hosting, this command is a convenient way to build the website and push to the `gh-pages` branch.
