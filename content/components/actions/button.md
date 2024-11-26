# Button

## The Component

```django
{% var size=size|match:"xs: btn-xs , sm: btn-sm , lg: btn-lg "|default:"btn-md" %}
{% var variant=variant|match:"neutral: btn-neutral , primary: btn-primary , secondary: btn-secondary , accent: btn-accent , ghost: btn-ghost , info: btn-info , success: btn-success , warning: btn-warning , error: btn-error , link: btn-link "|default:"" %}
{% var shape=shape|match:"square: btn-square , circle: btn-circle "|default:"" %}
{% var modifier=modifier|match:"outline: btn-outline "|default:"" %}
{% var type=type|default:"button" %}
{% var el=as_el|match:"div: div , a: a"|default:"button" %}

<{{el}} {% if el == "button" %}type="{{ type }}"{% endif %}
        {% if el == "div" %}tabindex="0" role="button"{% endif %}
        class="btn {% if active %}btn-active{% endif %} {% if block %}btn-block{% endif %} {{ shape }} {{ modifier }} {{ variant }} {{ size }} {{ classes }}"
        {% attrs id name form value disabled href %}
        {% attrs hx-get hx-post hx-confirm %}
        {% attrs x-show x-cloak x-ref @click @click.once :id :disabled :class %}>
  {{ children }}
</{{el}}>
```

## Properties

| Property | Description                                                                                | Default |
| -------- | ------------------------------------------------------------------------------------------ | ------- |
| size     | *xs*, *sm*, *md*, *lg*                                                                     | *md*    |
| variant  | *neutral, primary, primary, secondary, accent, ghost, info, success, warning, error, link* |         |
| shape    | *square, circle*                                                                           |         |

## Usage

{{< iframe "buttons/default" 16rem >}}

```django
{% #Button %}Button{% /Button %}
{% #Button variant="neutral" %}Neutral{% /Button %}
{% #Button variant="primary" %}Primary{% /Button %}
{% #Button variant="secondary" %}Secondary{% /Button %}
{% #Button variant="accent" %}Accent{% /Button %}
{% #Button variant="ghost" %}Ghost{% /Button %}
{% #Button variant="link" %}Link{% /Button %}
```

### Button with State Colors

{{< iframe "buttons/state-color" 16rem >}}

```django
{% #Button variant="info" %}Info{% /Button %}
{% #Button variant="success" %}Success{% /Button %}
{% #Button variant="warning" %}Warning{% /Button %}
{% #Button variant="error" %}Error{% /Button %}
```

### Button with Modifier

{{< iframe "buttons/modifier" 16rem >}}

```django
<div>
    {% #Button modifier="outline" %}Default{% /Button %}
    {% #Button variant="primary" modifier="outline" %}Primary{% /Button %}
    {% #Button variant="secondary" modifier="outline" %}Secondary{% /Button %}
    {% #Button variant="accent" modifier="outline" %}Accent{% /Button %}
</div>
<div>
    {% #Button variant="info" modifier="outline" %}Info{% /Button %}
    {% #Button variant="success" modifier="outline" %}Success{% /Button %}
    {% #Button variant="warning" modifier="outline" %}Warning{% /Button %}
    {% #Button variant="error" modifier="outline" %}Error{% /Button %}
</div>
```

### Button Sizes

{{< iframe "buttons/sizes" 16rem >}}

```django
{% #Button size="xs" %}Extra Small{% /Button %}
{% #Button size="sm" %}Small{% /Button %}
{% #Button %}Base{% /Button %}
{% #Button size="lg" %}Large{% /Button %}
```

### Icon Button

{{< iframe "buttons/icons" 16rem >}}

