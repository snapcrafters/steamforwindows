<h1 align="center">
  <img src="snap/gui/steamforwindows.png" alt="Steam for Windows">
  <br />
  Steam for Windows
</h1>

<p align="center"><b>This is the snap for Steam for Windows</b>. It works on Ubuntu, Fedora, Debian, and other major Linux
distributions.</p>

<p align="center">Published for <img src="http://anything.codes/slack-emoji-for-techies/emoji/tux.png" align="top" width="24" /> with :gift_heart: by Snapcrafters</p>

<!-- <p align="center">
<a href="https://build.snapcraft.io/user/snapcrafters/steamforwindows"><img src="https://build.snapcraft.io/badge/snapcrafters/steamforwindows.svg" alt="Snap Status"></a>
</p> -->

## Install

    snap install steamforwindows --edge
    snap connect steamforwindows:joystick

([Don't have snapd installed?](https://snapcraft.io/docs/core/install))

![Steam for Windows](screenshot.png?raw=true "Steam for Windows")

## Reusing this snap

You can use this snap as a reference for creating snaps of other WINE
compatible Windows applications. Here are the main things you'll need to
modify:

  * Change the meta data and `apps:` and `parts:` names from `steamforwindows`.
  * Modify the `command:` to reference the executable the application/game should launch.
  * If you can't redistrbute the application/game use `INSTALL_URL:` to reference a web accessible installer.
  * Modify the `install_app()` and `launch_app()` functions in [`snap/scripts/sommelier`](snap/scripts/sommelier) to suit the application/game you're snapping.
  * If your application/game requires some winetricks to work then you can specify them via `TRICKS:` in the `environment:` of the main `command:`. For example:

```
    environment:
      WINEPREFIX: "$SNAP_USER_COMMON/.wine"
      TRICKS: "winxp steam"
      LC_ALL: "C.UTF-8"
```

One other point of interest is that `yad` is staged in the snap and a faux
`zenity` script is included that execs `yad`. We do this because `yad` is
argument compatible with `zenity` but pulls far fewer package dependencies.

If you have any questions about creating snaps of WINE compatible Windows
applications then [post in the Snapcraft forum](https://forum.snapcraft.io).
