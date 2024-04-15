// ==UserScript==
// @name         YouTube Revert Layout
// @version      3.0
// @author       Garbhj
// @description  This script aims to revert some of Youtube's UI changes, unddoing the position change and formatting the video cards back into their original dimensions. It should be more accurate than most (at least it's better than all the other ones I've tried).
// @match        *://*.youtube.com/*
// @run-at       document-end
// @icon         https://www.google.com/s2/favicons?sz=64&domain=youtube.com
// ==/UserScript==

(function () {
    'use strict';

    // Modify experiment flags to revert UI changes ***
    ytcfg.set('EXPERIMENT_FLAGS', {
        ...ytcfg.get('EXPERIMENT_FLAGS'),
        "kevlar_watch_comments_panel_button": false,
        "kevlar_watch_comments_ep_disable_theater": true,
        "kevlar_watch_grid": false,
        "kevlar_watch_grid_hide_chips": false,
        "kevlar_watch_grid_reduced_top_margin_rich_grid": false,
        "optimal_reading_width_comments_ep": false,
        "small_avatars_for_comments": false,
        "small_avatars_for_comments_ep": false,
        "swatcheroo_direct_use_rich_grid": false,
        "web_watch_compact_comments": false,
        "web_watch_compact_comments_header": false,
        "swatcheroo_rich_grid_delay": 0,
        "wn_grid_max_item_width": 0,
        "wn_grid_min_item_width": 0,
    });

    // Modify page elements (main function)
    function modifyPageElements() {
        if (window.location.href.includes("youtube.com/watch")) {
            modifySidebarVideos();
        }

        // Delay for rate limit just in case
        setTimeout(() => {
            // Wait 250ms
        }, 250);
    }

    // Function to properly format sidebar video elements
    function modifySidebarVideos() {

        // Format thumbnails
        const thumbnailDivs = document.querySelectorAll('div#thumbnail');
        thumbnailDivs.forEach(function(div) {
            div.removeAttribute("class"); // Remove existing classes

            // Apply combined styles (168 pixels width, border radius doesn't work)
            div.style.cssText = `width: 168px; position: absolute; border-radius: 2px;`;
        });

        // Modify details div spacing: Optimal min spacing was 99px for me - adjust if neccesary
        const detailsDivs = document.querySelectorAll('div#details');
        // I just put min-height because one line titles messed up spacing for some reason
        detailsDivs.forEach(div => div.style.cssText = "padding-left:176px; margin-top:-10px; min-height: 99px;");

        // Remove margins from contentsDivs (containing both thumbnail and details) to improve spacing
        const contentsDivs = document.querySelectorAll('div#contents.ytd-rich-grid-row');
        contentsDivs.forEach(div => div.style.cssText = "margin: 0px;");

        // Sepecify rich-item-renderer div spacing (includes playlist and ad items as well) because it's quite big by default
        const richItemDivs = document.querySelectorAll("div#contents.ytd-rich-grid-row > ytd-rich-item-renderer");
        richItemDivs.forEach(div => div.style.cssText = "margin-left: 0px; margin-right 0px; margin-bottom: 13px;");

        // Remove channel avatar profile pics
        const avatarLinks = document.querySelectorAll("a#avatar-link");
        avatarLinks.forEach(link => link.remove());

        // Reformat text size and spacing (doesn't quite work yet)
        const metadataLineDivs = document.querySelectorAll("div#metadata-line");
        metadataLineDivs.forEach(div => div.style.cssText = "font-size: 1.2rem; line-height: 1.8rem;");

        // Removes weird gap at the top of secondary recommendations
        const secondaryDivs = document.querySelectorAll("div#secondary");
        secondaryDivs.forEach(div => div.style.cssText = "padding-top: 0px;");

    }

    // Initialize MutationObserver: will run modifyPageElements upon change
    const observer = new MutationObserver(modifyPageElements);
    observer.observe(document.body, { childList: true, subtree: true });

})();
