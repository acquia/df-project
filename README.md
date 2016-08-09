This is a Composer-based installer for the [Demo Framework](https://www.drupal.org/project/df) Drupal distribution.

## Get Started
You will need the following installed:

* [Composer](https://getcomposer.org)

When you have those, run this command:
```
$ composer create-project acquia/df-project:^8.1.0 MY_PROJECT --no-interaction
```
Composer will create a new directory called MY_PROJECT containing a ```docroot``` directory with a full Demo Framework code base therein. You can then install it like you would any other Drupal site.

## Maintenance
Your Demo Framework project can be maintained using a combination of Composer and Drush.

Let this handy table be your guide:

| Task                                            | Drush                                         | Composer                                          |
|-------------------------------------------------|-----------------------------------------------|---------------------------------------------------|
| Installing a contrib project (latest version)   | ```drush pm-download PROJECT```               | ```composer require drupal/PROJECT:8.*```         |
| Installing a contrib project (specific version) | ```drush pm-download PROJECT-8.x-1.0-beta3``` | ```composer require drupal/PROJECT:8.1.0-beta3``` |
| Updating all contrib projects and Drupal core   | ```drush pm-update```                         | ```composer update```                             |
| Updating a single contrib project               | ```drush pm-update PROJECT```                 | ```composer update drupal/PROJECT```              |
| Updating Drupal core                            | ```drush pm-update drupal```                  | ```composer update drupal/core```                 |

The installer will install a copy of Drush (local to the project) in the ```bin``` directory.

## Source Control
If you peek at the ```.gitignore``` we provide, you'll see that certain directories, including all directories containing contributed projects, are excluded from source control. In a Composer-based project like this one, **you SHOULD NOT commit your installed dependencies to source control**.

When you set up the project, Composer will create a file called ```composer.lock```, which is a list of which dependencies were installed, and in which versions. **Commit ```composer.lock``` to source control!** Then, when your colleagues want to spin up their own copies of the project, all they'll have to do is run ```composer install```, which will install the correct versions of everything in ```composer.lock```.

