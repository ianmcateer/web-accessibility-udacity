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