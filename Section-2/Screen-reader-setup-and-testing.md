# Screen reader setup and testing

While the experience of using a screen reader is largely consistent, results vary greatly across platform + browser combinations. When evaluating your feature for screen reader and keyboard accessibility it's recommended to focus on one combination, then perform a run through using a secondary variant once any necessary remediations have been made.

*Note:* Screen reader and keyboard accessibility are distinctly separate, though testing can be combined to identify issues simultaneously.

Screen reader + platform combinations we test against at Basecamp:

- On Mac, VoiceOver + Safari
- On Windows:
  - NVDA + Firefox
  - JAWS + Firefox (secondary)
- On iOS, VoiceOver in mobile Safari & native app
- On Android, Talkback in mobile Chrome & native app

---

1. [VoiceOver on Mac](#voiceover-on-mac)
   1. [Things to be aware of](#things-to-be-aware-of)
2. [NVDA on Windows](#nvda-on-windows)
   1. [Setup](#setup)
3. [JAWS on Windows](#jaws-on-windows)
4. [JAWS Inspect](#jaws-inspect)

## VoiceOver on Mac

[This video walkthrough](https://www.youtube.com/watch?v=5R-6WvAihms&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g&index=6) is a great place to start.

In essence:

1. Run through VoiceOver Training if you haven't used it before *(System Preferences > Accessibility > VoiceOver > Open VoiceOver Training…)*
2. Load up the page you want to test in Safari.
3. Turn on VoiceOver by pressing your TouchID button three times, or using the shortcut defined in *System Preferences > Shortcuts > Accessibility*. I've set mine to `⌥ (option) + `\`. [Here's how to do this in macOS settings](../images/VO-shortcut.png).
4. Begin tabbing through the page, ensuring that each thing that gets announced makes sense, and that every element on the page can be accessed and manipulated.

### Things to be aware of

- When an element receives focus, is it clear what it does?
- If an control has multiple options (like a picker) is this clearly communicated?
- As you interact with an element are changes in state communicated?
- Are all elements on the page focusable?
- Can all elements on the page be manipulated without the use of a mouse?
- Is the result of each action communicated aurally? This includes live updates, such as new content appearing on the page.

## NVDA on Windows

[NVDA](https://www.nvaccess.org), or non-visual access, is a popular screen reader for Windows because it's free. It works much like VoiceOver, though some actions require the use of the `insert` as a special modifier key. Since Mac laptops don't have an insert key you'll want to use [Karabiner](https://pqrs.org/osx/karabiner/index.html) to remap an unused key (like `caps lock`) or a combo to it.

### Setup

1. Install Parallels and Windows.
2. On the Windows VM, install [NVDA](https://www.nvaccess.org).
3. On your Mac, install [Karabiner](https://pqrs.org/osx/karabiner/index.html).
4. In Karabiner under the *Simple Modifications* tab, add a mapping from `caps_lock` to `insert`.
5. In Karabiner under the *Function Keys* tab, check the box at the bottom labeled *Use all F1, F2, etc. keys as standard function keys*.
6. Disable your Mac `caps lock` key. Under *System Preferences > Keyboard > Modifier keys… button*, choose "No Action" for `Caps Lock` on your internal and external keyboards.
7. If you have a TouchBar afflicted MacBook Pro: In *System Preferences > Keyboard > Shortcuts > Function Keys*, add Parallels or VMWare to your list of apps that should show function keys instead of the default.

Resources:
- Similar to the VoiceOver training linked above but for [learning to use NVDA + Firefox](https://www.youtube.com/watch?v=Jao3s_CwdRU&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g&index=4).
- [Deque guide to NVDA shortcuts](https://dequeuniversity.com/screenreaders/nvda-keyboard-shortcuts#nvda-nvda_shortcut_keys)
- [Webaim guide to NVDA shortcuts](https://webaim.org/resources/shortcuts/nvda)

## JAWS on Windows

JAWS is one of the two common screen readers used on Windows. It's rather expensive, but there's a trial that works in a 40 minute "demo" mode, requiring a restart after that time to resume using it. This should be fine for basic testing.

In addition to JAWS, you'll want to install [Karabiner](https://pqrs.org/osx/karabiner/index.html) on your Mac to remap a single key or combination to the windows `insert` key. `Insert` is used as a special shortcut key by both Windows screen readers (JAWS and NVDA). I decided my under-used `caps lock` key would be a good use for `insert`.

1. Install Parallels and Windows.
2. Install [JAWS](https://www.freedomscientific.com/products/software/jaws/).
3. Install [Karabiner](https://pqrs.org/osx/karabiner/index.html).
4. In Karabiner under the *Simple Modifications* tab, add a mapping from `caps_lock` to `insert`.
5. In Karabiner under the *Function Keys* tab, check the box at the bottom labeled *Use all F1, F2, etc. keys as standard function keys*.
6. Disable your Mac `caps lock` key. Under *System Preferences > Keyboard > Modifier keys… button*, choose "No Action" for `Caps Lock` on your internal and external keyboards.
7. If you have a TouchBar afflicted MacBook Pro: In *System Preferences > Keyboard > Shortcuts > Function Keys*, add Parallels or VMWare to your list of apps that should show function keys instead of the default.

Resources:
Using JAWS takes some practice. The [WebAIM guide to keyboard shortcuts for JAWS](https://webaim.org/resources/shortcuts/jaws) is a good place to start.

## JAWS Inspect

JAWS Inspect in like a special non-aural version of JAWS designed for developers. Like the original JAWS it's also quite expensive – $2000/seat/year. I tried it briefly a while back when it was in beta but plan to try using it again soon.
