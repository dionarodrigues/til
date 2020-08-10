# 🐱‍🏍 Drop-shadow CSS function

<div style="text-align:center"><img src="../_images/dropshadow-and-boxshadow-examples.png" width="250" alt="Drop-shadow and Box-shadow examples" /></div>

Check the code in my [Codepen](https://codepen.io/diogorodrigues/pen/PoNqRwY).

---

**Have you ever heard about `drop-shadow()` CSS function? A drop-shadow alternative to work with images that have transparent backgrounds.**

```
<img alt="" class="drop-shadow" src="image-path" />

.drop-shadow {
  filter: drop-shadow(2px 4px 8px rgba(0, 0, 0, 0.5))
}
```

The above example shows the difference between the CSS `box-shadow` property and the `drop-shadow` filter function. Where the `box-shadow` property outlines the html box and the `drop-shadow` outlines the element parts.
