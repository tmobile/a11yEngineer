---
layout: how-to-test
title: Forms
permalink: /how-to-test/form/
---

There are several types of HTML form fields and ensuring each type is accessible is crucial to enabling all users to fully engage with a site.

## <step-number>1</step-number> Input Fields
{: .divider }
Input fields allow users to provide information such as text, numbers and passwords. Keyboard and screen reader users should be able focus on each input field with their tab key, enter the relevant information, and tab away. 
<example>
{% include /examples/input-text.html %}
</example>

## <step-number>2</step-number> Checkboxes
{: .divider }
Checkboxes allow users to select one or more options from a list. Keyboard and screen reader users should be able to focus on each checkbox field with their tab key and use the enter or space keys to select or unselect the item. 
<example>
{% include /examples/input-checkbox.html %}
</example>

## <step-number>3</step-number> Radio Buttons
{: .divider }
Radio buttons allow users to select a single option from a list. Only one radio button in a group should be be selectable at a time. Keyboard and screen reader users should be able to focus on the group of radio buttons using the tab key. Arrow keys move focus between each radio option. Options can be automatically selected as they receive focus with the arrow keys, or they can be selected using the space key. Pressing tab navigates aways from the radio group. 
<example>
<fieldset>
  <legend>
    Choose a fruit
  </legend>
  <input type="radio" name="fruit" id="appleRadio">
  <label for="appleRadio">Apple</label>

  <input type="radio" name="fruit" id="bananaRadio">
  <label for="bananaRadio">Banana</label>

  <input type="radio" name="fruit" id="cherryRadio" checked>
  <label for="cherryRadio">Cherry</label>
</fieldset>
</example>

## <step-number>4</step-number> Select Fields
{: .divider }
Select fields allow users to select one or more options from an expandable list of options. Keyboard and screen reader users should be able to focus on the select using their tab key. The space key expands the list of options, the arrow keys traverse the options, and the space or enter keys make a selection. Escape collapses the list. 
<example>
{% include /examples/input-select.html %}
</example>

## <step-number>5</step-number> What to test for

### ✓ Ensure forms have persistent visible labels

<table class="column-2">
  <thead>
    <th scope="col">
      Pass
    </th>
    <th scope="col">
      Fail
    </th>
  </thead>
  <tbody>
    <tr>
      <td>
        <label for="persistentLabel">Persistent label</label>
        <input type="text" id="persistentLabel"/>
      </td>
      <td>
        <input type="text" placeholder="Impersistent label"/>
      </td>
    </tr>
  </tbody>
</table>

### ✓ Ensure forms can receive tab focus and have focus indicators

<table class="column-2">
  <thead>
    <th scope="col">
      Pass
    </th>
    <th scope="col">
      Fail
    </th>
  </thead>
  <tbody>
  <tr>
    <td>
        <input type="checkbox" id="accessibleCheckbox">
        <label for="accessibleCheckbox">Accessible Checkbox</label>
    </td>
    <td>
        <input style="display:none" type="checkbox" id="inaccessibleCheckbox">
        <label for="inaccessibleCheckbox">Inaccessible Checkbox</label>
    </td>
  </tr>  
  </tbody>
</table>

## ✓ Ensure forms meet color contrast requirements
<table class="column-2">
  <thead>
    <th scope="col">
      Pass
    </th>
    <th scope="col">
      Fail
    </th>
  </thead>
  <tbody>
  <tr>
    <td>
      <label style="margin-right:8px" for="passContrast">My border passes contrast</label>
      <input type="text" id="passContrast"/>
    </td>
    <td>
      <label style="margin-right:8px" for="failContrast">My border fails contrast</label>
      <input style="border:1px solid #00BD1F" type="text" id="failContrast"/>
    </td>
  </tr>  
  </tbody>
</table>

## ✓ Ensure interating with a form doesn't automatically or unexpectedly change context on the page without informing users
<table class="column-2">
  <thead>
    <th scope="col">
      Pass
    </th>
    <th scope="col">
      Fail
    </th>
  </thead>
  <tbody>
  <tr>
    <td>
      <label for="selectPass">
        Select a number
      </label>
      <select id="selectPass">
        <option value="None" selected disabled>Select a number</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
      </select>
      <button aria-disabled="true" class="button" id="submitSelectPassSelection" type="submit">Submit</button>
      <div role="alert" id="messagePass" style="display: none;">This was an expected submission!</div>
    </td>
    <td>
      <label for="selectFail">
        Select a number
      </label>
      <select id="selectFail">
        <option value="None" selected disabled>Select a number</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
      </select>
      <div id="messageFail" style="display: none;">This was an unexpected submission!</div>
    </td>
  </tr>  
  </tbody>
