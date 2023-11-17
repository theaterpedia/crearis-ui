<br />
<p align="center">
  <img src="https://user-images.githubusercontent.com/1626923/157498695-885de6c5-deba-416d-8287-51e7269aef56.png" alt="Crearis UI" />
</p>

<h3 align="center">
  Customizable typography solution for Tailwind (Variant of Storefront UI: Tailwind-Config)
</h3>
<p align="center">
  Create your own typography palette that fits perfectly with the rest of design system.
</p>

<p align="center">
  <img alt="npm" src="https://img.shields.io/npm/v/@crearis/typography">
  <a href="http://commitizen.github.io/cz-cli/">
    <img alt="Commitizen friendly" src="https://img.shields.io/badge/commitizen-friendly-brightgreen.svg" />
  </a>
  <a href="https://github.com/theaterpedia/crearis-ui">
    <img alt="License" src="https://img.shields.io/github/license/vuestorefront/storefront-ui" />
  </a>
  <a href="https://github.com/theaterpedia/crearis-ui/pulls">
    <img alt="PRs Welcome" src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg" />
  </a>
</p>


---

# SF Typography

Tailwind plugin that allows you to create fully customizable typography system. Ships with StorefrontUI typography by default.
<br /><br />
Made with ❤️ by <a href="https://github.com/vuestorefront" target="_blank">Vue Storefront</a> team and contributors.

## Why?

In many projects the designers specify a standarized range of typography atoms. From headings, body texts to elements like labels - everything follows the same palette of font styles. And whilst Tailwind is great when it comes to dealing with atomic styling we believe that **having typography-related classes structured leads to a better developer experience**. 💚
That's why we introduce you `SF Typography` plugin - to bring typography systems back to the Tailwind world!

## Installation

```bash
npm install --save-dev @storefront-ui/typography
```

```ts
// tailwind.config.ts

import sfTypography from '@storefront-ui/typography';

export default {
  content: ['your-components-source-directory/*.ts'],
  plugins: [sfTypography]
};
```

And get ready to use default StorefrontUI typography classes [that are based on SFUI designs](https://docs.storefrontui.io/v2/figma).

## How to use it

Every class defined within Tailwind theme configuration can be used in your template with a `typography-` prefix. You could use default classes as follows:

```html
<h2 class="typography-headline-3">Specifications</h2>

<h3 class="typography-headline-2">Fabric Content</h3>
<p class="typography-text-lg">Cotton blend</p>
<h3 class="typography-headline-2">Sleeve Length Style</h3>
<p class="typography-text-lg">Short sleeve</p>
```

## Customization

### Theming

Typography-related styling can be customized as a part of [Tailwind theme customization](https://tailwindcss.com/docs/theme#extending-the-default-theme):

#### Extending default theme

```ts
// tailwind.config.ts

import sfTypography from '@storefront-ui/typography';

export default {
  content: ['your-components-source-directory/*.ts'],
  plugins: [sfTypography],

  theme: {
    extend: {
      sfTypography: ({ theme }) => ({
        'headline-2': {
          fontSize: theme('fontSize.4xl'),
          lineHeight: '1.1',
        },
        'headline-8': {
          fontSize: theme('fontSize.xs'),
          lineHeight: theme('lineHeight.4'),
          fontWeight: theme('fontWeight.light')
        },
      })
    }
  }
};
```

#### Overriding default theme

You can also specify your own, fully custom typography palette:

```ts
// tailwind.config.ts

import sfTypography from '@storefront-ui/typography';

export default {
  content: ['your-components-source-directory/*.ts'],
  plugins: [sfTypography],

  theme: {
    sfTypography: ({ theme }) => ({
      'heading': {
        fontSize: theme('fontSize.4xl'),
        lineHeight: '1.1',
      },
      'label': {
        fontSize: theme('fontSize.xs'),
        lineHeight: theme('lineHeight.4'),
        fontWeight: theme('fontWeight.light')
      },
    })
  }
};
```

With configuration above, you can start using `typography-heading` and `typography-label` classes right away!

### Changing classNames prefix

You can change the default prefix `typography-` by passing configuration options when initializing the plugin:

```ts
// tailwind.config.ts

import sfTypography from '@storefront-ui/typography';

export default {
  content: ['your-components-source-directory/*.ts'],
  plugins: [sfTypography({ utilityPrefix: 'custom-text' })]
};
```

After this change, we can use `custom-text-` as a className prefix:

```html
<h2 class="custom-text-headline-3">Specifications</h2>

<h3 class="custom-text-headline-2">Fabric Content</h3>
<p class="custom-text-text-lg">Cotton blend</p>
```

## Looking for a library to accelerate your ecommerce development?

Make sure to check out StorefrontUI! [Read the documentation at https://docs.storefrontui.io/v2/](https://docs.storefrontui.io/v2/) 🚀
