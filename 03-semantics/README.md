# Contents

1. Intro
2. Assistive Technology
3. Affordances

## Intro

prev how to make things accessible for anyone who cant use a mouse or pointing device
whether that be because of some type of phsyical impariement
or simply personal preference

- how do we build websites who cant see at all?
- will look at screen readers

## Assistive Technology

ublrella term for a broad range of devices, software and tools that help anyone with a disability compelte a task

eg robitic prethsis, custom designed game controller or add on like a chrome extension

people may use screen reader, braille display, maginfication, eye tracking, voice control, switch access, sip and puff, eye tracking

## Affordances

affordances represent the actions we can take but more metaphorcial eg buttons, and sliders

eg checkbox is obvious to an user what it is

## Experiencing Affordances

affordances eg "THis is a yes/no option", "I can choose one option"

## Semantics and Assisitve Technology

someone who cant see the screen cant see visual informaiton in the interface

need to make sure information is expressed in a way which is flexible enough to be accessed programatically by assistive technology

refer to this as expressing the semantics of an element

2.0 checklist 4.1.2: name, role, markup is used in a way that facilitates accessibility

wcag checlist 4.1.2: name, role, value - for all user interface components, the name and role can be programaticlaly determined; states, properties and values that can be set by the user can be programaticlaly set

what are name, role and value??

in course mostly working with screen readers,but alot of work we do to support screen readers also benefits users who use other assistive technologies, things like voice control and switch control use the same semantics

## Experience using a screen reader

http://udacity.github.io/ud891/lesson3-semantics-built-in/02-chromevox-lite/

## Role Name Value

a screen reader largely creates the user interface for a user, based on the programatically expresed semantics

instead of a visual ui the screen reader provides autidorty reader

screen reader tells you

- what type of elemenet it is eg role
- the element names if it has one
- the value if it has one
- any information about the state

1. role
2. name
3. state
4. value

## The Accessibility Tree

Imagine building screen interface for screen readers only

how would you express a form interface?

eg "round trip, selected, radio button"

for a screen read user the screen reader is what provides the affordances without caring abotu the visual styling

the browser takes the DOM tree and turns it into a form that is useful to assistive technology, refer to this as the accessibility tree

## MAtching A Simple DOM and A11Y Tree

## Semantics in Native HTML

so we have the dom tree and we know the browser transofmrs it into the accessiblity tree

can do this bc the dom has implcit semantic meaning , the DOM is using standard native HTML elements that are automatically recognised by browsers and were predictably on a variety of platforms

accesbility for native html elements such as the standard link or button is handled automatically well

we can take advatage of that built in accessibility by writing HTMl that expresses the semantics of our page directly

## Writing Semantic HTML Quiz

goal for this excericse is to re-write the code so that its more semantic in nature

`writing-semantic-html`

will see the element is not actually a button

when we dont use a button the screen reader has no idea what button it landed on

simply replace the div with a button

## Writing Semantic HTML: The Name Game

earlier we saw that screen readers will announce an elements role, name state and value not necessarily in that order

by using the right semantic element weve got the role state and value covered BUT
we also need ot make sure that we are making elements name discoverable

very first item on web aims checklist - provide text alternatives for any non-text content: http://webaim.org/standards/wcag/checklist#g1.1

label interchangeably refers to Name in this context

there are two types of labels: visible and text alternatives

by its nature a text alternative is usually not displayed on the page

eg form buttons have a descriptive value - the button usually has some text content and that acts as the buttons text alternative

next we need to check that form inputs have associated text labels

when we create a form input and just put some text next to it, we get a visual label, but we didnt actually create
a programatically accessible label for the element we are trying to label , also dont get nice behaviour where we can click the label to focus on the input

can fix this by wrapping the input element in a label or we can use the for attribute on the label, if we do that we need to make sure we give the input element an id and use the same id as the value

## Labelling Input ELements

this form mostly marked up well but one form element with label not labelled correctly

`labelling-input-elements` lesson

```html
<div class="inline-control sign-up col-1">
  <input type="checkbox" checked name="jLetter" id="jLetter" /> Receive
  promotional offers?
</div>
```


## Text Alternative

we can use alt alternative to write 

we need to figure out what role the image plays in the page to figure out what kind of text alternative it should have 

alt used if fails ot load as well, web crawling bot, or a screen reader user 

alt differs from any other type of caption including title 
title will provide xtra content to the image rather than alternative 


alt needs to convery same thing as the image in the given context

imagine all images are broken- can you still understand the page content?

maginfying glass logo inside search link - 
but if inspect linkas whole heard mangifying glass search, might need to use empty alt text

empty alt text actually removes the image from the accessibility tree so the image is skipped by the screen reader

## Labelling Images with Alt Text

if the img is purely decorational eg picture inside a button might not need alt text

also if the link text is same as alt text might not need the alt text