</table>

## ✓ Ensure required and/or optional forms are clearly indicated and announced as such 
<table class="column-2">
  <thead>
    <th scope="col">
      Pass
    </th>
    <th scope="col">
      Fail
    </th>
  </thead>
  <tbody>
  <tr>
    <td>
      <div >* = required field</div>
      <label for="userLastnamePass">* Last name</label>
      <input aria-required="true" type="text" id="userLastnamePass"/>
    </td>
    <td>
      <label style="color: red;" for="userLastnameFail">Last name</label>
      <input type="text" id="userLastnameFail"/>
    </td>
  </tr>  
  </tbody>
</table>

## ✓ Ensure related form fields are announced as grouped together
<table class="column-2">
  <thead>
    <th scope="col">
      Pass
    </th>
    <th scope="col">
      Fail
    </th>
  </thead>
  <tbody>
  <tr>
    <td>
<fieldset>
  <legend>
    Choose a properly grouped day
  </legend>
  <div>
  <input type="radio" name="dayPass" id="fridayRadioPass">
  <label for="fridayRadioPass">Friday</label>

  <input type="radio" name="dayPass" id="saturdayRadioPass">
  <label for="saturdayRadioPass">Saturday</label>

  <input type="radio" name="dayPass" id="sundayRadioPass" checked>
  <label for="sundayRadioPass">Sunday</label>
  </div>
  </fieldset>
      </td>
      <td>
    <fieldset>
    <div class="legend">
      Choose an incorrectly grouped day
    </div>
    <div>
      <input type="radio" name="dayFail" id="fridayRadioFail">
      <label for="fridayRadioFail">Friday</label>
      <input type="radio" name="dayFail" id="saturdayRadioFail">
      <label for="saturdayRadioFail">Saturday</label>
      <input type="radio" name="dayFail" id="sundayRadioFail" checked>
      <label for="sundayRadioFail">Sunday</label>
    </div>
    </fieldset>
    </td>
  </tr>  
  </tbody>
</table>

## ✓ Ensure any associated instructions or helper text is announced when tabbing to a form

<table class="column-2">
  <thead>
    <th scope="col">
      Pass
    </th>
    <th scope="col">
      Fail
    </th>
  </thead>
  <tbody>
  <tr>
    <td>
    <div>
        <input type="checkbox"
           id="deltaCheckboxCard"
           aria-describedby="descDelta" >
    <label for="deltaCheckboxCard">
      Delta
    </label>
    <div class="hint"
         id="descDelta">
      Delta is the fourth letter of the NATO alphabet.
    </div>
    </div>
    </td>
    <td>
    <div>
    <input type="checkbox"
           id="echoCheckboxCard">    
    <label for="echoCheckboxCard">Echo</label>
    <div class="hint"
         id="descriptionEcho">
      Echo is the fifth letter of the NATO alphabet.
    </div>
    </div>
    </td>
  </tr>  
  </tbody>
</table>

## ✓ Ensure there is proper error handling for required fields

<table class="column-2">
  <thead>
    <th scope="col">
      Pass
    </th>
    <th scope="col">
      Fail
    </th>
  </thead>
  <tbody>
  <tr>
    <td>
      <label for="goodErrorInput">Submit for a good error</label>
      <input aria-describedby="goodErrorInputError" type="text" id="goodErrorInput"/>
      <div id="goodErrorInputError" style="display: none; color: #E02D00;">
         I announce with the input
      </div>
      <button id="goodErrorInputSubmit" class="button" type="submit">Submit</button>
    </td>
    <td>
    <div>
      <label for="badErrorInput">Submit for a bad error</label>
      <input type="text" id="badErrorInput"/>
      <div id="badErrorInputError" style="display: none; color: #E02D00;">
        I do not announce with the input</div>
      </div>
      <button id="badErrorInputSubmit" class="button" type="submit">Submit</button>
    </td>
  </tr>  
  </tbody>
</table>

## Related WCAG
- 1.3.1 Info and Relationships
- 3.2.2 On Input
- 3.3.1 Error Identification
- 3.3.2 Labels or Instructions
- 3.3.3 Error Suggestion
- 3.3.4 Error Prevention
- 4.1.2 Name, Role, Value

## Resources
- [WebAIM: Creating Accessible Forms](https://webaim.org/techniques/forms/)
- [WebAIM: Accessible Form Validation and Error Recovery](https://webaim.org/techniques/formvalidation/)