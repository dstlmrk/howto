# Ubuntu packages

## Dostupne baliky

Find out all available versions of Chromium web
browser from the Ubuntu repositories.

```
apt-cache policy chromium-browser
```

In the output, you’ll see there is two words:

* **Installed:** This will tell you the version that you have
  installed in your Ubuntu system.
* **Candidate:** This is actual version that will be installed
  when you install Chromium browser using apt-get.

There are also other couple of commands available to check the package version from Ubuntu repositories.

```
apt-cache showpkg chromium-browser
```
