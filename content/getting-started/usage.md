---
title: Usage
weight: 2
---

## Creating a Component


```html
{% var size=size|match:"xs: kbd-xs , sm: kbd-sm , md: kbd-md , lg: kbd-lg "|default:"kbd-md" %}

<kbd class="kbd {{ size }}">{{ children }}</kbd>
```


## Registering the Component

Before you can use our new component, you need to register it. Create a `components.yaml` file in your project root template directory. Think of it as an index for all of your components. Slippers will read this file to register your components.

```yaml
compontents:
    Kbd: "_ui/components/kbd.html"
```

## Using the Component

Now that you have created the component, you can use it with the following.

```html
{% #Kbd %}Ctrl{% /Kbd %} + {% #Kbd %}Shift{% /Kbd %} + {% #Kbd %}Del{% /Kbd %}
```