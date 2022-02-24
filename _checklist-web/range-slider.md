---
layout: entry
title:  "Range slider input"
description: "How to code and test an accessible range slider input for Web"
categories: form

keyboard:
  tab: |
    Focus moves visibly to the input
  arrow-keys: |
    Increase / decrease value one step
  page-up: |
    Increases slider value
  page-down: |
    Decreases slider value
  home: |
    Sets slider to its minimum value.
  end: |
    Sets slider to its maximum value.

mobile:
  swipe: |
    Focus moves to the input
  swipe up/down: |
    Increase/decrease slider value one step on iOS
  volume: |
    Increase/decrease slider value one step on Android

screenreader:
  name:  |
    Its purpose is clear
  role:  |
    It identifies itself as a range
  group: |
    Its label is read with the input
  state: |
    It its current value

gherkin-keyboard: 
  - when:  |
      the tab key to move focus to a range slider
    result: |
      focus is strongly visually indicated
  - then:  |
      the up/down/left/right arrow keys
    result: |
      the value is changed one step
  - then:  |
      the page up/page down keys
    result: |
      the value is changed one step

gherkin-mobile:
  - when:  |
      swipe to move focus to a range slider
  - then:  |
      swipe up/down in iOS or use the volume buttons in Android
    result: |
      the value is changed one step
---

## Code examples


### Semantic HTML
While there is a native range input, it is difficult to style reliably across browsers.

This is one of the exceedingly rare instances where a custom element makes a lot of sense.

{% highlight html %}
{% include /examples/input-range.html %}
{% endhighlight %}

{::nomarkdown}
<example>
{% include /examples/input-range.html %}
</example>
{:/}


### Custom elements

This is a rare instance where custom elements are easier to style reliably across browsers.

{% highlight html %}
<div id="range-label">
  How much cowbell?
</div>
<div class="track">
  <div id="thumb"
       role="slider"
       tabindex="0"
       aria-valuemin="0"
       aria-valuenow="10"
       aria-valuemax="11"
       aria-labelledby="range-label">
  </div>
</div>
{% endhighlight %}

Working example: <https://www.w3.org/TR/wai-aria-practices/examples/slider/slider-1.html>


## Developer notes

### Name
- Include `for="input-id` in each `<label>` label to associate it with the input
- Use `aria-label="Input name"` as a last resort if a `<label>` can't be used
- Don't hide the label on focus

### Role
- Identifies as a text input

### State

For custom elements, use these aria attributes to describe the min, max and current value.

- `aria-valuemin`
- `aria-valuemax`
- `aria-valuenow`

### Group
- Include `for="input-id` in each `<label>` label to associate it with the input

### Focus
- Focus must be visible