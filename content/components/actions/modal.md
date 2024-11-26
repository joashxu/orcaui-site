# Modal

## The Components

### The Modal

{{< tabs items="Modal,ModalContent,ModalContentDynamic,ModalTrigger" >}}

{{< tab >}}
```django {filename="modal.html"}
<div {% attrs id %}
     x-data="{ modalOpen: false, context:{}, openModal(){ this.modalOpen = true }, closeModal() { this.modalOpen = false } }"
     @modal-open.window="if ($el.id && $event.detail.target === $el.id) { context = $event.detail; openModal(); }"
     @modal-close.window=" if ($el.id && $event.detail.context.target === $el.id) { closeModal() }"
     @keydown.escape.window="modalOpen = false"
     class="{{ classes }}">
  {{ children }}
</div>
```
{{< /tab >}}

{{< tab >}}
```django {filename="modal_content.html"}
{% var size=size|default:"max-w-2xl" %}

<template x-teleport="body">
  <div x-show="modalOpen" x-cloak>
    <div class="modal" :class="modalOpen ? 'modal-open': ''">
      <div x-show="modalOpen"
           x-transition
           x-trap.inert.noscroll="modalOpen"
           class="modal-box p-0 {{ size }}">
        <template x-if="modalOpen">
          <div>{{ children }}</div>
        </template>
      </div>
    </div>
  </div>
</template>
```
{{< /tab >}}

{{< tab >}}
```django {filename="modal_content_dynamic.html"}
<div {% if url %}x-data="{ contentURL: '{{ url }}'}"{% else %}x-data{% endif %} >
  <div {% attrs :hx-get %}
       {% if url %}:hx-get="contentURL"{% endif %}
       hx-trigger="load, reload"
       x-data="{ hasError: false, loading: false, reload() { htmx.trigger($el, 'reload'); } }"
       x-init="$nextTick(() => { htmx.process($el); })"
       x-on:htmx:before-request="loading = true"
       x-on:htmx:after-request="loading = false"
       x-on:htmx:before-on-load="
        const xhr = $event.detail.xhr;
        if (xhr.status != 200) {
          $event.stopPropagation();
          hasError = true;
          let parser = new DOMParser();
          let documentContent = parser.parseFromString(xhr.responseText, 'text/html');
          let content = documentContent.body.innerHTML;
          $refs.response_container.innerHTML = content;
        }">
    <div  class="container flex flex-wrap justify-between items-center mx-auto">
      <div x-ref="response_container" class="max-h-32 overflow-y-auto">
        <div class="text-center w-full text-gray-500">
          {% Loading %}
        </div>
      </div>
      <div x-show="hasError" class="text-center w-full p-3 text-gray-500">
        {% #Button @click="reload()" size="sm" :disabled=loading %}
          {% Loading x-show="loading" size="sm" %} Reload
        {% /Button %}
      </div>
    </div>
  </div>
</div>
```
{{< /tab >}}

{{< tab >}}
```django {filename="modal_trigger.html"}
<div x-data
     @click="
        if ('modalOpen' in $data) {
          modalOpen = true;
        } else {
          let context = {};
          let attributes = Array.from($el.attributes).filter(attr => attr.name.startsWith('data-modal'));
          attributes.forEach(attr => {
              const key = attr.name.replace('data-modal-', '');
              context[key] = attr.value;
          });
          $dispatch('modal-open', context);
        }"
     {% attrs data-modal-target data-modal-url %}>
  {{ children }}
</div>
```
{{< /tab >}}

{{< /tabs >}}

### The Modal Dialog

{{< tabs items="ModalDialog,ModalDialogClose,ModalDialogContent,ModalDialogFooter,ModalDialogHeader" >}}

{{< tab >}}
```django {filename="modal_dialog.html"}
<div class="{{ classes }}">
  {{ children }}
</div>
```
{{< /tab >}}

{{< tab >}}
```django {filename="modal_dialog_close.html"}
{% #Button shape="circle" variant="ghost" @click="modalOpen=false" size="sm" %}
  {% Icon name="i-[heroicons--x-mark]" size="sm" %}
{% /Button %}
```
{{< /tab >}}

