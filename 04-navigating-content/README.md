# Contents

## Smeanitcs - Navigating Content

writing semanitc html gives it alot of accessibility out of the box
form fields, links and alot of complex behavious is given for free

how does a screen reader user actually find and read the information in the page

something like a newspaper front page not prctical to read through everything 

## Navigating With A Screen Reader

voiceover is favourtie screen reader

built into mac os 10 so its available on every mac computer 

start by turning voice over on - global shortcut key

cmd + f5

```
CMD+F5 to turn on VoiceOver on OS X
Normal keyboard operation (TAB, Shift+TAB, arrow keys etc.) work as normal with VoiceOver running
CMD+L to jump to address bar
CTRL+Option+U to open Web Rotor
Type search term with Web Rotor open to search within Web Rotor
CTRL + Option + ← ↑ ↓ → to explore content
CTRL + Option + CMD + H to move forward by heading
CTRL + Option + CMD + Shift + H to move backward by heading
```

can turn on page summary in mac settings

i start looking for hedings to make it easier to navigate 

web router allws me to see how many headings , browser throughthem and choose 

ctrl + option + u

order in which see headings is different that what you see on the web page
lvel indicates how prominent it is on the web page 

once select the heading 

think of headings like secitons of a web page 

can type heading and search heading

once press header focus will move to that heading 

ctrl + option + right arrow 

## Using Headings Effectively

1.3.2 meanigful sequance


order matters for focus order but also order read by screen reader


screen readers in general is intracting with the accesibility tree

```js
for (var i = 0, headings = $$('h1,h2,h3,h4,h5,h6');
     i < headings.length; i++) {
   console.log(headings[i].textContent.trim() + " " +  
               headings[i].tagName,
               headings[i]);
}
```

to log out the headings in the console

1.3.2: http://webaim.org/standards/wcag/checklist#sc1.3.2
2.4.10: http://webaim.org/standards/wcag/checklist#sc2.4.10
1.3.1: http://webaim.org/standards/wcag/checklist#sc1.3.1
2.4.1: http://webaim.org/standards/wcag/checklist#sc2.4.1
2.4.6: http://webaim.org/standards/wcag/checklist#sc2.4.6

## Other navigational Options

can also navigate by links, form controls and landmarks 

open web router- left arrow to links

```
CTRL+Option+U to open Web Rotor
← and → to change panes within Web Rotor
Type search term with Web Rotor open to search within Web Rotor
Enter to move VoiceOver focus to item from Web Rotor
CTRL + Option + Spacebar to activate link/button/other element
CTRL + Option + ← ↑ ↓ → to explore content
CTRL + Option + CMD + H to move forward by heading
CTRL + Option + CMD + Shift + H to move backward by heading
CTRL + Option + W to have a word spelled out
```

can also look at form controls on web rotor 

WebAIM's article on accesskey: http://webaim.org/techniques/keyboard/accesskey 

can spell a sentence letter by letter- ctr option w

## Link Text

link anti-patterns:

scrrren read should find links but some thigns can cause screen readers to miss links in the page:

- using a span with some link styling (not a link)
- anchor tag without a href attribute (you might think im a link but im not either) eg popular with spa for intrnal links

for anything that behaves like a link should absolutely use a tag with href

WebAIM checklist item 2.4.9: http://webaim.org/standards/wcag/checklist#sc2.4.9

adding href makes link show up in the links list , also means work with the keyboard
and can copy or bookmark the location 

link anti patterns :

1. - using a span with some link styling (not a link) or nchor tag without a href attribute (you might think im a link but im not either) eg popular with spa for intrnal links
2. something that is implemented using a link but is really more like a button 

```html
<a href="#" onClick="doSomething()">Do SOmething!</a>
```

in this situation should replace the anchor tag with a button tag and style it appropriately 

3. image used as link content 

```html
<a href="/">
        <img src="logo_watermark.svg">
</a>
```

for average sighted user this works fine becuase they can still understand what the link is for, however for an assisted technology this makes the link unusable 

can fix it by adding alt to make sure the link is exposed correctly to the assistive technology layer 
```html
<a href="/">
        <img alt="Udacity" src="logo_watermark.svg">
</a>
```
so this ensures screen reader can find the links 
but we also need ot make sure that once the linkmakes it it is also useful

WebAIM checklist item 2.4.9: http://webaim.org/standards/wcag/checklist#sc2.4.9 

one example of uninformative link text is "learn more" can change it to maake it "learn more about"

## Excercise Link text

fix the links o this page

http://udacity.github.io/ud891/lesson4-semantics-navigating/08-link-text/index.html

link click here doesnt tell me what happens when click it

add to order is a button whcih is fine 

logi is also a link- dev tools it has alt text so thats ok

problem- skips over as links, they are spans to look like tags


## Landmarks 

can also nagivate by landmark 

html5 intoruced new elements -to help us define the semantics of a region of the page rather than a single interactive element 
these are

- main: represent main content of the page
- header: either a page banner or a grouping element fir introductory section
- footer: can be either page footer or section footer
- nav- represents a section of apge links to toher pages or parts within page like a table of contents 
- article: for self contained sections of content like a blog entry, news article or forum close, handy test is whether its content will make sense in another context
- section: compeltely generic section of a document. typically has a heading inside it 
- aside: any content which is related to the content around it eg in article it might be a sidebar, often rendered as a sidebar

provides more info to screen readers- they dont have default styling 