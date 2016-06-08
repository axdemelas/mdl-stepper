# MDL Stepper

A library that implements to the [Material Design Lite](https://getmdl.io) a polyfill of stepper component specified by [Material Design](https://www.google.com/design/spec/components/steppers.html). The stepper polyfill will help you to implement this material design component today.
  
> As discussed at [#1748](https://github.com/google/material-design-lite/issues/1748) issue, the stepper is a component that is present in the Material Design specification and MDL has not support yet.

> While the Material Design Lite team works in other parts of the library, i decided to create my own component.

> Obviously, this is my interpretation of the spec and it does not reflect what the Material Design team would consider ‘correct’ but i tried to preserve as much of specified details.

> You can consider this as a polyfill to be used while the MDL do not include that. Maybe it can be useful and help other people to build their web apps.

### Use MDL Stepper on your site?

For addtional details go to 
[ahlechandre.github.io/mdl-stepper](https://ahlechandre.github.io/mdl-stepper/).

## Get Started

The MDL Stepper component was based on Material Design Lite (MDL) library. To use this component before you need to include the [MDL](https://getmdl.io) to your project.

### INCLUDE CSS & JAVASCRIPT

1. Choose the type of [download](http://getmdl.io/started/index.html#download) and include the Material Design Lite files to your all pages.

2. Get the CSS & Javascript files of MDL Stepper component.

3. Include the Material Design Lite + Stepper files.


### Basic Usage

```js
// Select your stepper element  
var stepperElement = document.querySelector('ul.mdl-stepper');
// Get the MaterialStepper instance of element to control it          
var myStepper = stepperElement.MaterialStepper;
// You can test
myStepper.next();
```

## Component

The types of steppers and steps are specified in [Material Design page](https://www.google.com/design/spec/components/steppers.html).

### Linear stepper
Linear steppers require users to complete one step in order to move on to the next. (Material Design)

![Linear stepper](content/gif/linear-stepper.gif)

### Non-linear stepper
Non-linear steppers allow users to enter a multi-step flow at any point. (Material Design)

![Non-linear stepper](content/gif/non-linear-stepper.gif)

### Stepper feedback
Steppers may display a transient feedback message after a step is saved. Stepper feedback should only be used if there is a long latency between  steps. (Material Design)

![Stepper feedback](content/gif/stepper-feedback.gif)

### Editable steps
Editable steps allow users to return later to edit a step. These are ideal for workflows that involve editing steps within a session. (Material Design)

![Editable steps](content/gif/editable-steps.gif)

### Optional steps
Optional steps within a linear flow should be marked as optional. (Material Design)

![Optional steps](content/gif/optional-steps.gif)

### Error state
![Error state](content/gif/error-state.gif)

## Introduction

"Steppers display progress through a sequence by breaking it up into multiple logical and numbered steps. Avoid using steppers to break up sections in a short form, or multiple times on one page". See the [Material Design specification page](https://www.google.com/design/spec/components/steppers.html).

### To include a component

Go to [component page](https://ahlechandre.github.io/mdl-stepper/component/index.html) for markup details.

### Configuration options

Class | Effect | Remarks
------|--------|------
```mdl-stepper```  | Defines a stepper container. |Required
```mdl-stepper--linear```  | Defines the stepper as linear and require users to complete one step in order to move on to the next. | Manually added
```mdl-stepper--feedback```  | Display a transient feedback message after a step is saved. | Manually added
```mdl-step```  | Defines a step item inside `mdl-stepper`. | Required
```is-active```  | Defines the active step. The first step will be marked as active if you don't set it. | Manually added
```mdl-step--optional```  | Defines a step as optional. | Manually added
```mdl-step--editable```  | Defines a step as editable after saved. | Manually added
```mdl-step__label```  | Defines the label section of step. | Required
```mdl-step__title```  | Defines title part of label. Must be inside a `mdl-step__label`. | Required
```mdl-step__title-text```  | Defines the text content of title. Must be inside a `mdl-step__title`. | Required
```mdl-step__title-message```  | Defines an addtional text to the title (e.g. Optional). Must be inside a `mdl-step__title`. | Manually added
```mdl-step__content```  | Defines the content section of step. | Required
```mdl-step__actions```  | Defines the actions section of step | Required

## Javascript API

All methods and custom events to the control over your stepper 

### Methods

Method | Effect | Return
------|--------|------
```MaterialStepper.next()```  | Complete the current step and move one to the next. Using this method on editable steps (in linear stepper) it will search by the next step without "completed" state to move. When invoked it dispatch the event onstepcomplete to the step element. | `boolean` - True if move and false if not move (e.g. On the last step)  
```MaterialStepper.back()```  | Move to the previous step without change the state of current step. Using this method in linear stepper it will check if previous step is editable to move. | `boolean` - True if move and false if not move (e.g. On the first step) 
```MaterialStepper.skip()```  | Move to the next step without change the state of current step. This method works only in optional steps. | `boolean` - True if move and false if not move (e.g. On non-optional step)
```MaterialStepper.error(message)```  | Defines the current step state to "error" and shows the `message` parameter on title message element. When invoked it dispatch the event onsteperror to the step element. | `undefined`
```MaterialStepper.goto(id)```  | Move "active" to specified step `id` parameter. The id used as reference is the integer number shown on the label of each step (e.g. 2). | `boolean` - True if move and false if not move (e.g. On id not found)
```MaterialStepper.getActiveId()```  | Get the current "active" step element id on the stepper. The `id` used as reference is the integer number shown on the label of each step (e.g. 2). | `number`  
```MaterialStepper.getActive()```  | Get the current "active" step element on the stepper. | `HTMLElement`   

### Custom Events

Event | Target | Fired
------|--------|------
```onstepcancel```  | .mdl-step | 	When the step action button/link with `[data-stepper-cancel]`  attribute is clicked.
```onstepcomplete``` | .mdl-step | When `MaterialStepper.next()` method is called on step and it returns `true`.
```onsteperror``` | .mdl-step | When `MaterialStepper.error(message)` method is called on step.
```onstepnext``` | .mdl-step | When the step action button/link with `[data-stepper-next]` attribute is clicked.
  ```onstepskip``` | .mdl-step | When the step action button/link with `[data-stepper-skip]` attribute is clicked.
```onsteppercomplete``` | .mdl-stepper | When all required steps are completed. Optional steps are ignored for dispatch this event.

## Help wanted

* Horizontal type support
* [Cross-browser styles](https://github.com/ahlechandre/mdl-stepper/issues/1)

## License 

[MIT License](https://github.com/ahlechandre/mdl-stepper/blob/gh-pages/LICENSE) © 2016 Alexandre Thebaldi
