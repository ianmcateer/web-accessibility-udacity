# Contents

1. Introduction to focus
2. What is focus
3. Experiencing focus
4. DOM Order Matters
5. Fixing DOM Order
6. using tab Index

## Introudction to Focus

focus refers to control on computer screen where you receive input from the keyboard and from the cliboard when you paste

probably familiar with focus for text fields

focus for text fields- in order to type in a text field have to go over with your mouse and click on it

that act of clicking on the text field is what actually focuses it 

if press tab will move focus to next field

some users driver the computer entirely with the keyboard or some other type of discrete input device

WEB AIM WCAG 2.0 Checklist
2.1.1 all page functionality should be available using the keyboard, unless the functionality cannot be accomplished in any known way using a keyboard
like free hand drawing

## What is Focus

focus detrmines where keyboards events go in the page

often indicated by a focus ring 

as a user you can control which elements is currently focused using your keyboard 

pressing tba key will move focus through the document 

sift tab moves focus backwards 

arrow keys to move focus within a component 

- having logical tab order is important step

input button and select are all implicitly focusable 

not all elements are focusable tho - eg paragraph, images

generally no need to something if a user cant interact with it or provide it some sort of input

## Experiencing Focus

search for ticket on audacity new airline on keyboard

this website has disable dmouse on the page 

http://udacity.github.io/ud891/lesson2-focus/01-basic-form/ 

Be a round trip
To Melbourne
Leaving on 10/12/2017
Returning on 10/23/2017
In a window seat
and you DO NOT want to receive promotional offers!

## DOM Order Matters

working with antive elements is great for focus behaviour bc they are automatically inserted 
into the tab order because they are automatically inserted into the tab order based on their position in the DOM

but using css can change order on screen than whats in the DOM eg floats, flexbox

even thoguh the visual order has changed the DOM order remains the same 

how does this affect tabbing? will mess with the tabbing 

BE CAREFUL WHEN USING CSS TO CHANGE POSIITON OF ELEMENTS ON SCREEN BC THIS CAN AFFECT TAB ORDER

1.3.2 the reading and navigation order should be logical and intuitive 

## Fixing DOM Order

replace the div used as a footer with the footer tag
that way screen readers 

doing so can benefit screen readers who rely on these kind of landmarked elements to navigate the page

## Using Tab Index

because native elements are automatically inserted in the tab order they can be very convenient to use

but there are instances when you will want to modify the tab order 
like if you are building a component without a native analog like this dropdown here

or if you need to have something off screen that should only be focusable when it appears like perhaps a modal window 

you can use the `tabindex` attribute
can be applied to any HTML element and it takes a range of numberic values

-1 means the elemenet will not be in the tab order but it can be programatically focused via jaavscript 
by calling the elements `focus()` method. this is useful for off screen content that appears on screen. when the content gets displayed you may wish to call its focus method which will direct future keyboard events to it 

tab index of 0 will add the element to the tab order and that element can be programatically focused

tab index greater than 0 will jump the eleement to the front of the tab order (ANTI-PATTERN!) its discouraged, can be confusing for screen reader

https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex 

https://www.w3.org/TR/html5/editing.html#sequential-focus-navigation-and-the-tabindex-attribute 

## Deciding What is Focus

tmepting when starting to add tab index to seemingly important elements - counter productive elements

normall only want to add focus behaviour to interactive eleemnts such as buttons tabs drop downs or anything user provide input to 

if worried about visually impaired users missing out on content dont be we will learn how screen reader users explore non interactive content 

- is this something the user is going to interact withz?

## Which Elemenets should have focus?

typically only add tabindex attributes to interactive elements, and not to our site content 

- header links
- search input
- call to action button
- footer links 

## Managing focus

as general rule shouldnt add tab index to site content as a general rule 
but one exception - when manipulating the page in response to a user action 

user might click menu item and the page does one of the animated scroll down to that particular section

