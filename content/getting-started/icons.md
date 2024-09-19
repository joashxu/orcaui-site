---
title: Icons
weight: 3
---

This project uses Iconify, a solution that streamlines the use of icons in web projects. Iconify offers a vast library of icons from various collections, simplifying their integration into projects. It enables dynamic generation of SVG icons, eliminating the need to download and store them manually. Through the use of APIs or client-side libraries, Iconify fetches and renders SVG icons on-demand based on the icons' identifiers.

While icons can be added to HTML through CSS or directly as SVG, using inline SVG provides greater flexibility. This method allows for complex interactions and styling, making icons more accessible and adaptable to the application's state, thereby improving user experience.

OrcaUI uses the excellent `heroicons` icon set by default. You can customize this to suit your need.

## Install Iconify

```bash
$ npm install @iconify-json/heroicons
```

## Setting up Iconify

Go to your `tailwind.config.js` file and write the following functions.

```javascript
import { readFileSync, mkdir, writeFileSync } from 'fs';
import { getIconData, matchIconName } from '@iconify/utils';

const TARGET = 'orcaui/templates/icons';
const CACHE = Object.create(null);


function loadIconSet(prefix) {
  let main = require.resolve(`@iconify-json/${prefix}/icons.json`);
  if (!main) {
    return;
  }

  if (CACHE[main]) {
    return CACHE[main];
  }

  try {
    const result = JSON.parse(readFileSync(main, 'utf8'));
    CACHE[main] = result;
    return result;
  }
  catch { }
}


function addDynamicIconSelectors(options) {
  const prefix = 'i';
  const outDir = `${TARGET}`;

  mkdir(outDir, { recursive: true }, (err) => { if (err) throw err; });

  return (({ matchComponents }) => {
    matchComponents({
      [prefix]: (icon) => {
        // Get icon identifier
        const nameParts = icon.split(/--|\:/);

        if (nameParts.length !== 2) {
          throw new Error(`Invalid icon name: "${icon}"`); 
        }

        // Get icon set prefix and icon name
        const [iconSetPrefix, name] = nameParts;
        if (!(iconSetPrefix.match(matchIconName) && name.match(matchIconName))) {
          throw new Error(`Invalid icon name: "${icon}"`);
        }

        // Load icon set
        const iconSet = loadIconSet(iconSetPrefix);
        if (!iconSet) {
          throw new Error(
              `Cannot load icon set for "${prefix}". Install "@iconify-json/${prefix}" as dev dependency?`
          );
        }

        // Get icon data
        const data =  getIconData(iconSet, name);

        // Save data to file
        writeFileSync(`${__dirname}/${outDir}/${prefix}-[${icon}]`, data['body']);
        return;
      }
    });
  })
}

/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
      './orcaui/templates/**/*.html',
      './orcaui/templates/**/*.yaml',
  ],
  plugins: [
      require('daisyui'),
      require('@iconify-json/heroicons'),
      addDynamicIconSelectors(),
  ],
  daisyui: {
      themes: ['light', 'dark', 'cupcake', 'bumblebee', 'retro'],
      styled: true,
  }
}
```

## Usage

### Create the Icon component 

```django
{% var size=size|match:"xs: xs, sm: sm, base: base, lg: lg, xl: xl"|default:"base" %}
{% var icon_size=size|match:"xs: h-4 w-4 , sm: h-5 w-5, base: h-6 w-6 , lg: h-7 w-7, xl: h-8 w-8 " %}
{% var viewbox=viewbox|match:"xs: 0 0 16 16 , sm: 0 0 20 20 "|default:"0 0 24 24" %}
{% var icon_path="icons/"|add:name %}

<svg xmlns="http://www.w3.org/2000/svg"
     class="{{ icon_size }} {{ color }} {{ classes }}"
     viewBox="{{ viewbox }}"
     {% attrs fill stroke stroke-width stroke-linecap stroke-linejoin %}
     {% attrs :class %}>
  {% include icon_path %}
</svg>
```

### Register the Icon component

```yaml
components:
  ...
  Icon: "_ui/components/icon.html"
  ...
```

### Usage in the Template

```django
{% #Button variant="primary" %}
  {% Icon name="i-[heroicons--adjustments-horizontal]" %}
{% /Button %}
```

