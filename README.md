# Picket Line Notifier

An open-source browser extension that alerts you when you navigate to a website belonging to an organization whose employees are on strike. You can then click on the notification to learn more about the strike. You can also click on the extension's icon in your browser's toolbar to show a popup with a list of active strikes and links to more information.

<img src="https://github.com/jamespizzurro/picket-line-notifier/raw/main/screenshots/chrome-notification.png" width="800" alt="A screenshot of wirecutter.com with a notification from this browser extension rendered over it indicating that Wirecutter's employees are on strike and that one can click the notification for more information.">
<img src="https://github.com/jamespizzurro/picket-line-notifier/raw/main/screenshots/firefox-strike-list.png" height="325" alt="A screenshot of a list of active strikes, each with a link to more information, that can be accessed by clicking the extension's icon in your browser's toolbar.">

## Installing

If available for your browser, we recommend installing this browser extension [automatically](#automatically) to ensure you receive any updates to the extension itself. Regardless of what browser or installation method you choose though, after installing the browser extension for the first time, you'll get [the latest strike data](https://github.com/jamespizzurro/picket-line-notifier/blob/main/data/strikes.json) automatically thereafter.

### Automatically

#### Google Chrome

Install from [our page on the Chrome Web Store](https://chrome.google.com/webstore/detail/picket-line-notifier/mbehfdoomcmpbejngdojlocpkgjacppl).

#### Microsoft Edge

Install from [our page on Microsoft Edge Addons](https://microsoftedge.microsoft.com/addons/detail/picket-line-notifier/apeihmeekhpcdaoedhbcidhllognbibl).

#### Mozilla Firefox

Install from [our page on Mozilla's list of Firefox add-ons](https://addons.mozilla.org/en-US/firefox/addon/picket-line-notifier/).

#### Opera

This browser extension is not yet available from [Opera's Extensions page](hhttps://addons.opera.com/en/extensions/); official approval for it to be listed there is still pending. In the meantime, please use [the manual installation instructions for Opera](#google-chrome--microsoft-edge--opera) below.

### Manually

#### Google Chrome / Microsoft Edge / Opera

1. Download this repository as a [ZIP file from GitHub](https://github.com/jamespizzurro/picket-line-notifier/archive/refs/heads/main.zip).
2. Unzip the ZIP file and you should have a directory named `picket-line-notifier-main`. Move this directory to a permanent location, as deleting it will uninstall the extension.
3. Launch your web browser and go to its Extensions page (<a href="chrome://extensions">chrome://extensions</a> in Chrome; <a href="edge://extensions">edge://extensions</a> in Edge; <a href="opera://extensions">opera://extensions</a> in Opera). Enable 'Developer Mode' from there.
4. Drag the `picket-line-notifier-main` directory anywhere on the Extensions page to install it. Remember: don't delete the `picket-line-notifier-main` directory unless you want to uninstall the extension.

#### Mozilla Firefox

1. Download [the latest XPI file from GitHub](https://github.com/jamespizzurro/picket-line-notifier/raw/main/web-ext-artifacts/picket_line_notifier-1.1.1-an+fx.xpi) in the `web-ext-artifacts` directory of this repository.
2. Launch Firefox, go to Settings > Extensions & Themes > Extensions (<a href="about:addons">about:addons</a>), click the button with a gear icon, and choose 'Install Add-on From File...' from the menu that appears. Find the XPI file you just downloaded from the file chooser dialog that appears, select it and continue.
3. Optional: delete the XPI file you downloaded; it's no longer necessary.

## FAQ

### I'm not seeing any browser notifications on Windows. What gives?

You may have Focus Assist enabled, which can block browser notifications. [Click here](https://support.microsoft.com/en-us/windows/make-it-easier-to-focus-on-tasks-0d259fd9-e9d0-702c-c027-007f0e78eaf2) (and scroll down to the 'Quiet down those notifications' section) for some general instructions on how to configure it.

## Contributing

Check out the `data/strikes.json` file. If you notice a strike is missing from that file, or the data for a given strike listed there isn't as good as it could be, or a strike that's no longer active is still listed, [create a new issue](https://github.com/jamespizzurro/picket-line-notifier/issues) or [submit a pull request](https://github.com/jamespizzurro/picket-line-notifier/pulls) to this repository on GitHub.

For reference, here's an example of what an entry in `data/strikes.json` should look like:

```json
"Wirecutter": {
    "moreInfoUrl": "https://twitter.com/wirecutterunion/status/1463734222812856321",
    "matchingUrlRegexes": [
        "wirecutter.com",
        "nytimes.com/wirecutter",
        "facebook.com/thewirecutter",
        "instagram.com/wirecutter",
        "twitter.com/wirecutter",
        "tiktok.com/@wirecutter"
    ]
}
```

In the example above, "Wirecutter" is the organization name, `matchingUrlRegexes` is the list of case-insensitive regular expressions that match on Wirecutter's websites which will create a browser notification alerting the user to the strike, and `moreInfoUrl` is the URL that the user will be navigated to when the user clicks on that browser notification to learn more about the strike.

For the organization name, make sure the organization isn't already listed, e.g. from another strike. This can happen with larger, international companies. If you run into this, simply edit the organization name for _both_ strikes, i.e. for the strike you're adding as well as for the one that was already there, to be more specific by including the location of the strike. This will help users know which strikes are more relevant to them at a glance.

For `moreInfoUrl`, URLs to primary sources are preferred, as are those to landing pages or social media profiles that are actively being kept up to date about the strike as new events unfold, e.g. the union's landing page for the strike or a post on the union's Facebook or Twitter profile that includes a link to a strike donation page. If nothing like this is readily available though, links to secondary sources are okay, e.g. a news story that includes interviews with striking workers or union representatives that details why they're striking.

For `matchingUrlRegexes`, we've found one of the easiest ways to generate this list is to go to the company's website and look for links to their social media pages. These are usually shown as icons at the top or bottom of most pages on their website and/or on 'About' or 'Contact Us' pages. You can then add these links to the list along with a link to the company's website, just be sure to remove boilerplate like `http://www.` from the beginning of all those links along with everything after the "?" or "#" character at the end of them. This will help ensure more people see the strike notification more often if they find themselves visiting these pages belonging to the company. For example, `https://www.tiktok.com/@wirecutter/video/7111430975724195118?is_copy_url=1&is_from_webapp=v1` should be added to the list as `tiktok.com/@wirecutter` to ensure users are notified whenever they view any video on Wirecutter's TikTok page in their web browser, not just the one particular video you viewed. A good way to check to see if you've removed too much from the URL is to visit your edited one (e.g. `tiktok.com/@wirecutter`) in your web browser; if it still takes you to the page you were expecting, e.g. Wirecutter's TikTok page, you're good, but if you are taken to a 404 page or something, you need to revisit your edits.

## Project Roadmap

* Add support for Apple's Safari web browser and publish it in Apple's App Store.

## Credits

### Frequently Used Data Sources

* [AFL-CIO's Strike Map](https://aflcio.org/strike-map)
* [The Cornell-ILR Labor Action Tracker](https://striketracker.ilr.cornell.edu/)

### Graphics

* <a href="https://www.flaticon.com/premium-icon/protest_756961">'Protest' icon</a> made by <a href="https://www.flaticon.com/authors/chanut-is-industries" title="Chanut-is-Industries">Chanut-is-Industries</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a>