{{< tab >}}
```django {filename="modal_dialog_content.html"}
<div class="p-3 md:p-4 {{ classes }}" >
  {{ children }}
</div>
```
{{< /tab >}}

{{< tab >}}
```django {filename="modal_dialog_footer.html"}
<div class="px-3 pb-3 md:px-4 md:pb-4 {{ classes }}">
  {{ children }}
</div>
```
{{< /tab >}}

{{< tab >}}
```django {filename="modal_dialog_header.html"}
<div class="flex items-center justify-between pt-3 px-3 md:px-4 md:pt-4 {{ classes }}">
  <div class="text-lg font-bold">{{ children }}</div>
  {% ModalDialogClose %}
</div>
```
{{< /tab >}}

{{< /tabs >}}

## Usage

### Modal

{{< iframe "modals/default" 16rem >}}

```django
  {% #Modal %}
    {% #ModalTrigger %}
      {% #Button %}Open Modal{% /Button %}
    {% /ModalTrigger %}
    {% #ModalContent %}
      {% #ModalDialog %}
        {% #ModalDialogHeader %}Hello!{% /ModalDialogHeader %}
        {% #ModalDialogContent %}Modal Content{% /ModalDialogContent %}
      {% /ModalDialog %}
    {% /ModalContent %}
  {% /Modal %}
```

### Modal with Remote URL

{{< iframe "modals/remote-url" 24rem >}}

```django
  {% #Modal %}
    {% #ModalTrigger %}
      {% #Button %}Open Modal{% /Button %}
    {% /ModalTrigger %}
    {% #ModalContent %}
      {% #ModalDialog %}
        {% #ModalDialogHeader %}Remote URL{% /ModalDialogHeader %}
        {% #ModalDialogContent %}
          {% ModalContentDynamic url="/buttons/default" %}
        {% /ModalDialogContent %}
      {% /ModalDialog %}
    {% /ModalContent %}
  {% /Modal %}
```

### Error Handling

{{< iframe "modals/error-handling" 24rem >}}

```django
  {% #Modal %}
    {% #ModalTrigger %}
      {% #Button %}Open Modal{% /Button %}
    {% /ModalTrigger %}
    {% #ModalContent %}
      {% #ModalDialog %}
        {% #ModalDialogHeader %}Remote URL{% /ModalDialogHeader %}
        {% #ModalDialogContent %}
          {% ModalContentDynamic url="/buttons/default2" %}
        {% /ModalDialogContent %}
      {% /ModalDialog %}
    {% /ModalContent %}
  {% /Modal %}
```

### Modal Size

{{< iframe "modals/size" 24rem >}}

```django
  {% #Modal %}
    {% #ModalTrigger %}
      {% #Button %}Open Modal{% /Button %}
    {% /ModalTrigger %}
    {% #ModalContent size="max-w-4xl" %}
      {% #ModalDialog %}
        {% #ModalDialogHeader %}Remote URL{% /ModalDialogHeader %}
        {% #ModalDialogContent %}
          {% ModalContentDynamic url="/buttons/default" %}
        {% /ModalDialogContent %}
      {% /ModalDialog %}
    {% /ModalContent %}
  {% /Modal %}
```

### Detached Modal

{{< iframe "modals/detached" 32rem >}}

```django
<div>
  <div>
    {% #ModalTrigger data-modal-target="modal-one" data-modal-url="/buttons/default" %}
      {% #Button %}Show Default Button{% /Button %}
    {% /ModalTrigger %}

    {% #ModalTrigger data-modal-target="modal-one" data-modal-url="/buttons/with-icon" %}
      {% #Button %}Show Button with Icon{% /Button %}
    {% /ModalTrigger %}

    {% #ModalTrigger data-modal-target="modal-one" data-modal-url="/buttons/loading" %}
      {% #Button %}Show Loading Button{% /Button %}
    {% /ModalTrigger %}
  </div>

  {% #Modal id="modal-one" %}
    {% #ModalContent %}
      {% #ModalDialog %}
        {% #ModalDialogHeader %}Remote URL{% /ModalDialogHeader %}
        {% #ModalDialogContent %}
          {% ModalContentDynamic :hx-get="context.url" %}
        {% /ModalDialogContent %}
      {% /ModalDialog %}
    {% /ModalContent %}
  {% /Modal %}
</div>
```
