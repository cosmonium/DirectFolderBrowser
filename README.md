# DirectFolderBrowser
A file and folder browser for Panda3D using DirectGUI

## Features
This is a simple fullscreen file and folder browser with a basic featureset. Currently implemented are:

- Browsing files and folders
- Show/Hide hidden files (using unix like leading dot)
- Create new folders
- Filter by file extension
- Resizes with window size changes
- Makes use of the <a href="https://github.com/fireclawthefox/DirectTooltip">Tooltip class</a>

## How to use
To add a browser instance to your running Panda3D application, just instantiate it like shown here:
```
from DirectFolderBrowser import DirectFolderBrowser

# this command will be called by the browser
def callbackCommand(ok):
    if ok == 1:
        print("User Clicked OK")
        
        # print the selected file
        print(browser.get())
        
        browser.hide()
        # Destroy the browser if it's not needed anymore
        #browser.destroy()
    elif ok == 0:
        print("User Clicked Cancel")
        browser.hide()
        browser.destroy()

# show the browser as file browser
browser = DirectFolderBrowser(callbackCommand, fileBrowser=True)
```
The DirectFolderBrowser accepts a few arguments.
- <b>command:</b> The command that will be called on closing the browser
- <b>fileBrowser:</b> If set to True the browser will show files, otherwise it will only show folders
- <b>defaultPath:</b> The initial path the browser will be set to show
- <b>defaultFilename:</b> The filename that will be set by default, <i>only usefull if fileBrowser is True</i>
- <b>fileExtensions:</b> A list of extensions. Only files with those extensions will be shown. <i>Only usefull if fileBrowser is True</i>
- <b>tooltip:</b> An instance of the <a href="https://github.com/fireclawthefox/DirectTooltip">Tooltip class</a> to display tooltips for certain parts of the editor
