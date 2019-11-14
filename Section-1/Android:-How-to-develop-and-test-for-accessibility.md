# Android: How to develop and test for accessibility

While the core principles around developing and testing for accessibility apply across all platforms there are some specific tools and practices for Android.

1. [Run an accessibility validation tool on each screen of the app](#run-an-accessibility-validation-tool-on-each-screen-of-the-app)
2. [Run through the app using TalkBack screen reader](#run-through-the-app-using-talkback-screen-reader)
3. [Additional Resources](#additional-resources)


## Run an accessibility validation tool on each screen of the app

There are two great tools you can run against each screen of the app to check for accessibility issues. Failures from these tests usually cover touch point sizes that are under-spec, missing or duplicate element names or descriptions, and low color contrast.

- Accessibility Scanner from Google ([download](https://play.google.com/store/apps/details?id=com.google.android.apps.accessibility.auditor), [docs](https://support.google.com/accessibility/android/answer/6376570))
- Axe Android app from Deque ([download](https://play.google.com/store/apps/details?id=com.deque.axe.android), [overview](https://www.deque.com/axe/axe-for-android/))

I've noticed Google's Accessibility Scanner returns less violations than Axe's tool, so I'd suggest running the Google scanner first, and Axe as a secondary check for less significant failures once all issues reported by the first check have been fixed.

## Run through the app using TalkBack screen reader

Android ships with a built-in screen reader called TalkBack. Using it is similar to VoiceOver and other screen readers. Once turned on (from Settings > Accessibility > TalkBack) you simply swipe left or right to move through items on the screen, and double tap to activate them. The first time it's enabled you'll be taken to a tutorial I'd highly suggest going through. There's [a tutorial on the web](https://support.google.com/accessibility/android/answer/6283677?hl=en) and [Android Accessibility documentation](https://support.google.com/accessibility/android/?hl=en#topic=6007234) you can reference as well.

Things to pay attention to when using TalkBack:

- Does the navigation order make sense?
- Do skip links work correctly? (These hidden elements, presented only to those using screen readers, provide a quick way to skip over the nav and get directly into the page content.)
- Does the spoken feedback for each element convey its content or purpose appropriately? (Learn how to [write meaningful labels](https://material.io/guidelines/usability/accessibility.html#accessibility-writing).)
- Are announcements succinct, or are they needlessly verbose?
- Are you able to complete the main workflows easily?
- Are you able to reach every element by swiping?
- If alerts or other temporary messages appear, are they read aloud?

## Additional Resources

- Google's [Material Design Accessibility docs](https://material.io/design/usability/accessibility.html)
- [TalkBack gesture reference](https://support.google.com/accessibility/android/answer/6151827?hl=en&ref_topic=3529932)
