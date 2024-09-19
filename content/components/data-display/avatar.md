# Avatar

## The Component

```django {filename="avatar.html"}
{% var size=size|match:"xs: w-6 , sm: w-8 , lg: w-12, xl: w-24"|default:"w-10" %}
{% var rounded=rounded|default:"rounded-full" %}
{% if with_ring %}{% var ring="ring ring-primary ring-offset-base-100 ring-offset-2" %}{% else %}{% var ring="" %}{% endif %}

<div class="overflow-hidden inline-flex {% if with_ring %}p-3{% endif %}" 
     x-data="{ showImage: false, options: '{{ size }} {{ rounded }} {{ ring }}' }">
  {{ children }}
</div>
```

## Usage

{{< iframe "avatars/default" 14rem >}}

```django
{% #Avatar %}
  {% #AvatarFallback %}YS{% /AvatarFallback %}
{% /Avatar %}
{% #Avatar %}
  {% AvatarImage src="https://img.daisyui.com/images/stock/photo-1534528741775-53994a69daeb.webp" %}
  {% #AvatarFallback %}YS{% /AvatarFallback %}
{% /Avatar %}
{% #Avatar %}
  {% AvatarImage src="https://invalid_image_url.webp" %}
  {% #AvatarFallback %}YS{% /AvatarFallback %}
{% /Avatar %}
```

### Avatar with Ring

{{< iframe "avatars/ring" 16rem >}}


```django
{% #Avatar size="lg" with_ring %}
  {% #AvatarFallback %}YS{% /AvatarFallback %}
{% /Avatar %}
{% #Avatar size="lg" with_ring %}
  {% AvatarImage src="https://img.daisyui.com/images/stock/photo-1534528741775-53994a69daeb.webp" %}
  {% #AvatarFallback %}YS{% /AvatarFallback %}
{% /Avatar %}
```

### Avatar Sizes

{{< iframe "avatars/sizes" 14rem >}}

```django
{% #Avatar size="xs" %}
  {% AvatarImage src="https://img.daisyui.com/images/stock/photo-1534528741775-53994a69daeb.webp" %}
{% /Avatar %}
{% #Avatar size="sm" %}
  {% AvatarImage src="https://img.daisyui.com/images/stock/photo-1534528741775-53994a69daeb.webp" %}
{% /Avatar %}
{% #Avatar %}
  {% AvatarImage src="https://img.daisyui.com/images/stock/photo-1534528741775-53994a69daeb.webp" %}
{% /Avatar %}
{% #Avatar size="lg" %}
  {% AvatarImage src="https://img.daisyui.com/images/stock/photo-1534528741775-53994a69daeb.webp" %}
{% /Avatar %}
```

### Avatar Group

{{< iframe "avatars/group" 14rem >}}

```django
{% #AvatarGroup %}
  {% #Avatar size="sm" %}
    {% AvatarImage src="https://img.daisyui.com/images/stock/photo-1534528741775-53994a69daeb.webp" %}
  {% /Avatar %}
  {% #Avatar size="sm" %}
      {% AvatarImage src="https://img.daisyui.com/images/stock/photo-1534528741775-53994a69daeb.webp" %}
    {% /Avatar %}
  {% #Avatar size="sm" %}
      {% AvatarImage src="https://img.daisyui.com/images/stock/photo-1534528741775-53994a69daeb.webp" %}
    {% /Avatar %}
  {% #Avatar size="sm" %}
      {% AvatarImage src="https://img.daisyui.com/images/stock/photo-1534528741775-53994a69daeb.webp" %}
    {% /Avatar %}
{% /AvatarGroup %}
```

### Online and Offline Status

{{< iframe "avatars/online-offline" 14rem >}}

```django
{% #Avatar %}
  {% AvatarImage src="https://img.daisyui.com/images/stock/photo-1534528741775-53994a69daeb.webp" status="online"%}
{% /Avatar %}
{% #Avatar %}
  {% AvatarImage src="https://img.daisyui.com/images/stock/photo-1534528741775-53994a69daeb.webp" status="offline" %}
{% /Avatar %}

{% #Avatar %}
  {% #AvatarFallback status="online" %}YS{% /AvatarFallback %}
{% /Avatar %}
{% #Avatar %}
  {% #AvatarFallback status="offline" %}YS{% /AvatarFallback %}
{% /Avatar %}
``