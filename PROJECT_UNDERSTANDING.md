# Project Understanding

## Overview

This repository is a `Nuxt 4` website for `SERVONIATEKNOLOGI`, positioned as a corporate technology / digital solutions company.

The current implementation is mainly a marketing landing page with:

- a homepage at `/`
- a very minimal `/about` page
- a shared default layout with a navbar
- a footer rendered directly on the homepage

The app looks like a customized `Nuxt UI` starter template that has been adapted into a company profile / landing page.

## Tech Stack

- `Nuxt 4`
- `Vue 3`
- `TypeScript`
- `@nuxt/ui`
- `Tailwind CSS v4`
- `@vueuse/core`
- `GSAP`
- `ESLint`

## Scripts

Defined in `package.json`:

- `pnpm dev` - start local dev server
- `pnpm build` - production build
- `pnpm preview` - preview production build
- `pnpm lint` - run ESLint
- `pnpm typecheck` - run Nuxt type checking

## Project Structure

### Root

- `nuxt.config.ts`  
  Loads `@nuxt/eslint` and `@nuxt/ui`, enables devtools, imports global CSS from `app/assets/css/main.css`, and prerenders `/`.

- `package.json`  
  Main dependency and script entrypoint.

- `.github/workflows/ci.yml`  
  CI runs `pnpm install`, `pnpm run lint`, and `pnpm run typecheck` on Node `22`.

- `README.md`  
  Still the default Nuxt starter README and does not yet describe this actual project.

### App

- `app/app.vue`  
  Global app shell. It only mounts `NuxtLayout` and `NuxtPage`.

- `app/layouts/default.vue`  
  Shared layout. Renders `UiNavbar` in a gradient header and places page content inside a container wrapper.

- `app/pages/index.vue`  
  Main homepage. It assembles these sections in order:
  - `SectionsHero`
  - `SectionsServices`
  - `SectionsAbout`
  - `SectionsCta`
  - `UiFooter`

- `app/pages/about.vue`  
  Currently only shows a simple placeholder heading: `THIS IS ABOUT PAGE`.

### Sections

- `app/components/sections/Hero.vue`  
  Hero banner with background image, company name, tagline, description, and a `Learn More` button.

- `app/components/sections/Services.vue`  
  Three-card services block using `UiServiceCard`. Content is partly placeholder and should be reviewed.

- `app/components/sections/About.vue`  
  Corporate trust / capability section. Uses:
  - `GSAP`
  - `SplitText`
  - `IntersectionObserver`
  - `UiCounter`

  It animates the `You Can Trust` text and reveals supporting bullet points.

- `app/components/sections/Cta.vue`  
  Final call-to-action section with `Contact Us Today` button.

### UI Components

- `app/components/ui/Navbar.vue`  
  Responsive navbar with desktop links and a mobile toggle menu.

- `app/components/ui/Footer.vue`  
  Footer with company title, quick links, and contact info.

- `app/components/ui/Counter.vue`  
  Animated counter showing:
  - `500` projects completed
  - `98%` client satisfaction

  It uses `@vueuse/core` intersection observer logic to trigger when visible.

- `app/components/ui/ServiceCard.vue`  
  Reusable card wrapper with icon slot, title slot, body content slot, and `Learn More` link.

- `app/components/ui/Categories.vue`  
  Appears to be an unused demo component.

- `app/components/ui/Card.vue`  
  Appears incomplete or leftover. It references `Card-button`, which I did not find in the inspected structure.

- `app/components/ui/test.vue` and `app/components/ui/test copy.vue`  
  Experimental GSAP / SplitText test components. These look like scratch files rather than production components.

### Other Components

- `app/components/AppLogo.vue`  
  SVG logo component.

- `app/components/TemplateMenu.vue`  
  Leftover Nuxt UI starter menu linking to template demos. It does not appear to be part of the current site.

## Styling Notes

Global styling lives in `app/assets/css/main.css`.

Current styling characteristics:

- imports `tailwindcss` and `@nuxt/ui`
- defines custom green color tokens
- registers local `Roboto` and `GoogleSans` fonts from `public/fonts`
- applies broad global resets for lists and links
- uses a darker brand palette, especially:
  - `#032A17`
  - `#1B2D37`
  - `#69473B`
  - `#815F53`

Important note:

- `* { font-family: var(--font-eb-garamond); }` is present globally, but I did not find `--font-eb-garamond` defined in the inspected files.
- `body` later sets `Roboto`, so there may be conflicting or unintended font behavior.

## Current Content / Brand Direction

The brand presentation currently suggests:

- company name: `SERVONIATEKNOLOGI`
- short label variation: `ServoniaTek`
- slogan: `Innovation You Can Trust`
- market position: enterprise / corporate technology solutions
- location shown in footer: `Jakarta, Indonesia`
- contact shown in footer: `hello@servoniateknologi.com`

## Current State Of The Site

The project is already usable as a visual landing page, but it is still in an early or mid-build state.

Observed unfinished areas:

- `README.md` is still starter content
- `/about` is placeholder only
- navbar links include routes that do not exist yet, such as `/contact`
- several links still use `#`
- `Services.vue` contains placeholder copy
- test / demo components are still inside the production component tree
- there are starter leftovers like `TemplateMenu.vue`
- some code looks experimental rather than finalized

## Behavior Summary

### Routing

- `/` is the real homepage
- `/about` exists but is not developed
- `/contact` is linked in navigation but no page was found during inspection

### Animations

- hero section uses CSS fade-up animation classes
- about section uses GSAP `SplitText` for animated headline characters
- about section and counter use intersection-based triggering

### Layout

- navbar is in the default layout, so it appears across pages
- footer is currently inserted directly in `app/pages/index.vue`, not globally in the layout

## Useful Files To Start With

If I need to work on this repo again, these are the first files to inspect:

- `package.json`
- `nuxt.config.ts`
- `app/pages/index.vue`
- `app/layouts/default.vue`
- `app/components/ui/Navbar.vue`
- `app/components/sections/Hero.vue`
- `app/components/sections/Services.vue`
- `app/components/sections/About.vue`
- `app/components/sections/Cta.vue`
- `app/components/ui/Footer.vue`
- `app/assets/css/main.css`

## Recommended Next Cleanup Steps

If this project is going to keep growing, the most useful next improvements would be:

1. Replace the starter `README.md` with project-specific documentation.
2. Decide which components are production vs. experiments, then remove or relocate test files.
3. Fix navigation so every link points to a real page or an in-page anchor.
4. Replace placeholder copy in services and about sections.
5. Decide whether the footer should live in the global layout.
6. Review font setup and global CSS resets for unintended side effects.
7. Add metadata / SEO setup for the homepage and future content pages.

## Working Assumption For Future Tasks

Unless the structure changes significantly, I should treat this repository as:

`A Nuxt 4 marketing website for ServoniaTek / SERVONIATEKNOLOGI, currently focused on a corporate landing page with custom styling, GSAP-enhanced section animations, and several unfinished placeholder areas still to be cleaned up.`
