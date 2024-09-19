# Avatar

## Avatar

{{< iframe "avatars/default" 16rem >}}

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

## Avatar with Ring

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

## Avatar Sizes

{{< iframe "avatars/sizes" 16rem >}}

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

## Avatar Group

{{< iframe "avatars/group" 16rem >}}

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

## Online and Offline Status

{{< iframe "avatars/online-offline" 16rem >}}

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