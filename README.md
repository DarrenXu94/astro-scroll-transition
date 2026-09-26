# Astro Scroll Transition

A scroll-driven image transition component for Astro. Import the `.astro` component, provide an ordered list of images, and add matching named slots for the content shown with each image.

## Install

```sh
npm install astro-scroll-transition
```

Astro is a peer dependency and must be installed in the consuming project.

## Use

```astro
---
import Transition from "astro-scroll-transition/Transition.astro";
import firstImage from "../assets/first.jpg";
import secondImage from "../assets/second.jpg";
import thirdImage from "../assets/third.jpg";
---

<Transition
  images={[firstImage, secondImage, thirdImage]}
  transitionDistance="75vh"
  transitionHold="25vh"
>
  <section slot="content-0"><h2>First scene</h2></section>
  <section slot="content-1"><h2>Second scene</h2></section>
  <section slot="content-2"><h2>Third scene</h2></section>
</Transition>
```

Slots are named `content-0`, `content-1`, and so on, matching the order of the `images` array. Images may be imported assets or image URLs supported by Astro's [image service](https://docs.astro.build/en/guides/images/).

### Props

| Prop | Default | Description |
| --- | --- | --- |
| `images` | `[]` | Ordered image sources for the transition. |
| `transitionDistance` | `75vh` | Scroll distance used to fade between adjacent images. |
| `transitionHold` | `25vh` | Scroll distance to hold each image before the next fade. |
| `scrollStartHeight` | `0vh` | Scroll spacing before the first transition. |
| `scrollEndHeight` | `0vh` | Scroll spacing after the last transition. |
| `containerHeight` | calculated | Optional explicit height for the component wrapper. Otherwise derived from the viewport and transition props. |

## Run the demo locally

The repository root is also a standalone Astro demo site. It imports the component through the package export, so the demo exercises the same import path used by consumers.

```sh
npm install
npm run demo
```

Astro starts the demo at `http://localhost:4321`. Build and preview the demo with `npm run build` and `npm run preview`.

## Package and publish

Before publishing, ensure the `name` in `package.json` is available on npm. Preview the exact contents of the package tarball with:

```sh
npm pack --dry-run
```

The published package contains the component and this README. `npm publish` runs the demo production build first through the `prepublishOnly` script.