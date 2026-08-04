---
name: anime-js
description: Use when implementing Disney's 12 animation principles with Anime.js v4 library
---

# Anime.js v4 Animation Principles

Implement all 12 Disney animation principles using Anime.js v4's flexible animation engine.

**IMPORTANT**: This skill uses the **v4 API** with named imports. Do NOT use the legacy v3 `anime({...})` default export.

```javascript
import { animate, stagger, createTimeline, onScroll, createDrawable, splitText } from 'animejs'
```

## 1. Squash and Stretch

```javascript
animate('.ball', {
  scaleX: [1, 1.2, 1],
  scaleY: [1, 0.8, 1],
  duration: 300,
  ease: 'inOutQuad'
});
```

## 2. Anticipation

```javascript
const tl = createTimeline();
tl.add('.character', {
  translateY: 10,
  scaleY: 0.9,
  duration: 200
})
.add('.character', {
  translateY: -200,
  duration: 400,
  ease: 'outQuad'
});
```

## 3. Staging

```javascript
animate('.background', {
  filter: 'blur(3px)',
  opacity: 0.6,
  duration: 500
});
animate('.hero', {
  scale: 1.1,
  duration: 500
});
```

## 4. Straight Ahead / Pose to Pose

```javascript
animate('.element', {
  keyframes: [
    { translateX: 0, translateY: 0 },
    { translateX: 100, translateY: -50 },
    { translateX: 200, translateY: 0 },
    { translateX: 300, translateY: -30 }
  ],
  duration: 1000
});
```

## 5. Follow Through and Overlapping Action

```javascript
const tl = createTimeline();
tl.add('.body', { translateX: 200, duration: 500 })
  .add('.hair', { translateX: 200, duration: 500 }, '-=450')
  .add('.cape', { translateX: 200, duration: 600 }, '-=500');
```

## 6. Slow In and Slow Out

```javascript
animate('.element', {
  translateX: 300,
  duration: 600,
  ease: 'inOutCubic'
});
// Options: inQuad, outQuad, inOutQuad
// inCubic, outCubic, inOutCubic
// spring(mass, stiffness, damping, velocity)
```

## 7. Arc

```javascript
animate('.ball', {
  translateX: 200,
  translateY: [
    { to: -100, duration: 500 },
    { to: 0, duration: 500 }
  ],
  ease: 'outQuad',
  duration: 1000
});
```

## 8. Secondary Action

```javascript
const tl = createTimeline();
tl.add('.button', {
  scale: 1.1,
  duration: 200
})
.add('.icon', {
  rotate: 15,
  duration: 150
}, '-=150')
.add('.particles', {
  opacity: [0, 1],
  delay: stagger(50)
}, '-=100');
```

## 9. Timing

```javascript
// Fast - snappy
animate('.fast', { translateX: 100, duration: 150 });

// Normal
animate('.normal', { translateX: 100, duration: 300 });

// Slow - dramatic
animate('.slow', { translateX: 100, duration: 600 });

// Spring physics
animate('.spring', { translateX: 100, ease: 'spring(1, 80, 10, 0)' });
```

## 10. Exaggeration

```javascript
animate('.element', {
  scale: 1.5,
  rotate: '2turn',
  duration: 800,
  ease: 'outElastic(1, 0.5)' // overshoot
});
```

## 11. Solid Drawing

```javascript
animate('.box', {
  rotateX: 45,
  rotateY: 30,
  perspective: 1000,
  duration: 500
});
```

## 12. Appeal

```javascript
animate('.card', {
  scale: 1.02,
  boxShadow: '0 20px 40px rgba(0,0,0,0.2)',
  duration: 300,
  ease: 'outQuad'
});
```

## Stagger Animation

```javascript
animate('.item', {
  translateY: [20, 0],
  opacity: [0, 1],
  delay: stagger(100), // 100ms between each
  ease: 'outQuad'
});
```

## Text Split Animation

```javascript
const targets = splitText('.headline');
animate(targets.words, {
  opacity: [0, 1],
  translateY: [20, 0],
  delay: stagger(80),
  ease: 'outQuad',
  duration: 600
});
```

## Scroll-Triggered Animation

```javascript
animate('.section', {
  opacity: [0, 1],
  translateY: [40, 0],
  duration: 800,
  ease: 'outQuad',
  autoplay: onScroll({
    target: '.section',
    enter: 'bottom-=100 top'
  })
});
```

## SVG Path Drawing

```javascript
const drawable = createDrawable('.svg-path');
animate(drawable, {
  draw: ['0 0', '0 1'],
  duration: 1200,
  ease: 'inOutQuad'
});
```

## Key Anime.js v4 Features

- `animate(targets, props)` - Animate elements
- `createTimeline()` - Sequence animations
- `stagger(value)` - Offset delays between elements
- `onScroll({ target })` - Scroll-triggered playback
- `splitText(target)` - Split text into words/chars for animation
- `createDrawable(svg)` - SVG stroke drawing animation
- `keyframes` - Multiple animation poses
- Built-in easings: `inQuad`, `outElastic`, `spring()`, etc.
- `'-=200'` - Relative offset timing in timelines
