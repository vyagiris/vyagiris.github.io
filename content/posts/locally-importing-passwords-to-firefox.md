---
title: "locally importing passwords to firefox"
date: 2022-08-30T20:46:29+05:30
draft: false
---

**tl;dr Use chrome instead to import csv files and, then use Firefox's in-built import from other browser**  


I recently had the need to import passwords *to* Firefox locally using a CSV file.  
I had a CSV file containing logins exported from KeepassXC and was looking for a way to add them to Firefox.  
The Mozilla Support [page](https://support.mozilla.org/en-US/kb/import-login-data-file) says the feature is disabled by default and has no instruction on how to enable it.  
I eventually found an **`about:config`** flag **`signon.management.page.fileImport.enabled`** using the first Google search result [hit](https://4sysops.com/archives/export-and-import-passwords-in-firefox/), which I had skipped earlier as it felt very SEO optimized.  
It did seem to add an **`Import from file`** option but, I was let down instantly as I couldn't get it to work.

For testing, I exported an example password and then tried to re-import it and, it failed with below error:

```javascript
Uncaught TypeError: this._errorMessages[errorType] is undefined
    show chrome://browser/content/aboutlogins/components/import-error-dialog.mjs:52
    <anonymous> chrome://browser/content/aboutlogins/aboutLogins.mjs:72
import-error-dialog.mjs:52:36
    show chrome://browser/content/aboutlogins/components/import-error-dialog.mjs:52
    <anonymous> chrome://browser/content/aboutlogins/aboutLogins.mjs:72
    sendToContent resource:///actors/AboutLoginsChild.jsm:320
    #passMessageDataToContent resource:///actors/AboutLoginsChild.jsm:311
    receiveMessage resource:///actors/AboutLoginsChild.jsm:280
```

Younger me would have tried to debug the error, but even with my limited experience I can say this would probably lead me into a rabbit-hole!  
It was kind-of unprecedented but to solve limitations of firefox I used chrome.
Well, I'm reasonably afraid of Google, and hence installed [ungoogled-chromium](https://ungoogled-software.github.io/ungoogled-chromium-binaries/) instead.  
Chrome/Chromium itself also doesn't allow importing by default and, it requires enabling a `chrome:flag` as well: `Password Import` which I learned from another [SEO-y link](https://www.guidingtech.com/import-passwords-csv-google-chrome/)
Chrome was able to import the example logins csv file I had exported off from Firefox.  

Editing the CSV file was pretty straightforward in Microsoft Excel it is alright if many of the fields are blank, Chrome was able to import them without issue.
Then, we can import these to Firefox by selecting the `Import from other browser` option instead.🎉
