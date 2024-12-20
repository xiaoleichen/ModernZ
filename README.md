<h1 align="center">ModernZ - A Sleek Alternative OSC for mpv</h1>

A sleek and modern OSC for [mpv](https://mpv.io/), this project is a fork of ModernX designed to enhance functionality by adding more features, all while preserving the core standards of mpv's OSC.

![modernz-osc](https://github.com/user-attachments/assets/03ea7f7d-7963-4ced-867e-4562460bbf0e)

<p align="center">
    <a href="#installation"><strong>Installation »</strong></a>
  <br>
  <a href="#configuration">Configuration</a>
  ·
  <a href="#controls">Controls</a>
  ·
  <a href="#interactive-menus">Interactive Menus</a>
  ·
  <a href="#translations">OSC Language</a>
  ·
  <a href="#extras">Extra Scripts</a>
</p>

## Features

- 🎨 Modern, customizable interface [[options](#configuration)]
- 📷 Image Viewer mode with zoom controls [[details](/docs/IMAGE_VIEWER.md)]
- 🎛️ Buttons: download, playlist, speed control, screenshot, pin, loop and more. [[details](/docs/CONTROLS.md)]
- 📄 Interactive menus for playlist, subtitles, chapters, audio tracks and audio devices [[details](#interactive-menus)]
- 🌐 Multi-language support with JSON [locale](#translations) integration
- ⌨️ Configurable controls [[details](#controls)]
- 🖼️ Video thumbnail previews with [thumbfast](https://github.com/po5/thumbfast)

## Customization Showcase

Don't like the default white buttons and text? ModernZ is fully customizable! Change colors and button layouts to match your style:

![modernz-osc_colors_top](https://github.com/user-attachments/assets/b5f04e5d-91d0-41ae-ba14-ebac4b45aaa5)

![modernz-osc_colors_bottom](https://github.com/user-attachments/assets/a29bb34e-14e9-4702-9ef3-9f308e71237d)

See the [Color Customization](docs/USER_OPTS.md#colors-and-style) section in the configuration guide for details on how to customize colors and buttons.

## Interactive Menus

ModernZ supports mpv's built-in console/select ([v0.39+](https://github.com/mpv-player/mpv/discussions/14903)) for playlist, subtitles, chapter navigation and more.

[![preview_menus](https://github.com/user-attachments/assets/4b7a3139-81f1-409b-98f5-f090a81d5ee6)](/docs/INTERACTIVE_MENUS.md)

## Installation

1. **Disable Stock OSC**

   - Add `osc=no` in your `mpv.conf`

2. **Copy Files**

   - Place `modernz.lua` in your mpv scripts directory
   - Place `fluent-system-icons.ttf` in your mpv fonts directory
   - (OPTIONAL) Place `thumbfast.lua` in your mpv scripts directory

3. **Locations**

   ```
   Linux:   ~/.config/mpv/
   Windows: C:/Users/%username%/AppData/Roaming/mpv/
   macOS:   ~/Library/Application Support/mpv/
   ```

4. **Folder Structure** [[mpv manual](https://mpv.io/manual/master/#files)]
   ```
   mpv/
   ├── fonts/
   │   └── fluent-system-icons.ttf
   ├── script-opts/
   │   └── modernz.conf
   └── scripts/
   	   ├── modernz.lua
   	   └── thumbfast.lua (optional)
   ```

## Configuration

1. Create `modernz.conf` in the `/script-opts` folder to customize settings

   - [Download default modernz.conf](./modernz.conf)

2. Example short configuration:

   ```
   # Seekbar colors (Hex format)
   seekbarfg_color=#B7410E

   # Interface options
   showplaylist=no
   title=${media-title}
   scalewindowed=1.0
   windowcontrols=auto
   ```

For a full list of options, [check out the detailed user options here](docs/USER_OPTS.md).

## Controls

### Button Interactions

- Left click: Primary action
- Right click: Secondary action
- Middle click/Shift+Left click: Alternative action

> [!NOTE]
> Middle clicking performs the same function as `Shift+left mouse button`, allowing for one handed use

For a full list of interactions, check out the [Button Interactions Guide](docs/CONTROLS.md).

### Keybinds

ModernZ doesn't set keybinds by default to avoid interfering with your current setup. You can add keybinds in `input.conf` if you prefer:

```
w   script-binding modernz/progress-toggle     # Toggle progress bar
x   script-message-to modernz osc-show         # Show OSC
y   script-message-to modernz osc-visibility   # Toggle visibility
z   script-message-to modernz osc-idlescreen   # Toggle idle screen
```

## Translations

ModernZ is currently available in English, but you can easily switch it to your preferred language! Here's how:

1. **Download the locale pack:**

Grab the [modernz-locale.json](/extras/locale/modernz-locale.json) file from this repository. This file holds translations for various languages.

2. **Add the locales to mpv:**

Copy the downloaded `modernz-locale.json` file to your mpv's `/script-opts` folder.

3. **Choose your language:**

There are two ways to set your preferred language:

- **Recommended:** Use the `modernz.conf` file

  ```ini
  # Example configuration in modernz.conf
  # Set language to Simplified Chinese
  language=zh
  ```

- **Alternative:** Edit the `modernz.lua` script

  Open `modernz.lua` and find the `user_opts` section near the beginning. Change the `language` value to your preferred code:

  ```lua
  local user_opts = {
      -- General
      language = "en",  -- Change this to your preferred language code
      ...
  }
  ```

**Need More Info?**

For a complete list of available languages, contribution guidelines, and in-depth translation documentation, head over to the [TRANSLATIONS.md](docs/TRANSLATIONS.md).

## Extras

The following scripts are ones I wrote and maintain, feel free to use them if they're useful to you.

- [Pause-Indicator-Lite](/extras/pause-indicator-lite) - A simple script that displays an indicator on pause

- [ytdlAutoFormat](https://github.com/Samillion/mpv-ytdlautoformat) - A simple mpv script to automatically change `ytdl-format` (yt-dlp) for specified domains.

- [BoxtoWide](https://github.com/Samillion/mpv-boxtowide) - A simple mpv script to change 4:3 aspect-ratio of video files/streams to 16:9 automatically.

For even more useful scripts, check out the [mpv User Scripts Wiki](https://github.com/mpv-player/mpv/wiki/User-Scripts). It offers a wide range of community-contributed scripts to enhance your mpv experience.

## History

- [Samillion/ModernZ](https://github.com/Samillion/ModernZ)
  - forked from [zydezu/ModernX](https://github.com/zydezu/ModernX)
  - forked from [dexeonify/ModernX](https://github.com/dexeonify/mpv-config/blob/main/scripts/modernx.lua)
    - forked from [cyl0/ModernX](https://github.com/cyl0/ModernX)
    - forked from [maoiscat/mpv-osc-modern](https://github.com/maoiscat/mpv-osc-modern)

**Why fork yet again?**

- To add many features in: [Color Customization](docs/USER_OPTS.md#colors-and-style), [Options](docs/USER_OPTS.md) and [Locale Integration](docs/TRANSLATIONS.md)
- To integrate console and select into the osc, which inspired mpv to apply it in the stock osc. [ref [#1](https://github.com/mpv-player/mpv/pull/15016), [#2](https://github.com/mpv-player/mpv/pull/15031)]
- To add a dedicated layout for images. [[details](/docs/IMAGE_VIEWER.md)]
- To re-do the project entirely to match mpv's stock osc standards, to ensure compatibility
- To eliminate old bugs and redundancy within the code

In essence, to modernize and revive the `Modern` origin.

Having said that, ModernZ still uses parts of the old code, and every previous and current fork author and contributor deserve credit (including mpv's stock osc), that is why they're mentioned in detail.

#### Credits:

- Font: UI Fluent System Icons [[details](https://github.com/microsoft/fluentui-system-icons)] [[font file](https://github.com/Samillion/ModernZ/blob/main/fluent-system-icons.ttf)]
- Font modified by [Xurdejl](https://github.com/Xurdejl) for use on ModernZ osc
- [mpv](https://github.com/mpv-player/mpv) and their [osc.lua](https://github.com/mpv-player/mpv/blob/master/player/lua/osc.lua), as ModernZ osc was re-based on the stock osc standards and applies updates from it
- All modern osc origin and their forks as mentioned in [history](#history)
- All [contributors](https://github.com/Samillion/ModernZ/graphs/contributors), testers and users that helped directly or indirectly with ModernZ osc ❤️
