# 😍 Animated Circle Image with SVG and CSS

<div style="text-align:center">![Animated Circle Text](https://raw.githubusercontent.com/diogorodrigues/til/master/_images/circle-text.gif "Animated Circle Text")</div>

Check the code in my [Codepen](https://codepen.io/diogorodrigues/pen/mdJNwLv).

---

**Using SVG and CSS, it is very easy to create animated circular text (or text on a curved path). And below, I'll show you how we can do that.**

```
<div class="animated-circle-text">
     <svg viewBox="0 0 244.1 244.1">
      <path id="circlePath" d="M226.6,122.1c0,57.7-46.8,104.5-104.5,104.5S17.6,179.8,17.6,122.1S64.4,17.6,122.1,17.6
        S226.6,64.4,226.6,122.1z" fill="transparent" />
      <text>
        <textPath  xlink:href="#circlePath">
          I am available for freelance - get in touch -  
        </textPath>
      </text>
    </svg>
  </div>
```

As you can see, we can create the SVG element using `<path>`, `<text>` and `<textPath>` tags.  If you don't know how to create an SVG path, you can use a vector editor, such as Illustrator, and export the document as an SVG..

Then, we can add CSS to style the element and animate it.