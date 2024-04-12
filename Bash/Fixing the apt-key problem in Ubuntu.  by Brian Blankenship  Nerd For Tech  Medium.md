[

![Brian Blankenship](https://miro.medium.com/v2/resize:fill:88:88/0*kmfqB3PpyjJGEga-.jpg)



](https://medium.com/@c0dezer019?source=post_page-----4bae7fe545aa--------------------------------)[

![Nerd For Tech](https://miro.medium.com/v2/resize:fill:48:48/1*53-lvCPnPV4sTOmvcITDxw.png)



](https://medium.com/nerd-for-tech?source=post_page-----4bae7fe545aa--------------------------------)

![](https://miro.medium.com/v2/resize:fit:1167/0*yiKE9HfPx5PaOiGF)

Photo by [Kelly Sikkema](https://unsplash.com/@kellysikkema?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

Sometimes, especially if you’re into development, you may have to add a source to the package manager. While a lot of packages that you get as a .deb will automatically solve this issue, if you’re unable to directly download a deb file, you’re probably going to be faced with this issue.

## The problem

The issue? apt-key is deprecated and will not be included post Ubuntu 22.04 and Debian 11, but a lot of documentation has yet to be updated for the new method. The only part of apt-key that isn’t deprecated is apt-key del to facilitate the ability to remove keys to migrate to the new way of storing keys.

So you may have noticed this when you update, or install a package, but you’ll get the following warning:

> W: [https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/jammy/dists/pgadmin4/InRelease](https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/jammy/dists/pgadmin4/InRelease): Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.

This is because they key was added like the below:

```
<span id="a6b4" data-selectable-paragraph="">$ wget — quiet -O — <a href="https://www.postgresql.org/media/keys/ACCC4CF8.asc" rel="noopener ugc nofollow" target="_blank">https://www.postgresql.org/media/keys/ACCC4CF8.asc</a> | sudo apt-key add -</span>
```

## The solution

In order to fix the current issues, we will need to first delete the keys from the keyring for the ones you’re getting errors for. If you’re not getting an error, don’t do anything, because it isn’t broken. That being said, the first step to deleting the key is getting the last 4 of its id by doing this:

```
<span id="9a85" data-selectable-paragraph="">$ apt-key list</span>
```

You don’t need sudo for this. After performing this command you’ll see output like below:

```
<span id="ae05" data-selectable-paragraph=""> — — — — — — — — — — <br>pub rsa4096 2017–06–22 [SC]<br> xxxx xxxx xxxx xxxx xxxx xxxx xxxx xxxx C33A 7AFF<br>uid [ unknown] Pop OS (ISO Signing Key) &lt;<a href="mailto:info@system76.com" rel="noopener ugc nofollow" target="_blank">info@system76.com</a>&gt;<br>sub rsa4096 2017–06–22 [E]</span><span id="7ad9" data-selectable-paragraph="">/etc/apt/trusted.gpg.d/cubic-wizard-ubuntu-release.gpg<br> — — — — — — — — — — — — — — — — — — — — — — — — — — — <br>pub rsa4096 2015–11–05 [SC]<br> xxxx xxxx xxxx xxxx xxxx xxxx xxxx xxxx B4F1 283B<br>uid [ unknown] Launchpad PPA for PJ Singh</span><span id="23c2" data-selectable-paragraph="">/etc/apt/trusted.gpg.d/microsoft.gpg<br> — — — — — — — — — — — — — — — — — — </span>
```

The id is the 10 segment long line, the one with x’s in (these are numbers, not x’s)

Take the last four numbers and concat them together (so for C33A 7AFF it would be C33A7AFF). Now perform this command:

```
<span id="f916" data-selectable-paragraph="">$ sudo apt-key del xxxxxxxx</span>
```

Again, the x will be the last 8.

Now the final step is to re-add the key in the new method. It will be similar to the previous, we will only change the part after the bitwise or operator (|) of the command.

```
<span id="e902" data-selectable-paragraph="">$ wget -qO- <a href="https://myrepo.example/myrepo.asc" rel="noopener ugc nofollow" target="_blank">https://myrepo.example/myrepo.asc</a> | sudo tee<br> /etc/apt/trusted.gpg.d/myrepo.asc</span>
```

The key should have the asc description. It also may not allow you to place it in trusted.gpg.d at first so if ends up creating it in /etc/apt instead or your cwd move it to trusted.gpg.d:

```
<span id="77bf" data-selectable-paragraph="">$ sudo mv myrepo.asc /etc/apt/trusted.gpg.d</span>
```

Your problem should now be fixed.