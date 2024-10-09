---
runme:
  id: 01J9Q54KC56EGW0HWRSTRB4QRM
  version: v3
---

# Welcome 👋!

...to the Intro to Runnable Docs with Runme & Stateful.

```sh {"id":"01J9PKTCCF1X9NKG7N64SVWDJ4","interactive":"false"}
curl -s https://media.graphassets.com/8npLBOUJT7K3i1AksnVj
```

- I'm [Sebastian Huckleberry](https://www.linkedin.com/in/sebastiantiedtke/) (formerly Tiedtke; just got married 💒)
- Co-founder & CTO at [Stateful](https://stateful.com/).
- Grew up outside of Munich in Germany 🇩🇪
- Relocated to the USA 🇺🇸 ~15y ago to work at startups (Sauce Labs & Smallstep)

# Unbreak Engineering Docs

Today we'll talk about how to levarage runnable docs to:

- Platform customers/teams to operate self-service
- Customer/team solution hand-off
- Supporting escalations & incident response

## Why is this so hard ⛓️‍💥?

#### It's 2024... and docs are still **always** broken

```sh {"id":"01J9QKC740F5YY7WPVGCC7JRQD","interactive":"false"}
curl -Ls https://steemitimages.com/0x0/https://media1.giphy.com/media/F7yLXA5fJ5sLC/giphy.gif
```

- Fault lines between tooling: editor, terminal, browser, and cloud consoles
- Disconnect between authoring, reading, running docs: often wrong the moment they are written
- Even if docs are "correct", we often don't realize they are couple with unreproducible environments
- Docs are a side-show, copy&paste at best, never how work actually gets done

### To solve this problem, we have created the open source toolchain called [Runme](https://runme.dev).

```javascript {"id":"01J9PP34RXT5C0470PABM5AC5T","interactive":"false"}
const sharp = require('sharp'), https = require('https'), ratio = process.env.IMG_RATIO || 0.1;
const w = Math.round(9535 * ratio), h = Math.round(8004 * ratio);
https.get('https://runme.dev/runme_cube.svg', (response) => {
  let data = '';
  response.on('data', (chunk) => data += chunk);
  response.on('end', () => sharp(Buffer.from(data)).resize(w, h).toBuffer().then(resized => process.stdout.write(resized)));
});
```

## Ohai large ▶️ Runme logo

Change the ratio with the cell below and rerun the previous cell to see its effect.

```sh {"id":"01J9PTV1YKNA83TESRZ18WC90D","promptEnv":"yes","terminalRows":"3"}
export IMG_RATIO="Enter the ratio of the image, e.g. 0.04"
echo "IMG_RATIO=${IMG_RATIO}"
```

Enough said, let's [dive right in](docs/0_intro.md)!

## Devcontainer Images & Templates 🧙 by ContainerCraft

This demo depends on the excellent devcontainer infra provided by https://github.com/ContainerCraft and their respective OSS licenses:

- https://github.com/ContainerCraft/Konductor
- https://github.com/ContainerCraft/devcontainer

## Licensing

This repo is license under Apache 2.0. The full license is right here:

```sh {"id":"01J9PTQEJNGB9PCYVG8DSEDNSQ","terminalRows":"20"}
cat LICENSE
```
