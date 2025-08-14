---
title: Custom Browser Settings
layout: default
excerpt: Set up incognito mode, use a custom browser, etc.
---
# Custom Browser Settings
In 0.7.8 the "Default browser" settings were renamed into "Custom browser" settings. Some bugs were fixed, and the available features were expanded upon. Here's an overview of those features and how to use them:

## Browser executable
You can select the path to your browser of choice using a normal file selection dialog. Explicitly selecting the executable file is the best way to ensure it's correct. However, if you manually type in the name of a browser, such as "firefox" or "librewolf" then Frolic will try to guess what you mean.

Frolic will take the following action to try to find your browser of choice:
On Windows:
* Add `.exe` to the end if you didn't provide it.
* Search in your `Program Files` directoy for that file name using this command:
```bash
where /r "c:\Program Files" "filename"
```

On Linux
* Search for your provided filename using this command:
```bash
which filename
```

If the browser can't be found, Frolic will try to use your system's default browser. If you right-clicked and selected "Open in Incognito Mode", then in order to respect your privacy, an error message will be displayed and the link won't be opened.

## Browser Arguments
You can configure custom command-line parameters for opening your browser.

For example, you can choose to open links in a specific user profile in chromium-based browsers:
* In your browser, navigate to `chrome://version` and notice the "Profile Path" name. Typically this is "Default" or "Profile 1", "Profile 2", and so on.
* In Frolic, under the "Arguments to pass to executable" you enter:
```
--user-profile="Profile 3"
```
...or whatever the profile is that appeared in your version page. Then, all links opened from Frolic will open with that profile.

There are additional options you can find across the internet for your browser of choice. You may also leave the arguments blank to use all the default settings. If left blank, a mandatory `%s` will be added.

Beneath the arguments is an example of how your browser will be invoked so you can double-check that you've entered everything correctly.

## Incognito mode arguments
This entry is new in Frolic 0.7.8 and allows you to specify any arguments specific to opening a browser in private browsing mode. If you selected a browser, you can hit the "Detect" button to automatically detect your browser and fill in the incognito argument.

You may want to fill in additional arguments to customize how your browser opens; if you do not put your browser's necessary argument, your browser will open normally.

If you delete all the text in the box, Frolic will try to detect the correct argument to enable private browsing mode and fill it in.

Beneath the incognito arguments box is an example of how your browser will open links when you right-click -> Open in Incognito Mode, so you can verify that everything looks correct.

---

Please keep in mind all the normal caveats about private browsing modes - they do not provide you more security against online threats - they are only intended to prevent your browsing history from being discovered by other people with access to your PC.


## Custom Browser Profiles
If you are using incognito mode to keep your f-chat browsing history distinct from your normal browsing history but aren't concerned about having it deleted regularly, considering setting your browsing arguments to open a specific profile. Something like this:

##### Firefox & Derivatives
Open `about:profiles` and look for the "Profile" entry. (You can also create a new profile from this page.) Use the profile name here:
```bash
-profile "profile_name"
```

##### Edge
Open `edge://version` in your browser and look at the "Profile path" entry. Add the last folder into the entry below.
```bash
--profile-directory="profile_directory"
```

##### Chromium & Derivatives
Open `chrome://version` in your browser and look at the "Profile path" entry. Add the last folder into the entry below.
```bash
--user-profile="profile_directory"
```

In all cases, you will have an example that looks like this:
```bash
"edge.exe" --profile-directory="Profile 2" "https://example.com/page"
"firefox.exe" -profile "default-release" "https://example.com/page"
"chromium.exe" --user-profile="Profile 11" "https://example.com/page"
```

This will let you open all links in that specific browser profile and the history will be kept separate from your primary browsing history.
