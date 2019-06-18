# Techniques & Best Practices

- [`aria-hidden`](#aria-hidden)
  - [Hiding SVGs (like avatars) from screen readers](#Hiding-SVGs-like-avatars-from-screen-readers)
- [`aria-label` and `aria-labelledby`](#aria-label-and-aria-labelledby)
  - [Some nuance around `aria-label` and `aria-labelledby`](#Some-nuance-around-aria-label-and-aria-labelledby)
- [`aria-live`](#aria-live)
- [`<details>` pop-up menus](#details-pop-up-menus)
- [Indicating focus (& usually never hiding it)](#Indicating-focus--usually-never-hiding-it)
- [Links: Mixed decorated + undecorated links](#Links-Mixed-decorated--undecorated-links)
- [ARIA/HTML5 Landmarks](#ARIAHTML5-Landmarks)

## `aria-hidden`

### Hiding SVGs (like avatars) from screen readers

[via Scott O'Hara](https://www.scottohara.me/blog/2019/05/22/contextual-images-svgs-and-a11y.html)
![decorative svgs](images/decorative-svgs.png)

## `aria-label` and `aria-labelledby`

### Some nuance around `aria-label` and `aria-labelledby`

[What happens with aria-labelledby, aria-label and aria-describedby on static HTML elements?](https://www.davidmacd.com/blog/does-aria-label-override-static-text.html)

## `aria-live`

## `<details>` pop-up menus

## Indicating focus (& usually never hiding it)

[Indicating focus to improve accessibility](https://hiddedevries.nl/en/blog/2019-06-06-indicating-focus-to-improve-accessibility): An article on why you should **never** use `:focus { outline: none;}`

## Links: Mixed decorated + undecorated links

This is useful when you want part of the link to be decorated, such as "click here", but the explanatory text before the link is necessary for someone using a screen reader.

*Example:* ["Change this" button isn't self explanatory for people using a screen reader](https://3.basecamp.com/2914079/buckets/11898988/todos/1851452489) via Haystack: Bundles

*Technique:* https://github.com/basecamp/haystack/commit/6e9c6f350d92176cd922c7583edf07ff2db1a00a

![mixed links](images/mixed-link.png)

## ARIA/HTML5 Landmarks

https://www.w3.org/TR/wai-aria-practices/examples/landmarks/index.html
