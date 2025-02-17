# Simple Steam Fetch

Stable tag: 0.2.1

Fetch and import game data from the Steam API. Automatically create custom posts with detailed descriptions, screenshots, and pricing information. Compatible with JetEngine..

# Simple Steam Fetch Plugin

> [!IMPORTANT]
> Minimum PHP version: 8.0

> [!IMPORTANT]
> Minimum WordPress version: 6.0

## INSTRUCTIONS

**How to download?**

In the right section the green button: **<>Code** click, and in the dropdown menu, select the **Download ZIP** option. The downloaded file just upload it, you can easily install the downloaded file as an plugin within wordpress.

## Description

This plugin uses **Three APIs** for its functionality:

1. **Steam Store API (Unofficial)**

   - This is the main API that provides detailed information about individual games.
   - It supports multiple languages (e.g., `en`, `hu`, etc.).

2. **Steam App List API** (Highly limited)

   - This API returns a list of all apps (games, software, and DLC) without any filtering options.
   - It's useful if you want to search for and select a specific game within the admin interface.
   - **Note:** This API is slow and has a **5-minute cache restriction**, which makes it less practical for frequent updates.

3. **Steam News API** (ISteamNews)
   - Get the news for the game (limited, and you cannot specify a language, it will use the default (English)).
   - You can use shortcode to display the news for a particular game, like a feed.
   - Has not saved any data to the database, the query is done with ajax.
   - You have to put the shortocde in the post template where you saved the games. The system will automatically identify which game news should be displayed.
   - **Shortcode: [steam_game_related_news feednumber="5" label="News"]**

---

## Features and Supported Game Data

With Simple Steam Fetch, you can easily fetch and import game data from Steam.  
Currently, the following fields are supported:

- **Game Name** (`name`)
- **Is Free** (`is_free`)
- **Price** (`final_formatted`) (Always returns the current price, if it is discounted it will return the discounted price)
- **Full Game Description** (`detailed_description`)
- **Short Description** (`short_description`)
- **Header Image** (`header_image`)
- **Capsule Image (logo)** (`capsule_imagev5`)
- **Developers** (`developers`)
- **Publishers** (`publishers`)
- **Platforms** (`platforms`)
- **Categories** (`categories`)
- **Genres** (`genres`)
- **Screenshots** (`screenshots`)
- **Trailer/Movies** (Only one video is currently fetched)
- **Release Date** (`release_date`)

---

## JetEngine Meta Field Compatibility

The plugin is **JetEngine-compatible** for storing game data. It supports the following JetEngine meta fields:

- **Media** (Single image)
- **Gallery**
- **Date** (support both unix and timestamp - only if using English language)

Other standard meta fields (`text`, `textarea`, `WYSIWYG`) are also supported, even with custom plugins or meta keys.  
**Note:** The plugin does **NOT** support **JetEngine Custom Meta Storage** yet.

---

## Plugin Behavior

- **No Duplicates:** The plugin ensures no duplicate posts are created when re-fetching game data.
- **Image Handling:**
  - The following images are saved in the WordPress Media Library:
    - Header Image (`header_image`)
    - Capsule Image (`capsule_image`)
    - Screenshots (`screenshots`)
  - **Inline images** from the full game description are handled as external resources and are not saved in the media library.
- **Full Game Description:**  
  If you use **Gutenberg**, the full game description is placed inside a **Classic Block**.  
  It's recommended to manually convert it to Gutenberg blocks (just one click).

- **Re-Fetching:**
  - Images (header, capsule, and screenshots) are not re-downloaded or duplicated when a game is re-fetched.
  - You can enable a setting to delete all related images from the media library when a game (post) is deleted.

---

## Focus on Games

The plugin is currently optimized for **games only**. While it may work for **DLCs** or **software**, it’s not officially supported or guaranteed.

---

## Taxonomy Support

You can link **Platforms**, **Publishers**, **Developers**, **Genres**, and **Categories** to taxonomies.  
The plugin is also compatible with **JetEngine-created taxonomies**.

---

## Custom Post Types (CPT)

You must select which **Custom Post Type (CPT)** to use for saving the imported games.

- **JetEngine-created CPTs** are fully supported.

---

## CHANGELOG

### V 0.2.1 _2025.02.18_

- Minor hotfix

### V 0.2 _2025.02.15_

- Complete rewitten the SettingsCFG handler - **You must re-set your settings and meta mapping**
- New modularised fetch system
- New Newsfeed using the **ISteamNews API** use the following shortcode: **[steam_game_related_news feednumber="5" label="News"]** in your single-post template where your game saved

---

### V 0.1 _2025.02.14_

- Initial release
