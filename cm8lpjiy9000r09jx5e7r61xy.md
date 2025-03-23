---
title: "Understanding Cascading in CSS"
seoTitle: "Understanding CSS Specificity: A Comprehensive Guide with Examples"
seoDescription: "Learn the basics of CSS specificity and how it affects your stylesheets. Explore examples and best practices for understanding selector priority, specificit"
datePublished: Sun Mar 23 2025 14:02:39 GMT+0000 (Coordinated Universal Time)
cuid: cm8lpjiy9000r09jx5e7r61xy
slug: understanding-cascading-in-css
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/dVBs3hKQrNo/upload/bd12fb72015f401225627e0b2e10ecb2.jpeg
tags: css3, css, web-development, webdev, cascading-style-sheets, understanding-how-cascading-works-in-css

---

In web development, CSS (Cascading Style Sheets) controls the presentation of HTML elements. One key concept in CSS is the *cascading* feature, which determines how styles are applied when multiple CSS rules could affect an element.

*Cascading* refers to the process of determining which CSS rule to apply when multiple conflicting rules for the same element exist. Understanding this concept is crucial for writing efficient and maintainable stylesheets.

## What is Cascading?

The CSS Cascade is a set of rules that dictate which styles are applied to elements when there are conflicts. This cascade is determined by three main factors:

1. **Specificity**: The more specific a CSS rule is, the higher its priority.
    
2. **Source Order**: If two rules have the same specificity, the one that appears later in the stylesheet takes precedence.
    
3. **Importance**: The `!important` declaration can be used to give a style rule higher priority, even over other specific selectors.
    

### Specificity

Specificity is the weight assigned to a CSS selector. A selector’s specificity is calculated based on how specific it is in targeting HTML elements. More specific selectors take precedence over more general ones.

For example:

* `div` is less specific than `.class`, which is less specific than `#id`.
    
* Inline styles (styles defined directly in HTML elements using the `style` attribute) have the highest specificity.
    

### CSS Specificity Table

| Selector Type | Example | Specificity Points | Explanation |
| --- | --- | --- | --- |
| **Inline styles** | `<div style="color: red;">` | `1000` | Inline styles have the highest specificity. |
| **IDs** | `#id` | `100` | IDs have high specificity. |
| **Classes, attributes, pseudo-classes** | `.class`, `[type="text"]`, `:hover` | `10` | Classes, attributes, and pseudo-classes have medium specificity. |
| **Elements, pseudo-elements** | `div`, `h1`, `p`, `::before` | `1` | Element selectors and pseudo-elements have the lowest specificity. |
| **Universal selector** | `*` | `0` | The universal selector has no specificity. |

### How Specificity is Calculated:

For example, consider the following CSS selectors:

1. `#header` → Specificity: `100` (1 ID)
    
2. `.button` → Specificity: `10` (1 class)
    
3. `p` → Specificity: `1` (1 element)
    
4. `div p:hover` → Specificity: `11` (1 element + 1 pseudo-class)
    

### Combining Specificity:

When multiple selectors apply to an element, you add the specificity of each selector. For example:

```css
/* Example 1 */
#container .header p {
  color: blue;
}
```

Specificity for `#container .header p`:

* `#container`: `100` (1 ID)
    
* `.header`: `10` (1 class)
    
* `p`: `1` (1 element)
    

Total specificity = `100 + 10 + 1 = 111`.

### Source Order

If two rules are equally specific, the one that comes later in the CSS file will be applied.

### Importance

The `!important` rule can be added to a CSS rule to ensure that it takes precedence over other conflicting rules, even those with higher specificity.

```css
p {
  color: blue;
}

p {
  color: red !important;
}
```

In the example above, even though both rules are equally specific, the paragraph text will be **red** because of the `!important` declaration.

## Example of Cascading in Action

Let’s create a simple example to see how cascading works in CSS. Below is a basic HTML structure with some inline, internal, and external styles.

### HTML + CSS Code Example

```xml
<!DOCTYPE html>
<html lang="en">
<head>
  <style>
    /* General paragraph styling */
    p {
      color: blue;
      font-size: 14px;
    }

    /* More specific class styling */
    .highlight {
      color: red;
      font-size: 16px;
    }

    /* Specific styling for an ID */
    #unique {
      color: green;
      font-size: 18px;
    }

    /* Overriding with !important */
    p {
      color: orange !important;
    }
  </style>
</head>
<body>
  <p>This is a paragraph with the general style (blue).</p>
  <p class="highlight">This is a highlighted paragraph (red).</p>
  <p id="unique">This is a unique paragraph (green).</p>
</body>
</html>
```

### Explanation of the Example:

* **First Paragraph**: The first paragraph will be **blue**, because it applies the general `p` style.
    
* **Second Paragraph**: The second paragraph has the `.highlight` class, which overrides the general `p` style, making the text **red**.
    
* **Third Paragraph**: The third paragraph has the `#unique` ID, which is more specific than both the `p` tag and the `.highlight` class. It applies the **green** color.
    
* **Cascading Order**: The last `p { color: orange !important; }` rule overrides all previous ones due to the `!important` flag. Hence, all paragraphs will turn **orange** despite the other rules.
    

## Wrapping it up

Here’s a quick recap of how CSS decides which styles to apply:

* **Specificity**: More specific selectors (e.g., IDs over classes, classes over elements) take precedence.
    
* **Source Order**: When two rules have the same specificity, the one that appears last wins.
    
* **Importance**: The `!important` flag can override other styles, but it should be used sparingly as it breaks the normal cascading flow.
    

Happy Styling! ✨