```django
{% #Button variant="primary" %}
  {% Icon name="i-[heroicons--adjustments-horizontal]" %}
{% /Button %}
{% #Button variant="primary" %}
  {% Icon name="i-[heroicons--face-smile]" %}
{% /Button %}
{% #Button %}
  {% Icon name="i-[heroicons--archive-box-solid]" %}
{% /Button %}
{% #Button %}
  {% Icon name="i-[heroicons--chat-bubble-bottom-center-solid]" %}
{% /Button %}
{% #Button variant="ghost" %}
  {% Icon name="i-[heroicons--eye]" %}
{% /Button %}
{% #Button variant="ghost" %}
  {% Icon name="i-[heroicons--bell-alert]" %}
{% /Button %}
```

#### Icon Button with Shape

{{< iframe "buttons/icons-shape" 16rem >}}

```django
<div>
  {% #Button shape="square" variant="primary" %}
    {% Icon name="i-[heroicons--adjustments-horizontal]" %}
  {% /Button %}
  {% #Button shape="square" variant="primary" %}
    {% Icon name="i-[heroicons--face-smile]" %}
  {% /Button %}
  {% #Button shape="square" %}
    {% Icon name="i-[heroicons--archive-box-solid]" %}
  {% /Button %}
  {% #Button shape="square" %}
    {% Icon name="i-[heroicons--chat-bubble-bottom-center-solid]" %}
  {% /Button %}
  {% #Button shape="square" variant="ghost" %}
    {% Icon name="i-[heroicons--eye]" %}
  {% /Button %}
  {% #Button shape="square" variant="ghost" %}
    {% Icon name="i-[heroicons--bell-alert]" %}
  {% /Button %}
</div>
<div>
  {% #Button shape="circle" variant="primary" %}
    {% Icon name="i-[heroicons--adjustments-horizontal]" %}
  {% /Button %}
  {% #Button shape="circle" variant="primary" %}
    {% Icon name="i-[heroicons--face-smile]" %}
  {% /Button %}
  {% #Button shape="circle" %}
    {% Icon name="i-[heroicons--archive-box-solid]" %}
  {% /Button %}
  {% #Button shape="circle" %}
    {% Icon name="i-[heroicons--chat-bubble-bottom-center-solid]" %}
  {% /Button %}
  {% #Button shape="circle" variant="ghost" %}
    {% Icon name="i-[heroicons--eye]" %}
  {% /Button %}
  {% #Button shape="circle" variant="ghost" %}
    {% Icon name="i-[heroicons--bell-alert]" %}
  {% /Button %}
</div>
```

#### Icon Button with Shape and Modifier

{{< iframe "buttons/icons-shape-modifier" 16rem >}}

```django
<div>
  {% #Button shape="square" modifier="outline" variant="primary" %}
    {% Icon name="i-[heroicons--adjustments-horizontal]" %}
  {% /Button %}
  {% #Button shape="square" modifier="outline" variant="primary" %}
    {% Icon name="i-[heroicons--face-smile]" %}
  {% /Button %}
  {% #Button shape="square" modifier="outline" %}
    {% Icon name="i-[heroicons--archive-box-solid]" %}
  {% /Button %}
  {% #Button shape="square" modifier="outline" %}
    {% Icon name="i-[heroicons--chat-bubble-bottom-center-solid]" %}
  {% /Button %}
  {% #Button shape="square" modifier="outline" variant="ghost" %}
    {% Icon name="i-[heroicons--eye]" %}
  {% /Button %}
  {% #Button shape="square" modifier="outline" variant="ghost" %}
    {% Icon name="i-[heroicons--bell-alert]" %}
  {% /Button %}
</div>
<div>
  {% #Button shape="circle" modifier="outline" variant="primary" %}
    {% Icon name="i-[heroicons--adjustments-horizontal]" %}
  {% /Button %}
  {% #Button shape="circle" modifier="outline" variant="primary" %}
    {% Icon name="i-[heroicons--face-smile]" %}
  {% /Button %}
  {% #Button shape="circle" modifier="outline" %}
    {% Icon name="i-[heroicons--archive-box-solid]" %}
  {% /Button %}
  {% #Button shape="circle" modifier="outline" %}
    {% Icon name="i-[heroicons--chat-bubble-bottom-center-solid]" %}
  {% /Button %}
  {% #Button shape="circle" modifier="outline" variant="ghost" %}
    {% Icon name="i-[heroicons--eye]" %}
  {% /Button %}
  {% #Button shape="circle" modifier="outline" variant="ghost" %}
    {% Icon name="i-[heroicons--bell-alert]" %}
  {% /Button %}
</div>
```

