# The Chillout App
*A modern web radio platform.*

Although nowadays we mostly enjoy our favorite radios online, we miss the ease of using the FM tuner to swap to that other
station and satisfy our music taste intricacies; web radios are scattered and those pages that try to gather them into one place
are rather primitive and non-interactive.

This app is an attempt to solve this problem by introducing a contemporary and interactive platform that combines a customizable
collection of radios and an audio player in a single lightweight page, promising a modern and refined experience.

### Usage
Simply click on a radio you like and enjoy the music! [Take me to the chillout.](https://kostaslib.github.io/chillout/)

## Animation States and Event Listeners
Basic interactive items (event targets) have three different states that can be activated (i.e. styles that can be applied).Each state has its own event listener and is activated by an event handler function.
- **Idle:** This is the default state of an item when it is not interacted with. This state is also activated by the ```changeToIdle()``` method when an item loses focus (bound to *.onmouseout*).
- **Hover:** This state is activated when the user hovers the mouse over the item, to indicate that the item is interactive. Activated by the```changeToHover()``` method (bound to *.onmouseenter*).
- **Active:** This state is activated when the user clicks on an item. Activated by the ```changeToActive()``` method (bound to *.onmousedown*).

An item can stay in the **active** state either momentarily, only to provide the animation, or until it is deactivated. The main features of the app stay in their active state until directed otherwise. For this reason, the active state is the most prominent state, meaning that:
1. When an item is **active**, other event listeners stop listening to raised events.
2. Only one item of the same type (i.e. ```<div class = "radio-item">```) can be active at any time. If a similar item is already active, it will be deactivated.

Some items, however, can enter a fourth state which is activated when an already ***active*** item gets ***hovered***. This state, namely **Active-hover**, provides visual feedback to the user that when clicked, this item will be deactivated.

**Active-hover** is a different state than **hover** in that it can be trigerred only when an item is already **active**, its styles override the **active** styles and when the item leaves the **active-hover** state, it returns to **active**. This state should also be activated when the ```.onmouseenter``` event is raised.

To help ```changeToHover()``` decide which of the two states to activate, the ```.hasActiveHover``` property is introduced. This property takes a ```Boolean``` value and can be passed as an optional arguement to the constructor. If not specificed, ```hasActiveHover``` defaults to false, which invokes the default behavior referenced in the three basic states.
