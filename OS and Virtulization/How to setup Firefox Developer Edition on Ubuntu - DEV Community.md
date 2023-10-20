Do you want to install and use Firefox Developer Edition on your Ubuntu and don’t know how to go about it?! If your answer is yes, then this article is for you. Am sure you’ve seen some documentations out there but in this one we will add Firefox Developer Edition to our Unity launcher. You’re welcome! 😉

Please follow the steps below…

**Step 1**  
Download the firefox\*.tar.bz2 file from **[Mozilla’s website](https://www.mozilla.org/en-US/firefox/developer/)**.

**Step 2**  
Open Terminal.

**Step 3**  
Navigate to the folder where the file is saved.

**Step 4**  
Copy firefox\*.tar.bz2 file to the /opt folder.  

```
sudo cp -rp firefox*.tar.bz2 /opt
```

Enter fullscreen mode Exit fullscreen mode

**Step 5**  
Delete the downloaded firefox\*.tar.bz2 file.  

```
sudo rm -rf firefox*.tar.bz2
```

Enter fullscreen mode Exit fullscreen mode

**Step 6**  
Navigate to the /opt directory.  

```
cd ~
cd /opt
```

Enter fullscreen mode Exit fullscreen mode

**Step 7**  
Un-tar the firefox\*.tar.bz2 file in opt folder.  

```
sudo tar xjf firefox*.tar.bz2
```

Enter fullscreen mode Exit fullscreen mode

**Step 8**  
Delete the firefox\*.tar.bz2 file in opt folder.  

```
sudo rm -rf firefox*.tar.bz2
```

Enter fullscreen mode Exit fullscreen mode

**Step 9**  
Change ownership of the folder containing Firefox Developer Edition /opt/firefox  

```
sudo chown -R $USER /opt/firefox
```

Enter fullscreen mode Exit fullscreen mode

**Step 10**  
Create the Firefox Developer Edition's shortcut  

```
nano ~/.local/share/applications/firefox_dev.desktop
```

Enter fullscreen mode Exit fullscreen mode

The content of this file is,  

```
[Desktop Entry]
Name=Firefox Developer 
GenericName=Firefox Developer Edition
Exec=/opt/firefox/firefox %u
Terminal=false
Icon=/opt/firefox/browser/chrome/icons/default/default128.png
Type=Application
Categories=Application;Network;X-Developer;
Comment=Firefox Developer Edition Web Browser.
StartupWMClass=Firefox Developer Edition
```

Enter fullscreen mode Exit fullscreen mode

**Step 10**  
Mark the launcher as trusted and make it executable.  

```
chmod +x ~/.local/share/applications/firefox_dev.desktop
```

Enter fullscreen mode Exit fullscreen mode

___

I hope this article has helped you to set-up your new Firefox Developer Edition.

**Thank you**