or if SPA clicking on one of the nav links changes the content of the page without doing the full page refresh

in these situations pick an approporate header, give it a tab index of negeative one so it doesnt appear in the natural tab order, and call its focus method 
after th euser has taken their action . this process is called managing focus 

it keeps the users interactive context in sync with the visual representation of the state 

---

example: in spa click on a link in the nav, content changes automatically, and would like to click a link in the content

but to click this click in order to get there i have to tab through my navigation 

take the header, give tab index of negative one, but can programatically focus it using javascript, now i can listen for my anchor clicks, tell the page content to update, and lastly call the focus method on that header - user willbe moved in here inside content and can quickly tab to whatever they want 

as we do this might notice the header gets a large focus ring placed around it - can work around this styling issue 

## Managing Focus Yourself 

- goal is to make the heading properly focused when the user cicks a navigation link 

`magaing-focus` folder is the one contains this excercise

need to use a local server for this excercise- https://chrome.google.com/webstore/detail/web-server-for-chrome/ofhbbkphhbklhfoeikjpcbhemlocgigb?hl=en 

launch the app - go to settings, make sure choose the folder
then click on the server url 

inside each section of the page going to find an appropriate header 

```html
<section class="section--center mdl-grid mdl-grid--no-spacing is-active">
          <div class="mdl-cell mdl-cell--12-col">
            <h2>What is Vegemite?</h2>
            Minim duis incididunt est cillum est ex occaecat consectetur. Qui sint ut et qui nisi cupidatat. Reprehenderit nostrud proident officia exercitation anim et pariatur ex.
```
and give them a tabindex of negative 1 so that is doesnt mess up the natural tab order 

```html
<section class="section--center mdl-grid mdl-grid--no-spacing is-active">
          <div class="mdl-cell mdl-cell--12-col">
            <h2 tabindex="-1">What is Vegemite?</h2>
            Minim duis incididunt est cillum est ex occaecat consectetur. Qui sint ut et qui nisi cupidatat. Reprehenderit nostrud proident officia exercitation anim et pariatur ex.

```

then open up router code in main.js whenever page changes ill look for a new header and calling its focus method

to preent code from running whenever add a guard variable isFirstPage and set it to false whenever the first page runs 

```js
var isFirstPage = true;


page('/', function() {
  page.redirect('/what-is-vegemite');
});


page('/:slug', function(context) {
  // This will match any value after the first / in the url. For example, if
  // the url was /foo, the value of slug would be "foo".
  var slug = context.params.slug;

  // Remove is-active class from previous menu item and section
  var oldMenuItem = document.querySelector('#menu .is-active');
  var oldPage = document.querySelector('main .is-active');
  oldMenuItem.classList.remove('is-active');
  oldPage.classList.remove('is-active');

  // Add is-active class to new menu item and section using the URL slug
  var newMenuItem = document.querySelector('#menu [data-page='+slug+']');
  var newPage = document.querySelector('main [data-page='+slug+']');
  newMenuItem.classList.add('is-active');
  newPage.classList.add('is-active');

  // If this is the first time someone is visiting the site, don't move focus
  // around. Wait until they have clicked a menu item
  if (isFirstPage) {
    isFirstPage = false;
    return;
  }

  // Move focus to a heading in the new page
  newPage.querySelector('h2').focus();

});
```

when you give something a tabindex it means that element is focuable 

are elements naturally fofusable eg form elements 

removing tabindex will mean that its not focusable anymore 

the numbers have meaning

anything above 0 when you tab the values you put- all the positive integers will be the seuqnce the tab seuqnce uses 

following that anything with tabindex 0 - the order will be the order they are in the html

-1 never gets selected because it has -1 can prevent somebody from tabbing to an element 

be careful with messing with the accessiblity, careful about taking an element not normally focusable and giving a tab index , if turning div into a button you are defeating its purpose

---

