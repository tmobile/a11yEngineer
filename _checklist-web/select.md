---
layout: entry
title:  "Dropdown select"
description: "How to code and test an accessible select listbox dropdown for the Web"
categories: form

keyboard:
  tab: |
    Focus moves visibly to the input
  arrow-keys: |
    Moves focus to and chooses the next option. 
  escape: |
    If the select options are displayed, collapses the select and moves focus to the select.
     
mobile:
  swipe: |
    Focus moves to the input, traverses list
  double-tap: |
    Opens select, chooses option

screenreader:
  name:  |
    Its purpose is clear
  role:  |
    It identifies itself as a select, popup, menu/submenu, listbox or combobox
  group: |
    Its label is read with the option
  state: |
    It indicates which option is selected 
    
gherkin-keyboard: 
  - when:  |
      the tab key to move focus to a select
    result: |
      focus is strongly visually indicated
  - then:  |
      the arrow keys to select an option
    result: |
      the selected option is changed
  - then:  |
      the escape key when the select is open 
    result: |
     it collapses and focus moves to the select

gherkin-mobile:
  - when:  |
      swipe to focus on a select
  - then:  |
      doubletap with the select in focus
    result: |
      the picker/spinner opens
---

## Code examples

### Use the Semantic HTML `<select>`

This native select contains all the accessibility criteria for free and is styled to look cool.

{% highlight html %}
{% include /examples/input-select.html %}
{% endhighlight %}

{::nomarkdown}
<example>
{% include /examples/input-select.html %}
</example>
{:/}

### Custom dropdown select elements: Just don't.

Custom dropdown selects are [notoriously difficult](https://www.24a11y.com/2019/select-your-poison/) to make screen reader accessible. 

> …it is now thoroughly clear that recreating the native behavior of a `<select>` element is impossible: its underlying semantics differ across platforms; its keyboard behavior is inconsistent; its mobile presentation and behavior is entirely different from desktop. In making a custom UI control, we take upon ourselves what was the browser’s responsibility to define semantics, presentation, and behavior, and this means we must choose one single implementation to serve to everyone.
> — [Sarah Higley](https://www.24a11y.com/2019/select-your-poison/), Web Developer at Microsoft

Even Angular Material documentation says "The native `<select>` offers the best accessibility because it is supported directly by screen-readers."

Angular material custom listbox requires the Live Announcer overlay to be accessible, and [advises using a native `<select>` for accessibility](https://material.angular.io/components/select/overview).

> Angular Material also supports use of the native `<select>` element inside of `<mat-form-field>`. The native control has several performance, accessibility, and usability advantages.

Before you attempt to use one of these, be certain a native `<select>` is not an option and you understand the commitment for coding and testing across all platforms.

## Further reading

- [24 Accessibility : Select your poison](https://www.24a11y.com/2019/select-your-poison/)
- [WebAxe.org: Accessible Custom Select Dropdowns](https://www.webaxe.org/accessible-custom-select-dropdowns/)
- [WAI-ARIA listbox examples](https://www.w3.org/TR/wai-aria-practices-1.1/examples/listbox/listbox-collapsible.html)