# Badge

## The Component

```django {filename="badge.html"}
{% var size=size|match:"xs: badge-xs , sm: badge-sm , lg: badge-lg "|default:"badge-md" %}
{% var variant=variant|match:"neutral: badge-neutral , primary: badge-primary , secondary: badge-secondary , accent: badge-accent , ghost: badge-ghost , info: badge-info , success: badge-success , warning: badge-warning , error: badge-error "|default:"" %}
{% var modifier=modifier|match:"outline: badge-outline "|default:"" %}

<div class="badge {{ modifier }} {{ variant }} {{ size }} {{ classes }}">{{ children }}</div>
```

## Usage

{{< iframe "badges/brand-color" 12rem >}}

```django
{% #Badge %}Default{% /Badge %}
{% #Badge variant="neutral" %}Neutral{% /Badge %}
{% #Badge variant="primary" %}Primary{% /Badge %}
{% #Badge variant="secondary" %}Secondary{% /Badge %}
{% #Badge variant="accent" %}Accent{% /Badge %}
{% #Badge variant="ghost" %}Ghost{% /Badge %}
```

### Outline badge

{{< iframe "badges/outline" 12rem >}}

```django
{% #Badge %}Default{% /Badge %}
{% #Badge variant="neutral" modifier="outline" %}Neutral{% /Badge %}
{% #Badge variant="primary" modifier="outline" %}Primary{% /Badge %}
{% #Badge variant="secondary" modifier="outline" %}Secondary{% /Badge %}
{% #Badge variant="accent" modifier="outline" %}Accent{% /Badge %}
{% #Badge variant="ghost" modifier="outline" %}Ghost{% /Badge %}
```

### Badge Sizes

{{< iframe "badges/sizes" 12rem >}}

```django
{% #Badge size="xs" %}Extra small{% /Badge %}
{% #Badge size="sm" %}Small{% /Badge %}
{% #Badge %}Default{% /Badge %}
{% #Badge size="lg" %}Large{% /Badge %}
```

### Empty Badge

{{< iframe "badges/empty" 12rem >}}

```django
{% #Badge variant="primary" size="xs" %}{% /Badge %}
{% #Badge variant="primary" size="sm" %}{% /Badge %}
{% #Badge variant="primary" %}{% /Badge %}
{% #Badge variant="primary" size="lg" %}{% /Badge %}
```

### Badge with State Colors

{{< iframe "badges/state-color" 12rem >}}

```django
{% #Badge variant="info" %}Info{% /Badge %}
{% #Badge variant="success" %}Success{% /Badge %}
{% #Badge variant="warning" %}Warning{% /Badge %}
{% #Badge variant="error"  %}Error{% /Badge %}
```

### Badge in a Text

{{< iframe "badges/in-text" 16rem >}}

```django
<h2 class="text-xl">Heading {% #Badge size="lg" %}Info{% /Badge %}</h2>
<h3 class="text-lg">Heading {% #Badge size="md" %}Success{% /Badge %}</h3>
<h4 class="text-base">Heading {% #Badge size="sm" %}Warning{% /Badge %}</h4>
<h5 class="text-sm">Heading {% #Badge size="xs" %}Error{% /Badge %}</h5>
```

### Badge in a Button

{{< iframe "badges/in-button" 12rem >}}

```django
{% #Button %}
  Inbox {% #Badge %}+99{% /Badge %}
{% /Button %}
{% #Button %}
  Inbox {% #Badge variant="secondary" %}+99{% /Badge %}
{% /Button %}
```