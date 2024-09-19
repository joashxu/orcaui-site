# Kbd

## The Component

```django {filename=kbd.html}
{% var size=size|match:"xs: kbd-xs , sm: kbd-sm , md: kbd-md , lg: kbd-lg "|default:"kbd-md" %}

<kbd class="kbd {{ size }}">{{ children }}</kbd>
```

## Usage

{{< iframe "kbd/default" 12rem >}}

```django
{% #Kbd %}Y{% /Kbd %}
```

### Kbd Sizes

{{< iframe "kbd/sizes" 12rem >}}

```django
{% #Kbd size="lg" %}Ctrl{% /Kbd %}
{% #Kbd size="md" %}Ctrl{% /Kbd %}
{% #Kbd size="sm" %}Ctrl{% /Kbd %}
{% #Kbd size="xs" %}Ctrl{% /Kbd %}
```

### In Text

{{< iframe "kbd/in-text" 12rem >}}

```django
Press {% #Kbd size="sm"%}F{% /Kbd %} to pay respects.
```

### Key Combination

{{< iframe "kbd/combination" 12rem >}}

```django
{% #Kbd %}Ctrl{% /Kbd %} +
{% #Kbd %}Shift{% /Kbd %} +
{% #Kbd %}Del{% /Kbd %}
```

### Function Keys

{{< iframe "kbd/function-key" 12rem >}}

```django
{% #Kbd %}⌘{% /Kbd %}
{% #Kbd %}⌥{% /Kbd %}
{% #Kbd %}⇧{% /Kbd %}
{% #Kbd %}⌃{% /Kbd %}
```