0 inserts an element into the natural tab order. The elemenet can be focused by pressing the tab key and the element can be focused by calling its focus() method

-1 removes an element from that natural tab order, but the element can still be focusable by calling its focus method 

anythign greater than 0 jumps the eleement to the front of the natural tab order. BUT USING A TAB INDEX GREATER THAN 0 IS CONSIDERED AN ANT PATTERN

if cant interact with it generally no reason to make it focusable. 

## Skip Links

most websites the main content is usually not the first thing in the DOM, instead we often begin with navigation, hamburger menus, page scaffolding

this means keyboard and screen reader users must first navigate all this content before they can get at the actual heart of the page 

for users with motor impariements this is espceically fristrating 

a user whos unable to move their arms might be navigating by using a switch devide- which they use by tapping their head , they will haveto tap over and over again to get to content

easy to impeenent solution - create a hidden link that allows keyboard and switch device users to jump straight to page content

these links are often referred to as skip links 

when press tab- presented with option asking if want to skip down to main content 
pressing enter willmove focus down to main content area 

```html
<a href="main-content" class="skip-link">Skip to main content</a>
```
http://webaim.org/techniques/skipnav/
https://developers.google.com/web/updates/2016/03/focus-start-point?hl=en

the href refers to an id of another element on the page

want the skip link to appear early in the DOM so going to put it before the navigation

then give say the main element that id 

i newer versions of chrome and firefox just doing this will allow you to move focus down to the main elemenet when the skip link is pressed
for older browsers which dont move focus when named anchors are clicked going to want to add a tab index of -1 to the main element 

then in css can make sure the skip link has an abolute posiiton so it can appear in top left corner of the screen  

but going to make it iniitally positioned off screen by setting the top value to -40 pixels and then use the :focus class to move the element back on screen 

```css
.skip-link {

    position: absolute;
    top: -40px;
    left: 0;
    background: #BF1722;
    color: white;
    padding: 8px;
    z-index: 100;
}

.skip-link:focus {
    top: 0;
}
```

## Focus in Complex Components

The ARIA Authoring Practices doc (or "ARIA Design Patterns doc") is a great resource for figuring out what kind of keyboard support your complex components should implement.

https://www.w3.org/TR/wai-aria-practices/

maye youll need to manage focus at the component level as well not just when nvaigate the page

## KeyBoard Design Components

custom component which resembles a radio group

https://www.w3.org/TR/wai-aria-practices/#aria_ex 
https://www.w3.org/TR/wai-aria-practices-1.1/#radiobutton

using technique called roving focus

setting tab index to -1 for all the children and 0 for the currently active item 

us ekeyboard listener to determine which key the user has pressed, then we set tab index on the slected item to 0 , set focus on item and set checked, when reach bottom of lsit then wrap back around

## Implementing Keyboard Event Listeners


Using the aria authoring best practices doc, find tne radio pattetn and implement support for the down arrow and right arrow pattern using the "roving focus" technique.

## OFF Screen Content

what do you do when content isnt on screen yet but is still in the DOM? 

eg responsive drawer panel

common ui pattern

sometimes will be tabbing and dont know where focus is- focus might be hiding behind a drawer pattern
might occasionaly find focus suddenly dissapears

in console can log the document active element 

```
document.activeElement
```

gives reference to currently focused element 

another option is to use chrome accessiblity dev tools extention- inspector whcih will show accesibility propertes of an element as well set of accessiblity audits 

could set to display none or visibility hidden using css wheneve rits off screen to prevent focus from being able to movie inside that element 

then can set it to display block or visibility visible 

## Implementing Offscreen Content

had to set the modal to display none in the excercise

## Modals and Keyboard Tips

keyboard trap can be very frustrating for users

2.1.2 keyboard focus should never be locked or trapped at one particular page element

BUT 
times when this is desirable eg modal window wont want users to be able to access any of the content behind it 

overlay wont stop focus from travelling outside of the modal

would want a temporary keyboard trap