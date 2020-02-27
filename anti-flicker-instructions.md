# surefoot - Page Conceal Anti-Flicker Liquid Snippet - Implementation Instructions

### Summary
This snippet will be used to temporarily conceal the page on pageload, so that the user does not percieve any FOUC when our test replaces elements on the original page. This snippet is in three parts: the anti-flicker/page concealing snippet (`anti-flicker-page.snippet.liquid`), a small code block to insert into the themes's main `theme.liquid` file (`anti-flicker-page_theme.liquid`), and a Shopify Theme Settings config snippet that provides an easily toggable checkbox to turn the Page Conceal Anti-Flicker snippet on or off. Complete installation should only take a few minutes of copy/pasting.


### 1. Page Conceal Snippet
Simply copy/paste the contents of `anti-flicker-page.snippet.liquid` into a new file `/snippets/anti-flicker-page.snippet.liquid`. 

This code sets `visibility: hidden` on the homepage's `<body>` element. After 2 seconds (or whatever is set in Settings), this CSS is removed. If our test code is active (either on the original homepage, or in one of the two new redesign variations), the homepage will be revealed sooner - as soon as the code has loaded from Google Optimize.

### 2. Theme Snippet
Copy the contents of `anti-flicker-page_theme.liquid` anywhere as high possible in the homepage's `theme.liquid` template's `<body>` section. This section will inject the snippet in step 1, but only if the Theme Settings checkbox is enabled.

### 3. Theme Settings Checkbox
Add the contents of `settings_schema-partial.liquid` to the array in the existing `settings_schema.json` file for your template. It doesn't matter if it goes at the beginning or at the end of the existing settings, as long as the existing settings are not overwritten or deleted.

This will create a new Theme Settings category called 'surefoot a/b test settings'. Inside this category there will be a checkbox labeled "Enable Page Conceal Anti-Flicker snippet". Simply check this box to enable the snippet. There is also a setting that allows you to set the delay timeout that controls when the anti-flicker snippet is removed. 
