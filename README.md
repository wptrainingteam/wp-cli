# WP CLI

## Description

In this lesson, you'll learn how to use the WP CLI, what they are, when you should use them and how it helps you in your WordPress development.

## Objectives

After completing this lesson, you will be able to:

* Install the WordPress using the Commands.
* You can easily mentioned the WordPress version during the installation.
* Installing Themes and Plugins using commands. 
* Activating Theme and Plugins.
* Create backups and setup the WordPress in few minutes.

## Target Audience

Who is this lesson intended for? What interests/skills would they bring? Choose all that apply.

* [ ] Users
* [ ] Designers
* [X] Developers
* [ ] Speakers
* [ ] All

## Experience Level

How much experience would a participant need to get the most from this lesson?

* [x] Beginner
* [x] Intermediate
* [x] Advanced
* [x] Any

## Type of Instruction

Which strategies will be used for this lesson plan? Choose all that apply.

* [X] Demonstration
* [ ] Discussion
* [X] Exercises
* [ ] Feedback
* [x] Lecture (Presentation)
* [x] Show & Tell
* [ ] Tutorial


## Prerequisite Requirements


Before installing WP-CLI, please make sure the  environment meets the minimum requirements:

1. UNIX-like environment (OS X, Linux, FreeBSD, Cygwin); limited support in Windows environment.

2. PHP 5.4 or later

3. WordPress 3.7 or later. Versions older than the latest WordPress release may have degraded functionality


Note that, SSH access is mandatory to use WP CLI commands in order to use in Hosting server. Before using it check whether the WP CLI is installed at your hosting server or machine. 

## What is WP CLI

WP-CLI is the official command line tool which allows to manage WordPress web sites from the command prompt. Updates can be performed, backups can be generated, new posts can be published and most of the admin actions can be performed with a set of commands.

WP command line interface use to complete admin tasks like upgrades, database backup creation, plugins and themes installations and removals, publishing and deleting posts, changing site's URL settings and getting help on chosen commands.

## Assets

* Setup to install and run WordPress [ PHP, MySQL ]

## Before Start :

* Are you familiar with the WordPress and installation process of it?
* Are you familiar with the Command Line Interface commands, like DOS and Linux ? 

## Teacher Notes

* **Time Estimate:** 45 minutes

## Table Of Content

* WP CLI Installation.
* Download and Install WordPress using WP CLI.
* Working with Themes using WP CLI.
* Working with Plugins using WP CLI.
* Setting Permalinks using WP CLI.
* Working with Database using WP CLI.
* Explaining Automated Installation Process using WP CLI.

### WP CLI Installation.

First to check whether WP CLI is install with you or not, 
How to check : 
wp --version [ It will show the wp cli version installed ] 

If Prerequisite Requirements are satisfied, please follow the steps : 
  
```
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar // download the wpcli phar
php wp-cli.phar --info // check whether the phar file is working  
chmod +x wp-cli.phar   // change permission of phar file to access from anywhere
sudo mv wp-cli.phar /usr/local/bin/wp // move to global folder
wp --info  //to check the installation

```
Now WP CLI installed and ready to use for further purposes. 

### Download and Install WordPress using WP CLI.

To start further proceeding with the WP CLI, first we need to create the installation folder in the root directory of Web Server. 

Assuming that Apache WebServer installed : 

```
cd /var/www/html
mkdir firstinstallation
cd firstinstallation
```

Now we are inside the project folder where we are going to install WordPress using WP CLI commands. 

* Downloading WordPress with and without mentioning the specific versions, using anyone of it will download the WordPress. 
```
wp core download
wp core download --version=4.5.1
```
* Now we need to create the wp-config.php file through the command, here following setting values will varies : 

1.  DataBase Name : <databasename> good to set same as project name
2.  DataBase UserName : <username> 
3.  DataBase Password : <password> 
4.  DataBase HostName : <hostname> 

```
wp core config --dbname=<databasename> --dbuser=<username> --dbpass=<password> --dbhost=<hostname> 
```
wp-config file is generated, success message will be shown in your command line screen

* Creating DataBase for your Installation, assuming no database in same name is not pre-exists

```
wp db create 
```
DataBase will be created successfully and message will be shown. 

* Now the installation process need to run, here few settings will varies 

1. URL : Project URL i.e http://localhost/firstinstallation
2. Title : Project Title, set it with folder name or project name i.e firstinstallation
3. Admin User : anything except admin [ Recommended ]
4. Admin Password : anything except admin [ Recommended ]
4. Admin Email : any email as admin email

```
wp core install --url="http://localhost/firstinstallation" --title="firstinstallation" --admin_user="<admin_username>" --admin_password="<admin_password>" --admin_email="<admin_email>"
```

* It will install the WordPress in given url and activate the default theme like TwentyNineteen or else. 


### Working with Themes using WP CLI.

* To Install and Activate any theme from wordpress.org. Astra is a popular theme available in wordpress.org. Just use the Slug or Theme Name to install. Internet connection is mandatory to get the new theme.

``` 
wp theme install astra // it will install the theme from wordpress.org
wp theme install astra --activate //it will install the theme and activate it
wp theme activate twentynineteen // activate the existing theme
```

* To delete the theme from your project. It will not delete activated theme.

```
wp theme delete astra // it will delete the theme 
wp theme delete twentynineteen //Can't delete the currently active theme
```


### Working with Plugins using WP CLI.

* WP CLI can install & activate any available plugins in wordpress.org. Also can activate any existing plugins. It works with the plugin slug [ contact-form-7 / wordpress-importer ]. Internet connection is mandatory to get the new plugins.

```
wp plugin install contact-form-7 // it will install the plugin
wp plugin install contact-form-7  --activate // it will install & activate the plugin

``` 

* Deactivate and Delete the existing plugins 

```
wp plugin deactivate contact-form-7 // it will deactivate the existing plugin
wp plugin delete contact-form-7 //it will deactivate and delete the existing plugin
```

### Setting Permalinks using WP CLI.

* WP CLI can be use to set the permalink structure as per the need, .htaccess file should have the writable permission. 

```
wp rewrite structure '/%postname%/' // write permalink to post name
wp rewrite flush --hard // To clear cache after setting up the site
```

### Working with Database using WP CLI.

* Here we have already learned to create the DataBase, WP CLI can be use to do few more with the DataBase. 

* To create and drop the database.
```
wp db create // it will create database, name mentioned in wp-config.php 
wp db drop --yes //it will drop the existing database 
```

* Export the existing database into the file 

```
wp db export db_exported.txt // it will export the full db to a file named db_exported.txt
```

* Import DataBase from a existing file 
```
wp db import db_exported.txt //it will import the db from already exported file.
```

#### Summary

* WP CLI is most wonderful and smooth way to installing the WordPress using the Command Line Interface. It will very helpful in deployment from any repository to SSH enabled server. 

#### Exercises

* Try to create a set of Command in a Script [ Probably Shell Script, which will run all the above process to install by asking inputs from the users ]

Please clone or download the repo and try it out : https://github.com/trisghosh/wordpress-automated-script.  


#### References 

1. https://wp-cli.org/
2. https://github.com/trisghosh/wordpress-automated-script  
3. https://make.wordpress.org/cli/handbook/installing/
