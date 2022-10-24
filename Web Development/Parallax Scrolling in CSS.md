---
created: 2022-10-23
tags: 'web-development/css/styling/parallax'
type: 'analysis'
description: 'Analysis on Parallax Scrolling in CSS'
---

### Simple Parallax Design
---
- Requires an element that can wrap around the background image.
- This will be the **scroll container** that will allow the background image to actually scroll up and down.
```html
<div class="wrapper">
	<!-- Background goes in here. -->
</div>
```
- The wrapper will need to encompass the entire page for parallax to work correctly!
- Have to also make sure that we specify a `overflow-y` of `auto`.
- This is what will allow the contents of the wrapper div to scroll.
- Applying the perspective property controls 3D aspect of the parallax. simulating the elements being closer to you/further away from you.
```css
.wrapper {
	height: 100vh;
	overflow-y: auto;
	overflow-x: hidden;
	perspective: 10px;
}
```
- The element that actually contains the background img elements will need the `transform-style: preserve-3d` property.
- In order for the background to display properly and appear behind the rest of the content, set `z-index: -1;`
```html
<div class="wrapper">
	<div class="parallax-container">
		<!-- Background images go here -->
	</div>
</div>
```

```css
.parallax-container {
	position: relative;
	display: flex;
	justify-content: center;
	align-items: center;
	height: 100%;
	transform-style: preserve-3d;
	z-index: -1;
}
```
The img elements need to have:
	- `position: absolute;`,
	- `width: 100%;`
	- `height: 100%;`
	- `object-fit: cover;`
```html
<div class="wrapper">
	<div class="parallax-container">
		<!-- Background images go here -->
		<img class="background" src="" alt="" />
	</div>
</div>
```

```css
.background {
	position: absolute;
	width: 100%;
	height: 100%;
	object-fit: cover;
	z-index: 1;
}
```
- In order to finalize the parallax effect, you need to add a `transform: translateZ()` with a value equalling the `distance` that the element should be at, where n < 0 = further away, and n > 0 = closer to the user.
- You also need to make sure that you set a scale that returns the img back to its original size.
- By having a perspective of 10px and a translation on the z-axis of 10px, the image will appear twice as far away as the rest of the page, so setting the scale to 2 will increase the size of the image back to its original size.
```css
.background {
	transform: translateZ(-10px) scale(2)
}
```
- It would probably make sense to add some variables that allow for easier calculation of the scale relative to both the translateZ and perspective.
- Scale Factor Formula: `1 + ((Z Transform Value * -1) / perspective)`
---
### Advanced, Customizable Parallax Design
---
- Still requires an element that wraps around the entire page.
- Groups the parallax layers together for a more customizable design.
- Number of parallax layers is up to you.
```html
<div class="parallax-wrapper">
  <div class="parallax-group intro-screen" id="intro">
    Parallax Showcase.
  </div>
  
  <div class="parallax-group" id="group-1">
    <div class="parallax-layer base-layer">
      Base Layer
    </div>
    <div class="parallax-layer mid-layer">
      Mid Layer
    </div>
  </div>
  <div class="parallax-group" id="group-2">
    <div class="parallax-layer mid-layer">
      Mid Layer
    </div>
    <div class="parallax-layer top-layer">
      Top Layer
    </div>
  </div>
  
  <div class="parallax-group outro-screen" id="outro">
    The End
  </div>
</div>
```

```scss
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

@mixin align-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

body {

  /* The font styling is for aesthetics */
  font-family: "Raleway", sans-serif;
  font-size: 4em;
  color: #fff;
  
  .parallax-wrapper {
    height: 100vh;
    overflow-x: hidden;
    overflow-y: auto;
    perspective: 300px;
    
    .intro-screen {
      height: 100vh;
      background-color: tomato;
      @include align-center;
    }
    
    .outro-screen {
      height: 100vh;
      background-color: teal;
      @include align-center;
    }
    
    .parallax-group {
      position: relative;
      height: 100vh;
      transform-style: preserve-3d;
      
      .parallax-layer {
        position: absolute;
        inset: 0;
        @include align-center;
      }
      
      .base-layer {
        background-image: url();
          transform: translateZ(-300px) scale(2);
      }
      
      .mid-layer {
        transform: translateZ(0px);
      }
      
      .top-layer {
        transform: translateZ(210px) scale(0.3);
      }
    }
    
    #intro {
      z-index: 0;
    }
    #group-1 {
      z-index: -1;
    }
    #group-1 > .base-layer {
      background-color: crimson;
    }
    
    #group-2 {}
    #group-2 > .mid-layer {
      background-color: yellowgreen;
    }
    
    #outro {}
  }
}

```

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Raleway", sans-serif;
  font-size: 4em;
  color: #fff;
}
body .parallax-wrapper {
  height: 100vh;
  overflow-x: hidden;
  overflow-y: auto;
  perspective: 300px;
}
body .parallax-wrapper .intro-screen {
  height: 100vh;
  background-color: tomato;
  display: flex;
  justify-content: center;
  align-items: center;
}
body .parallax-wrapper .outro-screen {
  height: 100vh;
  background-color: teal;
  display: flex;
  justify-content: center;
  align-items: center;
}
body .parallax-wrapper .parallax-group {
  position: relative;
  height: 100vh;
  transform-style: preserve-3d;
}
body .parallax-wrapper .parallax-group .parallax-layer {
  position: absolute;
  inset: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
body .parallax-wrapper .parallax-group .base-layer {
  background-image: url();
  transform: translateZ(-300px) scale(2);
}
body .parallax-wrapper .parallax-group .mid-layer {
  transform: translateZ(0px);
}
body .parallax-wrapper .parallax-group .top-layer {
  transform: translateZ(210px) scale(0.3);
}
body .parallax-wrapper #intro {
  z-index: 0;
}
body .parallax-wrapper #group-1 {
  z-index: -1;
}
body .parallax-wrapper #group-1 > .base-layer {
  background-color: crimson;
}
body .parallax-wrapper #group-2 > .mid-layer {
  background-color: yellowgreen;
}
```

---
### Additional Notes:
- When adjusting the size of a parallax group, the height of the layers inside of the group will also have to be adjusted to account for that, otherwise, you'll get issues like this:
![[Pasted image 20221020074654.png]]
- The entire layer will just be hidden behind everything else scrolling too far.

### Resources:
[This Simple Trick Makes Your Website 83% Better Looking](https://www.youtube.com/watch?v=mxHoPYFsTuk)
[Simple Pure CSS Parallax Scroll Tutorial](https://www.youtube.com/watch?v=rLrLJQBG_qo)