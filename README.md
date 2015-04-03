CKFinder 3 - Sample Plugins
===========================

This folder contains example plugins for CKFinder 3. 

To learn about writing own plugins, read the [Creating Plugins](http://docs.cksource.com/ckfinder3/#!/guide/dev_plugins) article in CKFinder 3 documentation.

Loading plugins
---------------

To run the sample plugins:

1. Download the sample plugins and extract them to `<ckfinder>/plugins` folder. You can download plugins:
 - using `git`,
 - by pressing the [Download ZIP](https://github.com/ckfinder/ckfinder-docs-samples/archive/master.zip) button.
2. Enable selected plugins with [config.plugins](http://docs.cksource.com/ckfinder3/#!/api/CKFinder.Config-cfg-plugins)

#### Example

```js
<script>
	CKFinder.widget( 'ckfinder-widget', {
		width: 800,
		height: 700,
		plugins: [
			'StatusBarInfo'
		]
	} );
</script>
```

Note: as it's possible in CKFinder 3 to load plugins from URL, you can point your CKFinder straight to the plugin on GitHub!

```js
<script>
	CKFinder.widget( 'ckfinder-widget', {
		width: 800,
		height: 700,
		plugins: [
			'https://raw.githubusercontent.com/ckfinder/ckfinder-docs-samples/master/StatusBarInfo/StatusBarInfo.js'
		]
	} );
</script>
```

Plugins list
------------

### ACLInfo

Plugin that displays folder's ACL data in the folders tree panel.

It illustrates how to modify templates used by CKFinder to render various parts of the application.

### AlterCommand

A simple plugin that illustrates how to alter commands sent to the server connector.

### AlterDialogWindow

Sample plugin that alters "Rename File" dialog view.

This plugin illustrates how to:

* Alter existing dialog windows by overriding the default templates.
* Read values from input elements in dialog windows.
* Listen to dialog events (e.g. to execute code when "Ok" button is pressed).
* Alter executed command to send additional data to the server side connector.

### CustomButton

Plugin that illustrates how to:

* Add a custom icon that can be used by a context menu item or a toolbar button.
* Add a context menu item.
* Add a toolbar button.

### FolderInfo

Sample plugin which displays folder information in the files pane.

This plugin illustrates how to:

* Localize plugin by providing language files.
* Render custom HTML content inside the application by providing own region and showing custom view in this region.

### SettingsDemo

Plugin that adds all possible types of settings to the Settings Panel.

### StatusBarInfo

This plugin illustrates how to show, style and add information to the Status Bar.

Creating plugins
----------------

* Each plugin inside `/plugins` folder must be placed in folder which name is equal to plugin name in which there must be a file named after plugin.
  * For instance plugin `MyPlugin` must be placed inside `plugins/MyPlugin/MyPlugin.js` file.
* If plugin is intended to be loaded from different location above rule does not apply but is considered a good practice.
* Plugins must be properly loaded by require.js AMD loader.
* Inside plugins folder other folders or files may exist, for instance plugin might be divided to AMD modules.

Template file for plugin:
-------------------------

```js

	CKFinder.define( function () {

		var MyPlugin = {
			init: function ( finder ) {
				// plugin initialization code, ie:
				finder.on( 'some:event', function ( evt ) {
					// Do something useful
				} );
			}
		};

		return MyPlugin;
	} );

```

License
-------
For license details see: [LICENSE.md](https://github.com/ckfinder/ckfinder-docs-samples/blob/master/LICENSE.md).
