localize-mainmenu
=================

Command line tool that localizes the common main menu items of an OS X app automatically.


# Problem

Localizing Apps for OS X requires to also localize the main menu. It include a bunch of items that are common throughout all OS X apps (like ``Copy``, ``Paste`` and so forth). Unfortunately Apple does not automatically provide localizations for those keys after adding a new langange. So either you or your translators need to take care of it. 

# Solution
Let this small command line tool take care of the common menu items for you. So neither you nor your translators need to bother localizing them. Furthermore the localization is based on Apple's build-in apps. This means you do not need to worry about to have the exact same variation. 


## Install

``[sudo] npm install localize-mainmenu -g``


## How it works 


1. Add a new language in XCode.

2. Export a xliff file.
	1. Select your project file in the project navigator.
	2. [Main Menu] Editor > Export for Localization… 
	
3. Run **localize-mainmenu** from your comman line.
	
	``$ cd /path/to/your/export``
	
	``$ localize-mainmenu de.xliff de_menu_done.xliff``
	
4. Send the output file ``de_menu_done.xliff`` to you translator(s) *to get the actual important stuff localized*.
5. Import the xliff file back in 
	1. Select your project file in the project navigator.
	2. [Main Menu] Editor > Import Localizations… 
	

## Requirements

- XCode 6 *(or higher)*
- [Node.js](http://nodejs.org)


## Contribution

Feel free to contribute, especially by adding more languages. **Make sure the localization matches Apple's strings so that the Apps won't feel alien.**

Please fork the repo and create a pull request when you are done. 

### Workflow for adding new langauges

1. Make copy of ``languages/_template.json`` and name it using the two lowercase language code. (e.g. ``de.json``).
2. Fill out the new language json file.
	- Running  ``node generate_search_translations_commands.js`` will generate command line commands for each existing language to look for tokens within your installed apps.
	- Here’s a [Map of Standard Internationalised OS X Application Menu Strings to Menu Locations](https://source.ind.ie/project/map-of-standard-internationalised-os-x-application-menu-strings-to-menu-locations/tree/master) if you’d like to base your translations off of Apple’s ones from Pages manually and you don’t want to hunt for their locations.
	- The [App Language Chooser](https://itunes.apple.com/de/app/app-language-chooser/id451732904?mt=12) allows you to start any app (prefer Apple's like Pages) an a language of your choice. This comes in handy to check how Apple translated particular menu items.  
	- As [@catlan](https://github.com/catlan) pointed out in [Issue #1](/../../issues/1) there is a collection of translated menu nib files.
3. Run ``node validate_language_files.js`` to validate whether all languages are formatted in correct json and check the token token quantity of all files.
4. Commit new langauge files one by one.
 
 
## Miscellaneous

- [Here is a short list of XLIFF capable editors](https://gist.github.com/maremmle/8597b27bb52baf00f1ef) I started. Feel free to contribute or hint to an existing collection. 

