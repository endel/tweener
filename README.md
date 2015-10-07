#tweener [![Build Status](https://secure.travis-ci.org/maurodetarso/tweener.png?branch=master)](https://travis-ci.org/maurodetarso/tweener)

Minimal Tweening Library for Games.

## Usage ##

```javascript
// Tweener is not singleton. You need to create the instance.
// Creating a Tweener instance with auto-update of 60 ticks per second:
var tweener = new Tweener(1/60);

// Tweening an object:
tweener.add(target).to({x:300, y:200}, 2, Tweener.ease.backOut);

// Killing tweens:
tweener.remove(target);
```

#### CHAINING ####
```javascript
// Dispatching a callback after completion:
tweener.add(target).from({x:300, y:200}, 2, Tweener.ease.elasticOut).then(method);

// Delaying tween start by 1 second:
tweener.add(target).wait(1).to({x:300, y:200}, 2, Tweener.ease.expoOut);

// Delaying the callback by 1 second:
tweener.add(target).to({x:300, y:200}, 2, Tweener.ease.quintOut).wait(1).then(method);

// Go, then come back:
tweener.add(target).to({x:300}, 2, Tweener.ease.sineOut).to({x:0}, 2, Tweener.ease.sineOut);

// Tweening targetB after targetA:
tweener.add(targetA).to({x:300}, 2, Tweener.ease.sineOut).add(targetB).to({x:300}, 2, Tweener.ease.sineOut);
```

#### MANUAL UPDATE ####
```javascript

// You can create Tweener instances without auto-update:
var tweenerA = new Tweener();
var tweenerB = new Tweener();

// Then, you need to call the update, passing the elapsed time:
tweenerA.update(elapesdTimeInSeconds);
tweenerB.update(elapesdTimeInMilliseconds);

// Added tweens will work with elapsed time format:
tweenerA.add(targetA).to({x:300, y:200}, 0.5, Tweener.ease.backOut); //seconds
tweenerB.add(targetB).to({x:300, y:200}, 500, Tweener.ease.backOut); //milliseconds
```

## Easing functions ##

Here is the list of available easing functions (thanks to [@mattdesl](https://github.com/mattdesl) for his [eases](https://github.com/mattdesl/eases) package):

```javascript
Tweener.ease.backInOut
Tweener.ease.backIn
Tweener.ease.backOut
Tweener.ease.bounceInOut
Tweener.ease.bounceIn
Tweener.ease.bounceOut
Tweener.ease.circInOut
Tweener.ease.circIn
Tweener.ease.circOut
Tweener.ease.cubicInOut
Tweener.ease.cubicIn
Tweener.ease.cubicOut
Tweener.ease.elasticInOut
Tweener.ease.elasticIn
Tweener.ease.elasticOut
Tweener.ease.expoInOut
Tweener.ease.expoIn
Tweener.ease.expoOut
Tweener.ease.linear
Tweener.ease.quadInOut
Tweener.ease.quadIn
Tweener.ease.quadOut
Tweener.ease.quartInOut
Tweener.ease.quartIn
Tweener.ease.quartOut
Tweener.ease.quintInOut
Tweener.ease.quintIn
Tweener.ease.quintOut
Tweener.ease.sineInOut
Tweener.ease.sineIn
Tweener.ease.sineOut
```
