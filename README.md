See [the MediaWiki Extension page](https://www.mediawiki.org/wiki/Extension:WPMW) for documentation.

Use the following code in your LocalSettings.php


# wordpress location relative to wiki location
$wgAuthWPRelPath = '../';
# disable new user  registration from mediawiki
$wgGroupPermissions['*']['createaccount'] = false;
# use wordpress auth extension
require_once "$IP/extensions/AuthWP/AuthWP.php";
$wgAuth=new AuthWP();
#DEPRECATED but available for backward compatibility
#Add hook for session management . MediaWiki\Session\SessionProvider should be used instead
$wgHooks['UserLoadFromSession'][] = 'AuthWPUserLoadFromSession';
$wgHooks['UserLogout'][] = 'AuthWPUserLogout';
