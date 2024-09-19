---
title: Installation
weight: 1
---

This document assume that you have installed and setup your Django project.

### Django Slippers

You can install Slippers from PyPI

```bash
$ pip install slippers
```

Add `slippers` to your `INSTALLED_APPS`.

```python
# setting.py

INSTALLED_APPS = [
    ...,
    'slippers',
    ...,
]
```

And done.


## Tailwind CSS

Please refer to the [TailwindCSS installation documentation](https://tailwindcss.com/docs/installation).

## Daisy UI

You also need to install daisyUI.

{{% steps %}}

### Install daisyUI

```bash
$ npm i -D daisyui@latest
```

### Add daisyUi to tailwind.config.js

```javascript
module.exports = {
  plugins: [
      require('daisyui'),
  ],
  // Optional
  daisyui: {
      themes: ['light', 'dark', 'cupcake', 'bumblebee', 'retro'],
      styled: true,
  }
}
```

{{% /steps %}}
