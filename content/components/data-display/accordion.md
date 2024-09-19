# Accordion

## The component

{{< tabs items="Accordion,AccordionContent,AccordionItem,AccordionTrigger" >}}

{{< tab >}}
```django {filename="accordion.html"}
{% var default_page=default_page|default:"" %}

<div class="relative w-full divide-y divide-gray-200 {{ classes }}"
  x-data="{
    activeAccordion: '',
    setActiveAccordion(id) {
        this.activeAccordion = (this.activeAccordion == id) ? '' : id
    }
}">
{{ children }}
</div>
```
{{< /tab >}}

{{< tab >}}
```django {filename="accordion_content.html"}
<div x-show="activeAccordion==id" x-collapse x-cloak>
  <div class="p-4 pt-0 {{ classes }}">
    {{ children }}
  </div>
</div>
```
{{< /tab >}}

{{< tab >}}
```django {filename="accordion_item.html"}
<div class="cursor-pointer group"
     x-data="{ id: $id('accordion') }" 
     {% if active %}x-init="setActiveAccordion(id)"{% endif %}>
  {{ children }}
</div>
```
{{< /tab >}}

{{< tab >}}
```django {filename="accordion_trigger.html"}
<button @click="setActiveAccordion(id)" class="flex items-center justify-between w-full p-4 text-left select-none group-hover:underline {{ classes }}">
  {{ children }}
  {% Icon name="i-[heroicons--chevron-down]" classes="duration-200 ease-out" :class="{ 'rotate-180': activeAccordion==id }" %}
</button>
```
{{< /tab >}}
{{< /tabs >}}


## Usage

{{< iframe "accordions/default" 24rem >}}

```django
{% #Accordion %}
  {% #AccordionItem %}
    {% #AccordionTrigger %}Click to open{% /AccordionTrigger %}
    {% #AccordionContent %}
    Oh hello, hi there.
    {% /AccordionContent %}
  {% /AccordionItem %}
  {% #AccordionItem %}
    {% #AccordionTrigger %}Click to open{% /AccordionTrigger %}
    {% #AccordionContent %}
    Oh hello, hi there.
    {% /AccordionContent %}
  {% /AccordionItem %}
  {% #AccordionItem %}
    {% #AccordionTrigger %}Click to open{% /AccordionTrigger %}
    {% #AccordionContent %}
    Oh hello, hi there.
    {% /AccordionContent %}
  {% /AccordionItem %}
{% /Accordion %}
```

### Accordion with a Page Opened

{{< iframe "accordions/preselected" 24rem >}}

```django
{% #Accordion %}
  {% #AccordionItem %}
    {% #AccordionTrigger %}Click to open{% /AccordionTrigger %}
    {% #AccordionContent %}
    Oh hello, hi there.
    {% /AccordionContent %}
  {% /AccordionItem %}
  {% #AccordionItem active %}
    {% #AccordionTrigger %}Click to open{% /AccordionTrigger %}
    {% #AccordionContent %}
    Oh hello, hi there.
    {% /AccordionContent %}
  {% /AccordionItem %}
  {% #AccordionItem %}
    {% #AccordionTrigger %}Click to open{% /AccordionTrigger %}
    {% #AccordionContent %}
    Oh hello, hi there.
    {% /AccordionContent %}
  {% /AccordionItem %}
{% /Accordion %}
```
