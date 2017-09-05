See [the MediaWiki Extension page](https://www.mediawiki.org/wiki/Extension:WPMW) for documentation.

### If you are in  Hurry ###
* Create a folder AuthWP in extensions directory of your MediaWiki installation root
* Clone this git repo in that directory 
* Finally, paste the following code in your LocalSettings.php 

```php
# wordpress location relative to wiki location
$wgAuthWPRelPath = '../';

# disable new user  registration from mediawiki
$wgGroupPermissions['*']['createaccount'] = false;

# use wordpress auth extension
require_once "$IP/extensions/AuthWP/AuthWP.php";
$wgAuth=new AuthWP();

# Add hook for session management 
# THIS IS DEPRECATED by MediaWiki but works for now 
# instead MediaWiki\Session\SessionProvider should be used
$wgHooks['UserLoadFromSession'][] = 'AuthWPUserLoadFromSession';
$wgHooks['UserLogout'][] = 'AuthWPUserLogout';
```
