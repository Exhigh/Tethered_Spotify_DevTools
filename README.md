# Tethered_Spotify_DevTools
This patch enables us to activate the dev tools for Spotify in a tethered manner.

## Usage
Copy the files included in the zip file from the Release Section into Spotify's Directory.          
Start Spotify or Restart Spotify if it was already running and presto !. 

Dev-Tools has been acitvated and with the right context menu working as inteded,           
as well as the patch working even after restarts and reloads of the application.

`Note`: To avoid showing error messages saying that Lyptus32.dll was not found when running Spotify
	  via the terminal or powershell, inside the file `Koaloader.json`, 
	  in the line for `path` point to `Lyptus32.dll` absolute location within the double quotes.
	  
	  Eg. `C:\\Users\\Username\\AppData\\Roaming\\Spotify\\Lyptus32.dll` or `C:/Users/Username/AppData/Roaming/Spotify/Lyptus32.dll`

### Reasons
I used this method to achieve what we could basically already achieve but was a clunky solution as the solution,
is to patch the memory address that holds the `app.enable-developer-mode` value while the application runs, 
also there exists this other solution that patches the value of `app-developer` within `offline.bnk` file within Spotify's Local AppData.

Plus this didn't allow us to have access to the right context menu which although we could get working by patching,
the `xpui.js` file within `xpui.spa`. Anyway having gone down the path of trying to find something better, I stumbled across this method.

Also, this method is resilient across updates as we won't be required to update the pattern for every single update, 
as this method activates the Dev-Tools from Spotify version `1.1.80+ - 1.1.88+` which is quite convenient.

Not to say that this pattern will hold true for future patches to come but updating this pattern will be far easier,
as we will just need to update the pattern within `Lyptus.json`.

#### Underlying-Method
So, basically we use Koaloader to load `Lyptus32.dll` into the Spotify Executable, 
this is achieved using Search-Order Hijacking using Koaloader.

We then search for a specific Hex String Pattern in the Spotify Executable which then we replace,
this Hex String with the patched Hex String to enable the Dev-Tools within Spotify.

This is quite the simplification on how this works, to be frank you should check the work of Koaloader and Lyptus,
in their respective Repos to have a better understanding as to how this works.

#### Softwares Used For Obtaining The Hex String Pattern
* `Ghidra`
* `Cheat-Engine`


## Acknowledgements

* [Koaloader](https://github.com/acidicoala/Koaloader)
* [Lyptus](https://github.com/acidicoala/Lyptus)

 Cheers - Exhigh
