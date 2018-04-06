# CSS Animation

## animation

CSS Animations is a module of CSS that lets you animate the values of CSS properties over time.

To style the element you want to animate with the animation property or its sub-properties. This lets you configure the timing, duration, and other details of how the animation sequence should progress. This does not configure the actual appearance of the animation, which is done using the @keyframes

```css
p {
  animation-duration: 3s;
  animation-name: slidein;
  animation-iteration-count: infinite;
  animation-direction: alternate;
}
```
Which can be written in short form

```css
p {
  animation: 3s infinite alternate slideIn;
}
```

Actual animation will written using @keyframes. Where 0% indicates the first moment of the animation sequence, while 100% indicates the final state of the animation. Because these two times are so important, they have special aliases: **from and to**. Both are optional. If **from/0% or to/100%** is not specified, the browser starts or finishes the animation using the computed values of all attributes.

```css
@keyframes slidein {
  0% {
    margin-left: 100%;
    width: 300%; 
  }

  100% {
    margin-left: 0%;
    width: 100%;
  }
}
```
Then **animation** has following sub-properties
  1. animation-delay

  2. animation-direction

  3. animation-duration

  4. animation-name

  5. animation-timing-function

  6. animation-fill-mode

## Making text slide across the browser window

```css
p {
  animation-duration: 3s;
  animation-name: slidein;
}

@keyframes slidein {
  from {
    margin-left: 100%;
    width: 300%; 
  }

  to {
    margin-left: 0%;
    width: 100%;
  }
}
```
## Adding another keyframe

```css
p {
  animation-duration: 3s;
  animation-name: slidein;
}

@keyframes slidein {
  0% {
    margin-left: 100%;
    width: 300%; 
  }
  
  75% {
    font-size: 300%;
    margin-left: 25%;
    width: 150%;
  }

  100% {
    margin-left: 0%;
    width: 100%;
  }
}
```
## Making it repeat

```css
p {
  animation-duration: 3s;
  animation-name: slidein;
  animation-iteration-count: infinite;
}
```
## Making it move back and forth

```css
p {
  animation-duration: 3s;
  animation-name: slidein;
  animation-iteration-count: infinite;
  animation-direction: alternate;
}
```
## Setting multiple animation property values
The CSS animation longhand values can accept multiple values, separated by commas — this feature can be used when you want to apply multiple animations in a single rule, and set separate durations, iteration counts, etc. for the different animations.

we have three animation names set, but only one duration and iteration count. In this case all three animations are given the same duration and iteration count:
```css
animation-name: fadeInOut, moveLeft300px, bounce;
animation-duration: 3s;
animation-iteration-count: 1;
```
we have three values set on all three properties. In this case each animation is run with the corresponding values in the same position on each property,

```css
animation-name: fadeInOut, moveLeft300px, bounce;
animation-duration: 2.5s, 5s, 1s;
animation-iteration-count: 2, 1, 5;
```
In third case, there are three animations specified, but only two durations and interation counts. In such cases where there are not enough values to give a separate value to each animation, the values cycle from start to finish. So for example, fadeInOut gets a duration of 2.5s and moveLeft300px gets a duration of 5s. We’ve now got to the end of the available duration values, so we start from the beginning again — bounce therefore gets a duration of 2.5s. The iteration counts (and any other property values you specify) will be assigned in the same way.

```css
animation-name: fadeInOut, moveLeft300px, bounce;
animation-duration: 2.5s, 5s;
animation-iteration-count: 2, 1;
```
## Using animation events
You can get additional control over animations — as well as useful information about them — by making use of animation events. These events, represented by the AnimationEvent object, can be used to detect when animations start, finish, and begin a new iteration. Each event includes the time at which it occurred as well as the name of the animation that triggered the event.
```css
.slidein {
  animation-duration: 3s;
  animation-name: slidein;
  animation-iteration-count: 5;
  animation-direction: alternate;
}

@keyframes slidein {
  from {
    margin-left:100%;
    width:300%
  }
  
  to {
    margin-left:0%;
    width:100%;
  }
}
```
```javascript
var e = document.getElementById("watchme");
e.addEventListener("animationstart", listener, false);
e.addEventListener("animationend", listener, false);
e.addEventListener("animationiteration", listener, false);

e.className = "slidein";
function listener(e) {
  var l = document.createElement("li");
  switch(e.type) {
    case "animationstart":
      l.innerHTML = "Started: elapsed time is " + e.elapsedTime;
      break;
    case "animationend":
      l.innerHTML = "Ended: elapsed time is " + e.elapsedTime;
      break;
    case "animationiteration":
      l.innerHTML = "New loop started at time " + e.elapsedTime;
      break;
  }
  document.getElementById("output").appendChild(l);
}
```

```html
<h1 id="watchme">Watch me move</h1>
<p>
  This example shows how to use CSS animations to make <code>H1</code>
  elements move across the page.
</p>
<p>
  In addition, we output some text each time an animation event fires,
  so you can see them in action.
</p>
<ul id="output">
</ul>
```
## @keyframes
The @keyframes CSS at-rule controls the intermediate steps in a CSS animation sequence by defining styles for keyframes (or waypoints) along the animation sequence. This gives more control over the intermediate steps of the animation sequence than transitions.

