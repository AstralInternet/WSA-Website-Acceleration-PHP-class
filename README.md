# Website Acceleration PHP class

A PHP class to easilly manage the different aspect of dealing with the WSA caching engine.

_Note: Since the WSA update to 1.1.X, the administrator may hide the WSA caching header in the HTML page. Therefore, the function to verify is WSA is installed will now return an integer instead of a Boolean. A value of 0 for the module not being installed will be return and help keep backward compatibility. Added value of 1, 2 or 3 will be return depending on the information found in the page header. See the function detail for more information._

## Getting Started

This class can be freely integrated into any PHP project. A Wordpress plugin currently exist for purging the WSA cache and uses this class in it's backend.

### Prerequisites

In order for this class to be usefull, the server hosting the website need to have the Website Accelerator (WSA) module developed by Astral Internet inc.

## Coding

The class can easilly be intergrated into any project, simply included the class to use it's functions.

```php
include "wsa.class.php";

// Purge the cache for the current domain.
if (WSAHandler\WSA::is_module_installed()) {
    WSAHandler\WSA::purge_cache();
}

// Purge the cache for all the user domains.
if (WSAHandler\WSA::is_module_installed()) {
    WSAHandler\WSA::purge_cache(true);
}
```
### Functions

#### is_module_installed

Function that will try to determine if the WSA module is currently installed inside the server. 
It will return one of the following choices :
0 - not installed
1 - installed
2 - could be installed (needed since WSA 1.1)
3 - could be installed, behind CloudFlare proxy (needed since WSA 1.1)

#### purge_cache

Function that will write the file being check by the WSA deamon in order to initiate the cache purging procedure in the server. 

The function will return true if it manage to write the file. 

**Argument:** 

- *$p_purgeAll:* Set to true if you want to empty the cache for all domains that belong to the user, otherwise the class will try to empty the cache for the domain in use only.
- *$p_fullPath:* Allow you to override the default ".wsa" folder. If for some reason the class cannot find the path, it can be manually specified.

## Authors

* **Daniel Berthiaume** - *Initial work* - [Astral Internet inc.](https://github.com/AstralInternet)
* **Nicholas Brun** - *Initial work* - [Astral Internet inc.](https://github.com/AstralInternet)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the [GNU General Public License, version 3]([LICENSE.md](https://www.gnu.org/licenses/gpl-3.0.html)) for details.
