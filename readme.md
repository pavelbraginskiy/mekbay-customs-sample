# Mekbay Custom Units Server (Sample)

This is an example of a **custom units server** for [Mekbay](https://github.com/MegaMek). It shows one working way to host your own units so they show up in Mekbay.

The sample units included here come from the *Operation Lancaster* BattleTech fan project.

> [!NOTE]
> MekBay's support for custom units is a work in progress.
> Eventually you will be able to upload `.mtf` and `.blk` unit files to MekBay directly.
> This guide explains the use of the temporary custom unit scheme that is in place until then.
>
> If you encounter any problems while using custom units on mekbay, please report them at [the MekBay issue tracker](../../../../MegaMek/mekbay/issues).
> Please use this repository's issue tracker only for reporting issues with this documentation or with the provided SVG exporter. 

---

## What you'll end up with

By the end of this guide you'll have:

1. A set of exported unit files (SVG record sheets plus a few `.json` data files).
2. A public GitHub repository hosting those files.
3. A URL you can paste into Mekbay so it loads your custom units.

## Before you start

You'll need:

- **The SVG exporter.** Download it from this repository's [Releases](../../releases) page.
- **Your unit files** — the `.mtf` and/or `.blk` files for the units you want to add.
- **A free GitHub account.** If you don't have one, sign up at [github.com](https://github.com/signup). This guide assumes you'll host your files on GitHub, since that's the easiest option.

You do **not** need to know Git or use the command line for GitHub — the web-based upload option is covered below.

---

## Step 1 — Export your units

1. Unpack the SVG exporter you downloaded into a folder of your choice.
2. Open a terminal (Command Prompt on Windows) and **navigate to the folder where you unpacked the exporter**. You do this with the `cd` ("change directory") command. The easiest way is to type `cd ` (with a space after it), then drag the exporter's folder from your file browser onto the terminal window — this pastes in the full path for you — and press Enter. For example:

   ```
   cd "C:\Users\YourName\Downloads\svgexporter"
   ```

3. Run the command below, replacing the example path with the folder that contains **all** of your `.mtf` and/or `.blk` files:

   ```
   .\bin\svgmassprinter.bat --skip-equipment --units "C:\folder\with\mtfs-blks" -o "C:\desired\output\location"
   ```

   The `-o` part is optional: If left out, the default location is `../../svgexport` (creating a folder called `svgexport` two folders up). 

> [!NOTE]
> The `.bat` file is for Windows. On **Linux or macOS**, run `./bin/svgmassprinter` instead:
>
> ```
> ./bin/svgmassprinter --skip-equipment --units "/path/to/mtfs-blks" -o "/desired/output/location"
> ```

> [!WARNING]
> Run this from the folder **above** `bin` (the one you unpacked into). Do **not** `cd` into the `bin` directory and run the exporter from there, that will not work.

When it finishes, the exporter will have created your record sheets and data files in its output folder.

> [!NOTE]
> **Prefer to host the files yourself?** Hosting on GitHub (Steps 2–5) is the most convenient option for most people, but the exported files can be served by any web server. For example, from your export folder you could run `npx http-server . --cors -p 8000`. If you go this route, just make sure the server sends CORS headers so Mekbay can read the files, then skip to Step 6 and use your server's base URL.

## Step 2 — Create a public GitHub repository

1. Make sure you're signed in to GitHub.
2. Create a **new repository**. It **must be public** so that Mekbay can read the files.
3. Give it any name you like, then create it.

## Step 3 — Upload your exported files

You need to get everything from your export folder into the repository.

- **If you know Git**, you can commit and push the files the usual way.
- **Otherwise**, use the **Add file → Upload files** option on the GitHub website:

<img width="324" height="171" alt="The GitHub 'Add file' menu with the 'Upload files' option" src="https://github.com/user-attachments/assets/36e000ca-371c-4eaa-ac03-d496105616f6" />

Upload the **entire contents** of your export folder (for example, everything inside `C:\where\you\want\the\export\to\go`).

> [!TIP]
> If you have more than roughly 100 units, GitHub's web uploader may not accept them all at once. Just upload them in several smaller batches.

## Step 4 — Keep it updated when you add units later

To add more units in the future, **repeat Steps 1–3**.

> [!IMPORTANT]
> It isn't enough to upload just the new units. The `.json` files list every custom unit, so you must **re-export and replace the `.json` files** as well — otherwise your new units won't appear.

## Step 5 — Get your server URL

Mekbay needs the **raw** base URL for your repository.

For this sample repository, the URL is:

```
https://raw.githubusercontent.com/pavelbraginskiy/mekbay-customs-sample/refs/heads/main
```

To find the URL for **your** repository:

1. Open any file in your repository on GitHub.
2. Click the **Raw** button.
3. Copy the address from your browser, and remove the file name and path at the end so you're left with the base URL (the part ending in `.../refs/heads/main`).

## Step 6 — Add the server to Mekbay

1. In Mekbay, open **Advanced settings**.
2. Add your repository URL to the list of **custom unit servers**.

<img width="1039" height="369" alt="Mekbay Advanced settings showing the custom unit servers list" src="https://github.com/user-attachments/assets/23e69643-89dd-41a8-8fc0-8c2dffed23f5" />

That's it — your custom units should now be available in Mekbay.
