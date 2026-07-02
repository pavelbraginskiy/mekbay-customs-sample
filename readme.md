Example custom units server for Mekbay.
Sample units are from the *Operation Lancaster* BT fan project.

How to do this for your own units:
- Download the SVG exporter from this repo's releases
- Create the export: In a termainal, navigate to the directory where you unpacked the exporter and run `.\bin\svgmassprinter.bat --skip-equipment --units "C:\folder\with\all\your\blk-mtf\files" -o "C:\where\you\want\the\export\to\go"`
- Figure out some way to host the resulting files. The easiest way is probably to put it in a github repo, I'll assume that's what you're doing from now on.
- Create a *public* github repository.
- Get the export you made into the repo. If you know git you can do it the normal way, otherwise use the Upload Files option from the github website:
<img width="324" height="171" alt="image" src="https://github.com/user-attachments/assets/36e000ca-371c-4eaa-ac03-d496105616f6" />

- Upload the entire folder `"C:\where\you\want\the\export\to\go"` from before. If you have >~100 units you might need to do this in multiple steps.
- If you want to add more files in the future, repeat the above steps - it isn't enough to just add in the new units, the `.json` files will also have to be replaced to include all of the custom units you want in total.
- Get URL to use for mekbay. For this repo, it's `https://raw.githubusercontent.com/pavelbraginskiy/mekbay-customs-sample/refs/heads/main`. You can work it out for your repo by viewing any file and clicking "Raw" to generate this url. Cut off the filename at the end - it should probably end in `/refs/heads/main`.
- At time of writing, custom unit servers are only supported on next.mekbay.com, not yet on mekbay.com itself.
- In advanced settings, add the URL for your repo to the list of custom unit servers.
<img width="1039" height="369" alt="image" src="https://github.com/user-attachments/assets/23e69643-89dd-41a8-8fc0-8c2dffed23f5" />