```css
@keyframes identifier {
  0% { top: 0; left: 0; }
  30% { top: 50px; }
  75%{ left: 50px; }
  100% { top: 100px; left: 100%; }
}
```

```css
@keyframes <keyframes-name> {
  <keyframe-block-list>
}
where 
<keyframes-name> = <custom-ident> | <string>
<keyframe-block-list> = <keyframe-block>+

where 
<keyframe-block> = <keyframe-selector># {
  <declaration-list>
}

where 
<keyframe-selector> = from | to | <percentage>
```
## animation
The animation CSS property is a shorthand property for the various animation properties: animation-name, animation-duration, animation-timing-function, animation-delay, animation-iteration-count, animation-direction, animation-fill-mode, and animation-play-state.

```css
#circle {
    background-color: #1766aa;
    margin: 20px;
    border: 5px solid #333;
    width: 150px;
    height: 150px;
    border-radius: 50%
}

@-webkit-keyframes slidein {
    from {
        margin-left: -20%
    }

    to {
        margin-left: 100%
    }
}

@keyframes slidein {
    from {
        margin-left: -20%
    }

    to {
        margin-left: 100%
    }
}
```
#1
```css
animation: slidein 3s ease-in 1s infinite reverse both running;
```
#2
```css
animation: slidein 3s linear 1s infinite running;
```
#3
```css
animation: slidein 3s linear 1s infinite alternate;
```
#4
```css
animation: slidein .5s linear 1s infinite alternate;


```html
<div id="circle"></div>
```

```css
/* @keyframes duration | timing-function | delay | 
iteration-count | direction | fill-mode | play-state | name */
animation: 3s ease-in 1s 2 reverse both paused slidein;

/* @keyframes duration | timing-function | delay | name */
animation: 3s linear 1s slidein;

/* @keyframes duration | name */
animation: 3s slidein;
```
Reference example from [MDN](https://interactive-examples.mdn.mozilla.net/pages/css/animation.html).

### Gmail like Loader Animation

```css
@keyframes slidein {
  from { transform: scaleX(0); }
  to { transform: scaleX(1); }
}

.a1 { animation: 3s ease-in 1s 2 reverse both paused slidein; }
.a2 { animation: 3s linear 1s slidein; }
.a3 { animation: 3s slidein; }

.animation {
  background: #3F87A6;
  width: 100%;
  height: calc(100% - 1.5em);
  transform-origin: left center;
}
```
```html
<div class="animation a1"></div>
<div class="animation a2"></div>
<div class="animation a3"></div>
```
Reference example from [MDN](https://mdn.mozillademos.org/en-US/docs/Web/CSS/animation$samples/animation?revision=1367951).
#### Formal syntax
```css
<single-animation>#
where 
<single-animation> = <time> || <single-timing-function> || <time> || <single-animation-iteration-count> || <single-animation-direction> || <single-animation-fill-mode> || <single-animation-play-state> || [ none | <keyframes-name> ]

where 
<single-timing-function> = linear | <cubic-bezier-timing-function> | <step-timing-function> | <frames-timing-function>
<single-animation-iteration-count> = infinite | <number>
<single-animation-direction> = normal | reverse | alternate | alternate-reverse
<single-animation-fill-mode> = none | forwards | backwards | both
<single-animation-play-state> = running | paused
<keyframes-name> = <custom-ident> | <string>

where 
<cubic-bezier-timing-function> = ease | ease-in | ease-out | ease-in-out | cubic-bezier(<number>, <number>, <number>, <number>)
<step-timing-function> = step-start | step-end | steps(<integer>[, [ start | end ] ]?)
<frames-timing-function> = frames(<integer>)
```
## animation-delay
The animation-delay CSS property specifies when an animation should start. You can begin the animation at a future point in time, immediately and from its begining, or immediately and partway through the animation cycle.
```css
#circle {
    background-color: #1766aa;
    color: #fff;
    margin: auto;
    margin-left: 0;
    border: 5px solid #333;
    width: 150px;
    height: 150px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column
}

#playstatus {
    font-weight: 700
}

.animating {
    animation-name: slide;
    animation-duration: 3s;
    animation-timing-function: ease-in;
    animation-iteration-count: 2;
    animation-direction: alternate
}

@-webkit-keyframes slide {
    from {
        background-color: orange;
        color: #000;
        margin-left: 0
    }

    to {
        background-color: orange;
        color: #000;
        margin-left: 80%
    }
}

@keyframes slide {
    from {
        background-color: orange;
        color: #000;
        margin-left: 0
    }

    to {
        background-color: orange;
        color: #000;
        margin-left: 80%
    }
}

/*****First ****/
animation-delay: 250ms;
/*****Second ****/
animation-delay: 2s;
/*****Third ****/
animation-delay: -2s;
```
