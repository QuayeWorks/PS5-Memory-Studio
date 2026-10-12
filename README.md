# PS5 Memory Studio

**A memory scanner and editor for jailbroken PS5 consoles, controlled from your phone or computer.**

PS5 Memory Studio is a QuayeWorks project built for people who like to experiment with their games. Browse running processes, search for values, edit memory, freeze addresses, and keep game-specific cheat profiles in one place. The interface runs in your browser, so there's no companion app to install on your PC or phone.

> **Development status:** v1.12 is a test candidate, not a finished public release. Process inspection and scanning/editing of the QuayeWorks test application have been tested on a real PS5. The new real-game read/write engine and console pairing system are included, but full game compatibility still needs physical-console validation. Some games may not work yet.

## What you'll need

- A PS5 already running a compatible homebrew environment. Development and hardware testing have focused on **firmware 13.60, Relapse, and OnionHEN v0.9.0-beta2**.
- The `QWMS00001.elf` plugin from this project's release package.
- A PC or phone on the same local network as the PS5.
- A way to copy files to the console, such as an FTP client or PS5 file manager.

Memory Studio **does not jailbreak the PS5**. Load your existing exploit and OnionHEN first.

## Install on the PS5

1. Load Relapse and OnionHEN as you normally would.
2. If Memory Studio is already running, stop it before replacing the plugin.
3. Copy `QWMS00001.elf` to:

   ```text
   /data/OnionHEN/plugins/QWMS00001.elf
   ```

4. Start Memory Studio from OnionHEN's plugin controls.
5. On your phone or computer, open:

   ```text
   http://YOUR-PS5-IP:13965
   ```

   Replace `YOUR-PS5-IP` with the console's local IP address. You can find it in the PS5's network settings.

That's it for the initial connection. You don't need to install anything in your browser.

**For developer testing:** The package also includes `QWMT00001.elf`, a separate QuayeWorks test application. Put it in the same plugins folder if you're running the DEV test campaign. It isn't required just to open Memory Studio or browse its interface.

## Pair your phone or computer

The first time you connect, Memory Studio asks you to pair the browser with your PS5.

1. Name your device and choose **Read Only**.
2. Select **Show code on PS5**.
3. Look for the six-digit code in the PS5 notification. If notifications aren't available, follow the on-console instructions, if offered.
4. Enter the code in your browser and select **Pair**.

The code expires after five minutes. Once paired, that browser can reconnect automatically on future visits.

If you want to change game-memory values, open **Devices & Security** and choose **Request Memory Editing**. The PS5 displays another code to approve that higher permission. You can also view and revoke paired devices from the security screen.

## Using Memory Studio

**Find a game.** Start an offline game, then open the **Processes** view and select its running process. Choose **Open game memory** when available.

**Search for a value.** In **Memory Studio**, choose a data type, enter a value you can see in the game (for example, your ammunition count), and run **First Scan**. Change that value through normal gameplay, then use **Next Scan** to narrow the matches.

**Edit or freeze an address.** Select a result and double-click its value, or press Enter. Enter a replacement and save it. You can also freeze supported writable addresses to keep a value from changing. Memory Studio checks the selected process and address before attempting a write and reads the value back afterward.

**Save a profile.** Open the **Cheat Profiles** panel to save compatible game-specific entries for later use. Profiles don't activate themselves when a game starts. Some addresses, especially temporary heap addresses, cannot be saved as portable profiles.

Supported search types include **Byte, 2 Bytes, 4 Bytes, 8 Bytes, Float, and Double**. Integer searches can also use hexadecimal values.

## DEV testing

The **DEV** menu is for testing builds, collecting diagnostics, and checking whether new functionality actually works on the console. Select **Run consolidated tests** to start the guided campaign. It pauses when you need to perform an action on the PS5, and it can resume unfinished checks rather than starting over.

At the end, use **Download comprehensive JSON** to save the results. If you're reporting a bug, that file is more useful than a screenshot of a generic error message. Review reports before sharing them, and never post pairing codes or device credentials.

## A few things to know

- **Offline use only.** Don't use Memory Studio in multiplayer or with online services. Back up important saves before editing memory.
- **Game support is still being tested.** A process appearing in the list doesn't guarantee its memory can be safely read or written.
- **Keep it local.** The dashboard currently uses HTTP on your LAN, not encrypted HTTPS. Don't forward port `13965` to the internet, and use a network you trust.
- **Not all edits are reversible.** Memory can change as a game runs, and a failed write may leave an altered value. Restart the game if you are unsure of its state.

## Having trouble?

**The page won't open:** Check that OnionHEN and the plugin are running, that you're using the correct PS5 IP address, and that both devices are on the same network.

**No pairing notification:** Try **Show code on PS5** again after the cooldown. Check for an on-console fallback. Pairing will not succeed if neither method is available.

**You can scan, but can't edit:** Your device may be approved for **Read Only**. Request **Memory Editing** in **Devices & Security**.

**A game isn't available or a scan fails:** Check that the game is running offline and review **Diagnostics**. Include the game title, game version, firmware, OnionHEN version, and a sanitized DEV report when opening an issue.

## Credits and license

Developed by **QuayeWorks**, using the PS5 homebrew SDK and OnionHEN ecosystem. Thanks to the developers and researchers whose work makes homebrew on the PS5 possible.

See [LICENSE](LICENSE) for the project's licensing terms. PS5 and PlayStation are trademarks of Sony Interactive Entertainment. This project is not affiliated with or endorsed by Sony.
