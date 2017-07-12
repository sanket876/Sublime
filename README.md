# Sublime
---------------
Sync sublime settings across all machines.
I just set up a good solution for this, it requires dropbox. I am currently using this to sync plugins and settings across ~5 different sublime installs on windows, linux, osx, and a few vm's.

Step 1: use PackageControl to manage all your plugins, its awesome.
Step 2: Add a "Sublime" directory to your root drop-box directory (I replicated the full directory structure for the hell of it, {DropBox}/Sublime/Packages/User). Make sure sublime is closed, and move the contents of {SublimeRoot}/Packages/User in to the dropbox directory you just made. Delete {SublimeRoot}/Packages/User, and replace it with a symlink that points to {DropBox}/Sublime/Packages/User.
Use this same process on every computer where you use sublime, it accomplishes 2 things.

1) The contents of your User/ directory are synced, so all your custom settings are the same across machines.
2) Every time PackageControl starts up, it checks the Package Control.sublime-settings in your User/ directory. If if finds a plugin that should be installed according to the settings, but isn't actually installed, it automatically installs it, no questions asked.
Setting up another computer with this solution simply requires sublime and package control to be installed, then just delete the {SublimeRoot}/Packages/User/ directory and point it to the copy in dropbox with a symbolic link. Next time you fire up sublime, package control will automatically install all your plugins.

Creating the symbolic links: execute from the {Sublime}/Packages directory

Windows: mklink /D .\User C:\Users\[username]\Dropbox\Sublime\Packages\User
Linux/OSX: ln -s {DropboxRoot}/Sublime/Packages/User ./User
