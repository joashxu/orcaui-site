# Card

## The Component 

{{< tabs items="Card,CardActions,CardBody,CardTitle" >}}

{{< tab >}}
```django {filename="card.html"}
{% var bg=bg|default:"bg-base-100" %}
{% var width=width|default:"w-full" %}
{% var shadow=shadow|match:"sm: shadow-sm , base: shadow , md: shadow-md , lg: shadow-lg"|default:"shadow-md" %}

<div class="card {{ bg }} {{ width }} {{ shadow }} {% if side %}card-side{% endif %} {{ classes }}">
  {{ children }}
</div>
```
{{< /tab >}}

{{< tab >}}
```django {filename="card_actions.html"}
<div class="card-actions {{ classes }}">
  {{ children }}
</div>
```
{{< /tab >}}

{{< tab >}}
```django {filename="card_body.html"}
<div class="card-body {{ classes }}">
  {{ children }}
</div>
```
{{< /tab >}}

{{< tab >}}
```django {filename="card_title.html"}
<h2 class="card-title {{ classes }}">{{ children }}</h2>
```
{{< /tab >}}

{{< /tabs >}}

## Usage

{{< iframe "card/default" 24rem >}}

```django
{% #Card width="w-96" %}
  {% #CardBody %}
    {% #CardTitle %}Shoes!{% /CardTitle %}
    <p>These are some shoes. They're the best shoes!</p>
    {% #CardActions classes="justify-end" %}
      {% #Button variant="primary"%}Buy Now{% /Button %}
    {% /CardActions %}
  {% /CardBody %}
{% /Card %}
```

### Card with Top Image

{{< iframe "card/top-image" 38rem >}}

```django
{% #Card width="w-96" %}
  <figure><img src="https://img.daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.webp" alt="Shoes" /></figure>
  {% #CardBody %}
    {% #CardTitle %}Shoes!{% /CardTitle %}
    <p>These are some shoes. They're the best shoes!</p>
    {% #CardActions %}
      {% #Button variant="primary"%}Buy Now{% /Button %}
    {% /CardActions %}
  {% /CardBody %}
{% /Card %}
```

### Card with Button Image

{{< iframe "card/bottom-image" 38rem>}}

```django
{% #Card width="w-96" %}
  {% #CardBody %}
    {% #CardTitle %}Shoes!{% /CardTitle %}
    <p>These are some shoes. They're the best shoes!</p>
  {% /CardBody %}
  <figure><img src="https://img.daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.webp" alt="Shoes" /></figure>
{% /Card %}
```

### Card with Horizontal Image

{{< iframe "card/horizontal" 24rem>}}

```django
{% #Card side %}
  <figure><img src="https://img.daisyui.com/images/stock/photo-1606107557195-0e29a4b5b4aa.webp" alt="Shoes" /></figure>
  {% #CardBody %}
    {% #CardTitle %}Shoes!{% /CardTitle %}
    <p>These are some shoes. They're the best shoes!</p>
    {% #CardActions classes="justify-end" %}
      {% #Button variant="primary"%}Buy Now{% /Button %}
    {% /CardActions %}
  {% /CardBody %}
{% /Card %}
```

### Card Example

{{< iframe "card/showcase" 36rem >}}

```django
{% #Card width="w-96" %}
  {% #CardBody %}
    {% #CardTitle %}Notifications{% /CardTitle %}

    <p class="text-gray-500 text-sm">You have 3 unread messages.</p>
    <div class="flex items-center space-x-4 rounded-md border p-4 mb-2">
      {% Icon name="i-[heroicons--bell-alert]" %}
      <div class="flex-1 space-y-1">
        <p class="text-sm font-medium leading-none">Push Notifications</p>
        <p class="text-sm text-muted-foreground">Send notifications to device.</p>
      </div>
    </div>
    <ul class="[&>li]:mb-2 list-disc px-4 mb-4">
      <li>
        <span class="font-medium">Your call has been confirmed.</span>
        <span class="block text-sm text-gray-500">2 minutes ago</span>
      </li>
      <li>
        <span class="font-medium">You have a new message!</span>
        <span class="block text-sm text-gray-500">1 hour ago</span>
      </li>
      <li>
        <span class="font-medium">Your subscription is expiring soon!</span>
        <span class="block text-sm text-gray-500">1 day ago</span>
      </li>
    </ul>

    {% #CardActions %}
      {% #Button variant="neutral" size="sm" block %}Mark all as read {% /Button %}
    {% /CardActions %}
  {% /CardBody %}
{% /Card %}
```

