# How to audit for accessibility on the web

- [1. Scan for violations using a browser extension](#1-Scan-for-violations-using-a-browser-extension)
- [2. Every focusable element on the page should have an outline or other visible indicator of focus.](#2-Every-focusable-element-on-the-page-should-have-an-outline-or-other-visible-indicator-of-focus)
- [3. Make sure heading levels are semantic](#3-Make-sure-heading-levels-are-semantic)
- [4. Color contast](#4-Color-contast)
  - [Tools for checking contrast levels](#Tools-for-checking-contrast-levels)
  - [More resources](#More-resources)
- [5. Hide decorative elements from assistive technology](#5-Hide-decorative-elements-from-assistive-technology)

---

## 1. Scan for violations using a browser extension

*Who is this for?* General accessibility/usability

There are a few browser extensions designed to detect accessibility issues, and explain how to fix them. Keep in mind these won't catch all accessibility issues, only a subset of them. These checks should be run *both* against the normal desktop sized viewport, and again for mobile views.

- My current favorite for Chrome and Firefox is [axe](https://www.deque.com/axe/)
- [Chrome's built-in accessibility audit](https://developers.google.com/web/tools/chrome-devtools/accessibility/reference)
- [tota11y](https://khan.github.io/tota11y/), an accessibility (a11y) visualization toolkit from Khan Academy.
- [Lighthouse](https://developers.google.com/web/tools/lighthouse/) auditing tool, built directly into Google Chrome!
- And [Firefox's integrated accessibility checker](https://developer.mozilla.org/en-US/docs/Tools/Accessibility_inspector)

Here's what a example report from axe looks like:
![axe sample report](images/axe-report-1.png)

The column on the right lists all of the accessibility violations. When you select a violation and click the "Highlight" control, the respective element will be called out:
![axe violations](images/axe-report-violations.png)

---

## 2. Every focusable element on the page should have an outline or other visible indicator of focus.

*Who is this for?* Users with low vision

This is pretty simple to check. Just tab through each screen and make sure every element you land on has an outline or other visual indicator of focus.

---

## 3. Make sure heading levels are semantic

*Who is this for?* People using a screen reader, those with cognitive disabilities.

For someone using a screen reader, heading levels are important for getting an overview of the structure of a page. Therefore, heading levels should first and foremost be used for semantics, and only secondarily for styling.

> Making texts larger helps guide the eye around the page. Using headings and making them visually apparent is especially helpful for users with cognitive disabilities.

> If the underlying code for a pages headings is correct, screen reader users can also benefit from headings. Screen reader users can navigate a page according to its headings, listen to a list of all headings, and skip to a desired heading to begin reading at that point. Screen reader users can use headings to skip the repeated blocks of content like headers, menus, and sidebars, for example.

> In 2017, WebAIM asked [how screen reader users preferred to find information on lengthy web pages](https://webaim.org/projects/screenreadersurvey7/#finding). Almost 70% of respondents said they preferred to use headings on a page. Clearly, organizing pages using headings is one of the best accessibility strategies available.

While the extensions in [Section 1](https://github.com/basecamp/accessibility/blob/master/how-to-perform-an-accessibility-audit-web.md#1-scan-for-violations-using-a-browser-extension) will include heading level violations, the [headingsMap](https://chrome.google.com/webstore/detail/headingsmap/flbjommegcjonpdmenkdiocclhjacmbi?hl=en) Chrome extension is an easy way to review heading levels in one spot. Here's what a sample report looks like:
![sample headingsmap report](images/headingsmap-report.png)

Further reading about the importance of headings for people using assistive technology:
- [Heading levels should only increase by one](https://dequeuniversity.com/rules/axe/3.2/heading-order)
- [Page must contain a level-one heading](https://dequeuniversity.com/rules/axe/3.2/page-has-heading-one)

---

## 4. Color contast

*Who is this for?* People with low vision and color blindness

When the contrast of an element is too similar to that of another its background or label it can be difficult to see. These failures will get raised by the browser extensions. There are two dimensions to consider when thinking about contast: <span style="color:cyan">color</span> and <span style="font-size:24px">size</span>.

- WCAG 2 level AA requires a contrast ratio of at least `4.5:1` for normal text and `3:1` for large text. Large text is defined as 14 point (typically 18.66px) **and bold** or larger, or 18 point (typically 24px) or larger

- For graphics and user interface components (such as form input borders), a contrast ratio of at least `3:1` is required.

- Level AAA requires a contrast ratio of at least `7:1` for normal text and `4.5:1` for large text.

### Tools for checking contrast levels

- [In Chrome dev tools, viewing the contrast ratio of a text element in the Color Picker](https://developers.google.com/web/tools/chrome-devtools/accessibility/reference#contrast): Provides a handy curve for colors above and below the recommendation.
- [ColorZilla for Firefox & Chrome](https://www.colorzilla.com)
- [Contrast Mac app](https://usecontrast.com): Handy app that lives in your menu bar. (**Important note:** Does not consider text size in contrast calculation.)

### More resources

- [Webaim article on Contrast and Color Accessibility](https://webaim.org/articles/contrast/)

---

## 5. Hide decorative elements from assistive technology

*Who is this for?* People using a screen reader

Elements that serve only a purpose visually or repeat information that's conveyed via alternate means, such as by a nearby text label, should be hidden from screen readers to prevent annoying redudancy. Some common examples include horizontal rule `<hr>` elements, or avatars when the name of the person they refer to are repeated nearby.

It's easiest to test this out by [navigating through the page using a screen reader](https://github.com/basecamp/accessibility/blob/master/how-to-use-a-screen-reader.md). When you determine that an element should be omitted, add the attribute `aria-hidden="true"` to hide it from the accessibility tree. Then re-test using a screen reader to make sure this changes what you were intending.