### Button with Icon

{{< iframe "buttons/with-icon" 24rem >}}

```django
<div>
  {% #Button %}
    {% Icon name="i-[heroicons--adjustments-horizontal]" %}
    Button
  {% /Button %}
  {% #Button variant="neutral" %}
    {% Icon name="i-[heroicons--face-smile]" %}
    Neutral
  {% /Button %}
  {% #Button variant="primary" %}
    {% Icon name="i-[heroicons--adjustments-horizontal]" %}
    Primary
  {% /Button %}
  {% #Button variant="secondary" %}
    {% Icon name="i-[heroicons--face-smile]" %}
    Secondary
  {% /Button %}
  {% #Button variant="accent" %}
    {% Icon name="i-[heroicons--archive-box-solid]" %}
    Accent
  {% /Button %}
  {% #Button variant="ghost" %}
    {% Icon name="i-[heroicons--chat-bubble-bottom-center-solid]" %}
    Ghost
  {% /Button %}
</div>
<div>
  {% #Button %}Button 
    {% Icon name="i-[heroicons--adjustments-horizontal]" %}
  {% /Button %}
  {% #Button variant="neutral" %}
    Neutral 
    {% Icon name="i-[heroicons--face-smile]" %}
  {% /Button %}
  {% #Button variant="primary" %}
    Primary 
    {% Icon name="i-[heroicons--adjustments-horizontal]" %}
  {% /Button %}
  {% #Button variant="secondary" %}
    Secondary 
    {% Icon name="i-[heroicons--face-smile]" %}
  {% /Button %}
  {% #Button variant="accent" %}
    Accent 
    {% Icon name="i-[heroicons--archive-box-solid]" %}
  {% /Button %}
  {% #Button variant="ghost" %}
    Secondary 
    {% Icon name="i-[heroicons--chat-bubble-bottom-center-solid]" %}
  {% /Button %}
</div>
```

### Button States

{{< iframe "buttons/states" 18rem >}}

```django
<div>
  {% #Button variant="primary" %}Primary{% /Button %}
  {% #Button variant="primary" active %}Primary Active{% /Button %}
  {% #Button variant="primary" disabled %}Primary Disabled{% /Button %}
</div>
<div>
  {% #Button %}Secondary{% /Button %}
  {% #Button active %}Secondary Active{% /Button %}
  {% #Button disabled %}Secondary Disabled{% /Button %}
</div>
<div>
  {% #Button variant="ghost" %}Ghost{% /Button %}
  {% #Button variant="ghost" active %}Ghost Active{% /Button %}
  {% #Button variant="ghost" disabled %}Ghost Disabled{% /Button %}
</div>
```

### Loading Button

{{< iframe "buttons/loading" 16rem >}}

```django
<div>
  {% #Button variant="primary" %}{% Loading size="xs" %} Primary{% /Button %}
  {% #Button variant="secondary" %}{% Loading size="xs" %} Secondary{% /Button %}
  {% #Button variant="tertiary" %}{% Loading size="xs" %} Ghost{% /Button %}
</div>
<div>
  {% #Button variant="primary" disabled %}
    {% Loading size="xs" %} Primary
  {% /Button %}
  {% #Button variant="secondary" disabled %}
    {% Loading size="xs" %} Secondary
  {% /Button %}
  {% #Button variant="tertiary" disabled %}
    {% Loading size="xs" %} Ghost
  {% /Button %}
</div>
```

### Link as Button

{{< iframe "buttons/link" 16rem >}}

```django
{% #Button variant="primary" as_el="a" %}Primary{% /Button %}
{% #Button variant="secondary" as_el="a" %}Secondary{% /Button %}
{% #Button variant="accent" as_el="a" %}Ghost{% /Button %}
```
