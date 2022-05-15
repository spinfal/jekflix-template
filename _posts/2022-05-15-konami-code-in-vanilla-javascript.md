---
date: 2022-05-15 15:34:36
layout: post
title: "Konami Code in vanilla JavaScript "
subtitle: Up, Up, Down, Down, Left, Right, Left, Right, B, A
description: Making a Konami code easter egg in plain, vanilla JavaScript. No
  external libraries are needed.
image: https://cdn.discordapp.com/attachments/788198099067076638/975519387308142653/unknown.png
optimized_image: https://media.discordapp.net/attachments/788198099067076638/975519387308142653/unknown.png
category: "{{slug}}"
tags:
  - konami
  - code
  - js
  - javascript
  - html
  - website
  - frontend
  - simple
  - vanilla
  - easy
author: spin
paginate: false
---
## The Konami Code

Long ago when an NES game called [Gradius](https://www.mobygames.com/game/nes/gradius) was released, it came with a cheat code that would be known to many as the *Konami Code.* This code was implemented by the developer to help make the game easier, it would provide many different power-ups. Now, [many other games](https://www.riddlester.co/games-that-support-konami-code/) support the Konami Code and it has become another pop-culture reference that even [websites have begun to use](https://nick.boldison.com/websites/konami-code-sites-that-use-the-konami-code/).

## Developing the Konami Code in JS

Creating the Konami code in JavaScript and making it work with HTML wasn't extremely difficult to do. It took some thinking, but I managed to put my singular brain cell into overdrive and create a simple and short script.

### Defining the keys

First, I began by defining the Konami Code keys `(up up down down left right left right b a)` and the starting index, which is `0`

```javascript
const keys = {
    index: 0,
    konami: ["ArrowUp", "ArrowUp", "ArrowDown", "ArrowDown", "ArrowLeft", "ArrowRight", "ArrowLeft", "ArrowRight", "b", "a"]
};
```

### Document keyup event listener

After defining the keys, I created an event listener which would listen for "`keyup`" events on the document. This allows us to check if the correct keys were pressed or not.// konamiCode function will be explained in the next section

```javascript
document.addEventListener("keyup", (e) => konamiCode(e)); 
// konamiCode function will be explained in the next section
```

### The Konami Code function

Now that we have the keys defined and the document event listener created, we can now begin work on the function that will check the keys and then run some code if the Konami Code is detected.

```javascript
function konamiCode(e) {
    if (e.isTrusted) {
        if (keys.konami[keys.index] === e.key) {
            if (keys.index == 9) {
                keys.index = 0;
                return alert("Konami!"); // this line can be replaced to run whatever code you need it to run
            } else {
                keys.index++;
            }
        }
    }
}
```

Here's what's happening in this function:

1. We check if the event is trusted, meaning that the rest of the code will only run if a user has pressed a key (this is not needed, it can be removed if you wish)
2. We then check if the current index in the Konami keys array is equal to the current event key that has been pressed by the user
3. If they are equal, then we check if the current index is equal to `9`, which is the amount of Konami keys that we are using
4. When the index is equal to `9`, we reset the index to `0` and run the code. If the index is not equal to `9`, then no more code is run and we just add `1` to the index

### Now we put it all together

Finally, we can put the JS code altogether and see our result

```javascript
"use strict";

const keys = {
    index: 0,
    konami: ["ArrowUp", "ArrowUp", "ArrowDown", "ArrowDown", "ArrowLeft", "ArrowRight", "ArrowLeft", "ArrowRight", "b", "a"]
};

document.addEventListener("keyup", (e) => konamiCode(e));

function konamiCode(e) {
    if (e.isTrusted) {
        if (keys.konami[keys.index] === e.key) {
            if (keys.index == 9) {
                keys.index = 0;
                return alert("Konami!");
            } else {
                keys.index++;
            }
        }
    }
}
```

## JSFiddle Preview with website

<iframe width="100%" height="300" src="//jsfiddle.net/spinfal/jc4ot2qf/1/embedded/js,html,result/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>