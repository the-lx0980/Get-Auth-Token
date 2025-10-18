# Get-Auth-Token

Nice — you can get your Stremio token entirely on your Android phone using a small bookmarklet (a bookmark that runs JavaScript). Follow these steps exactly — no PC required.

> ⚠️ Security reminder: your auth.key is like a password. Do not share it. Keep it private and only paste it into scripts you trust.




---

A — Create the bookmarklet (one-time setup)

1. Open Chrome (or Firefox) on your Android phone and go to any website (e.g. https://example.com).


2. Tap the star (☆) to bookmark the page.


3. Open your bookmarks and edit the bookmark you just created. Change the Name to ```Get Stremio Token``` (or anything you like).


4. In the URL field, replace the existing URL with this single-line JavaScript code exactly as written:


```
javascript:(function(){try{var p=localStorage.getItem('profile');if(!p)throw'No profile found. Are you logged in?';var t=JSON.parse(p).auth&&JSON.parse(p).auth.key; if(!t)throw'No token found'; if(navigator.clipboard&&navigator.clipboard.writeText){navigator.clipboard.writeText(t).then(function(){alert('Token copied to clipboard:\\n'+t);},function(){prompt('Token (copy):',t);});}else{prompt('Token (copy):',t);} }catch(e){alert('Error: '+e);} })();
```
5. Save the bookmark.




---

B — Use the bookmarklet to fetch the token

1. Open Chrome and go to https://web.stremio.com/.


2. Log in to your Stremio account (make sure you remain on that page and are logged in).


3. Open your bookmarks and tap the Get Stremio Token bookmark you created.


4. The bookmarklet will try to copy the token to your clipboard and show it in an alert.

If clipboard copy works you’ll see an alert saying Token copied to clipboard: and the token.

If clipboard copy is blocked, a prompt will appear with the token — copy it manually from there.




If you get an error No profile found. Are you logged in? — make sure you are actually logged into web.stremio.com (not the mobile app) in the same browser tab when you run the bookmarklet.


---

C — What to do with the token

Paste it into the Termux script (or whatever mobile script) where it says YOUR_TOKEN_HERE.

After you finish using it, consider revoking or rotating it in your account settings if you think it was exposed.



---

D — If the bookmarklet fails

Try in Firefox for Android (bookmark editing works there too).

Or install Kiwi Browser (Chromium-based, supports extensions/bookmarks well) and repeat.

As a last resort, if you can’t make the bookmarklet run, tell me the exact error message you see and I’ll give the next troubleshooting step.



---

