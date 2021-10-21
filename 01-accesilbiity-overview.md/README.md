# Contents

1. Intro
2. What is accesibility
3. Understanding the diversity of users
4. using a screen reader
5. Checklists

## Intro

Alice Boxhall
Rob Dobson
Mike Wales

How make website accesible and usable by everyone 

often shorten it to a11y

- show how to improve accesibility with minimal effort
- how to use whats built into html to create more accesible and robust interfaces
- some advanced techniques 
- interfaces more dleightful and easy to use by everyone 

most developers hazy understanding a11y means

when we say is accesbile we are saying that the sites ocntent is avaiable to eveyone and the functonality can be operated by anyone

eveyone should be able to access it 

## What is Accesibility

can all relate to experience of using an interface which is not accesible
- whenever ruse desktop optomised site on a mobile devide
- seen this content is not available in your country 

some problems a site might have:
- low contrast might make it hard for low vision users to read
- labels not correctly associated with checkboxes, means user has to click the checkbox and not the label, plius screen read difficulty figuring out the association 

- mak elow contrast text darker, make labels associated with the inputs

## Understanding the diversity of users

Victor Tsaran - technology program manager- ensure products create are accesible regardless of ability and impact 

modern technologies make very easy for a developer to make a website thats difficult for someone whos blind to use

1. visual
2. motor
3. hearing
4. cognitive

temporalities
1. temporary
2. situational
3. permanent

vision disability
if no vision likely the user will be using a screen reader, sofrwtare to help hear the information on the screenor braille display to feel the on screen text 
many website visual in nature and lack keyboard navigation 

color vision deficiency
more people who have some problems with sight than completely blind
people with low visual acuity may be using large print text or maginfication, 
text to speech as well as various color contrast options
might have difficulty distinguishing red or green or blue or yellow
also might just be trying to use the computer in the sun or looking at a dodgy projector

motor or dexterity impariements
people migh tonly be using keyboard, head or eye tracking software, voice dictation, switches
might have abroken write, broken trackpad

hearing disability
also users with hearing imparimeents- some might be deaf or osme hearing
content that uses sound should use some visual alternative 

cognitie impariements
ADD, dyslexia or autism
might need screen zoomed in to see the content 
or minimal design to minimise distraction and cognotive load

2% of population has visual imparimeent (blind or difficulty seeing )
50% of population has some kind of clinically significant retractive error
8% males and 0.5% femaills some form of visual color deficiency
2% of adults have a hearing disability
4% have a cognitive disability (difficulaty rememebring, concentrating, or making decisions)

## How to use a screen reader
making screen reader faster might improve efficiency

groups.google.com/forum/#overview

lots of shortcut keys this website has

to use the built in screen reader, chromevox

1. turn on chromebook accesibility features

`ctrl + alt + z` to turn on chromevox on or off from any web page

on tablet press and hold `volume down + volume up` button for 5 seconds

## Checklists

need a roadmap for this journey

WCAG - WEB Content Accessibility Guidelines 2.0
set of guidelines and best practices put together by experts to answer question what accessibility means 

some countries mandate use of these guidleiens in their legal requirements

4 core pricniples (POUR)

1. Perceivable: just because something is perceivable with one sense like sight doesnt mean all users can perceive it
2. Operable: can users use ui components and navigate the content eg something requires hover interaction cannot be oeprated by someone who cant use a mouse or touch screen
3. Understandable: scan users understand the content and the user interface
4. Robust: robust enough for content to be consumed by wide range of users and does it work with assiested technology

WCAG can be overwhelimg

they have condensed it into a checklist
WebAIM accessibility checklist
Webbing checklist is a good summary

https://www.w3.org/TR/WCAG20/ 

http://webaim.org/standards/wcag/checklist

what actually matters is the user experience

guidleiens may be incomplete 

as long as project is meeting outlined criteria our users should have a positive experience 

## Conclusion

now create some accessible code
3 main topics:

1. focus and keyboard: hwo to make sure we build things that can be operated with a keyboard. important for people with motor impairmenets
2. semantics: make sure expressing interface in a robust way
3. Styling and visual design