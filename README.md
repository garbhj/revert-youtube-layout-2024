# Description
A userscript that aims to revert Youtube's recent UI change, with extensive attention to detail. 
I am fairly certain that V4 is the **most accurate** script for reverting back to the pre-2024 layout, at least out of the ones that I could find.

To use it, install Tampermonkey or some other similar userscript extension, click "Create New Script", and copy and paste in the code.

V4 is much more extensive than V3, with detailed adjustments for font size, the clipped off control bar, video window size, and I fixed the rate limiting.
V3 changes fewer things so try switching over to that if you encounter any major bugs with V4. It's also a bit more lightweight, so try it if you encounter any performance issues (though I really don't think that should be an issue). Or, try adjusting the rate limit.

Future version (Possibly): easier customization with instructions and easily settable variables.

If you encounter any problems, feel free to open an issue, and I may or may not ever come around to checking it.

**(I am not be able to continue testing/debugging at the moment, since my layout got changed back to the pre-2024 version)**

# Instructions
To use this, you'll need to:

1. Go to the Chrome Web Store and install the Tampermonkey Chrome extension (or something similar).
2. Once you do that, click "create a new script"
3. Download or copy and paste the code in from here: https://github.com/garbhj/revert-youtube-layout-2024/tree/main
4. Click save, and enable it when you visit Youtube (though it should be enabled by default after saving)

It works by unchecking the experiment flags (taken from some other userscript), and then does a lot of cleanup work restyling everything.

Edit: I also uploaded it to greasyfork for easier installation at https://greasyfork.org/en/scripts/495706-youtube-revert-layout.

Note: Always verify that a userscript is safe before running it. Malicious scripts can be used to steal personal information.

# Other Notes
For an easier (partial) solution, try simply adding the following line to whichever adblocker you already have that allows you to run your own filters (like UBlock Origin):

  youtube.com##+js(set, yt.config_.EXPERIMENT_FLAGS.kevlar_watch_grid, false)
