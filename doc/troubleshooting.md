# Settings that can fix websites

If changing one of these settings fixes your bug, please visit the corresponding Github issue and let us know you encountered the bug.

-   `:seturl $URL_OF_THE_WEBSITE noiframe true` and then reload the page. This disables the Tridactyl commandline on a specific url. [#639](https://github.com/tridactyl/tridactyl/issues/639)
-   `:set allowautofocus true` and then reload the page. This allows website to use the javascript `focus()` function. [#550](https://github.com/tridactyl/tridactyl/issues/550)
-   `:set modeindicator false` and then reload the page. This disables the mode indicator. [#821](https://github.com/tridactyl/tridactyl/issues/821)

# Native Editor/Messenger issues

If you're having trouble running your editor on OSX, you might be having \$PATH issues: [#684](https://github.com/tridactyl/tridactyl/issues/684). The solution is to specify the absolute path to your editor, like this: `:set editorcmd /usr/local/bin/vimr`.

If you're encountering problems on windows, you might want to try some of the workarounds mentioned here: [#797](https://github.com/tridactyl/tridactyl/issues/797).

If you're on Unix, running `printf '%c\0\0\0{"cmd": "run", "command": "echo $PATH"}' 39 | ~/.local/share/tridactyl/native_main.py` in a terminal after you have installed the native messenger will tell you if there are any missing modules.

# Getting logging information

Tridactyl can selectively display logs for certain components. These components are the following:

-   messaging
-   cmdline
-   controller
-   containers
-   hinting
-   state
-   styling
-   excmds

In order to activate logging for a component, you can use the following command: `:set logging.$COMPONENT DEBUG`. Then, to get the logs, click the hamburger menu in the top right of Firefox, click "Web Developer", then click "Browser Console". Open the menu again and click "Web Console" in the same place.

This will open a two consoles where Tridactyl's messages are logged. Click on the little bin icons in the consoles in order to remove previous messages and try to re-trigger the bug. Copy the logs as you would any other text, and then paste them in your GitHub issue in a block surrounded by three backticks like so:

```
\`\`\`
logs
go
here
\`\`\`
```

Unfortunately, Firefox truncates some objects, so if there are any that look particularly important, please copy them manually by right clicking on them and clicking "Copy object".

Once you have finished troubleshooting, we recommend that you run `unset logging` as the logs can slow Tridactyl down a bit.
