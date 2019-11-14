# Techniques and Best Practices

1. [`aria-hidden`](#aria-hidden)
   1. [Basic overview](#basic-overview)
   2. [Hiding SVGs (like avatars) from screen readers](#hiding-svgs-like-avatars-from-screen-readers)
2. [`aria-label` and `aria-labelledby`](#aria-label-and-aria-labelledby)
   1. [Some nuance around `aria-label` and `aria-labelledby`](#some-nuance-around-aria-label-and-aria-labelledby)
3. [`aria-live`](#aria-live)
4. [ARIA/HTML5 Landmarks](#ariahtml5-landmarks)
5. [`<details>` pop-up menus](#details-pop-up-menus)
6. [Indicating focus (& usually never hiding it)](#indicating-focus--usually-never-hiding-it)
7. [Links: Mixed decorated + undecorated links](#links-mixed-decorated--undecorated-links)
8. [Managing focus on navigation/page load](#managing-focus-on-navigationpage-load)

## `aria-hidden`

### Basic overview

>It’s important to understand that ARIA can only affect the *semantics* of an element; it has no effect on the *behavior* of the element. While you can make an element hidden to screen readers with `aria-hidden=”true”`, that does not change the focus behavior for that element. For offscreen interactive content, you will often need to combine `aria-hidden=”true”` and `tabindex=”-1”` to make sure it’s truly removed from the keyboard flow. The proposed [inert attribute](https://github.com/WICG/inert) aims to make this easier by combining the behavior of both attributes. (Via [Google accessibility docs](https://developers.google.com/web/fundamentals/accessibility/how-to-review))


### Hiding SVGs (like avatars) from screen readers

[via Scott O'Hara](https://www.scottohara.me/blog/2019/05/22/contextual-images-svgs-and-a11y.html)
![decorative svgs](../accessibility/images/decorative-svgs.png)

## `aria-label` and `aria-labelledby`

### Some nuance around `aria-label` and `aria-labelledby`

[What happens with aria-labelledby, aria-label and aria-describedby on static HTML elements?](https://www.davidmacd.com/blog/does-aria-label-override-static-text.html)

## `aria-live`

## ARIA/HTML5 Landmarks

https://www.w3.org/TR/wai-aria-practices/examples/landmarks/index.html

## `<details>` pop-up menus

## Indicating focus (& usually never hiding it)

[Indicating focus to improve accessibility](https://hiddedevries.nl/en/blog/2019-06-06-indicating-focus-to-improve-accessibility): An article on why you should **never** use `:focus { outline: none;}`

## Links: Mixed decorated + undecorated links

*Who is this for?* People using a screen reader

When someone using a screen reader lands on a link with a name such as *"click here"*, that's exactly what the screen reader will announce and the context is totally unclear. To improve this, you can wrap the entire line in a link so the full context is conveyed.

This is useful when you want part of the link to be decorated, such as "click here", but the explanatory text before the link is necessary for someone using a screen reader.

*Example:* ["Change this" button isn't self explanatory for people using a screen reader](https://3.basecamp.com/2914079/buckets/11898988/todos/1851452489) via Haystack: Bundles

*Technique:* https://github.com/basecamp/haystack/commit/6e9c6f350d92176cd922c7583edf07ff2db1a00a

![mixed links](../accessibility/images/mixed-link.png)

## Managing focus on navigation/page load

* For single page applications, focus should be set to the first `<h1>` on page load using the Javascript `focus()`, and a `tabindex="-1"` on the element.
* In this **rare** case the focus indicator on the `<h1>` should be overridden with:
```
h1:focus {
  outline: none;
 }
```

Check out Rob Dodson's [video](https://www.youtube.com/watch?time_continue=44&v=srLRSQg6Jgg) and [explanation](https://dev.to/robdodson/managing-focus-64l) for more about this.
