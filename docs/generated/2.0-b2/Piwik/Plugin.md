<small>Piwik</small>

Plugin
======

Base class of all Plugin Descriptor classes.

Description
-----------

Any plugin that wants to add event observers to one of Piwik's [hooks](#), 
or has special installation/uninstallation logic must implement this class.
Plugins that can specify everything they need to in the _plugin.json_ files,
such as themes, don't need to implement this class.

The name of the implementation of this class should be the same name as the
plugin they are a part of (eg, `class UserCountry extends Plugin`).

### Plugin Metadata

In addition to providing a place for plugins to install/uninstall themselves
and add event observers, this class is also responsible for loading metadata
found in the plugin.json file.

The plugin.json file must exist in the root directory of a plugin. It can
contain the following information:

- **description**: An internationalized string description of what the plugin
                   does.
- **homepage**: The URL to the plugin's website.
- **author**: Author name.
- **author_homepage**: The URL to the author's website.
- **license**: The license the code uses (eg, GPL, MIT, etc.).
- **license_homepage**: URL to website describing the license used.
- **version**: The plugin version (eg, 1.0.1).
- **theme**: `true` or `false`. If `true`, the plugin will be treated as a theme.

### Examples

**How to extend**

    use Piwik\Common;
    use Piwik\Plugin;
    use Piwik\Db;

    class MyPlugin extends Plugin
    {
        public function getListHooksRegistered()
        {
            return array(
                'API.getReportMetadata' => 'myPluginFunction',
                'Another.event'         => array(
                                               'function' => 'myOtherPluginFunction',
                                               'after'    => true // execute after callbacks w/o ordering
                                           )
            );
        }

        public function install()
        {
            Db::exec("CREATE TABLE " . Common::prefixTable('mytable') . "...");
        }

        public function uninstall()
        {
            Db::exec("DROP TABLE IF EXISTS " . Common::prefixTable('mytable'));
        }
    }


Methods
-------

The class defines the following methods:

- [`__construct()`](#__construct) &mdash; Constructor.
- [`getInformation()`](#getInformation) &mdash; Returns the plugin details - 'description' => string        // 1-2 sentence description of the plugin - 'author' => string             // plugin author - 'author_homepage' => string    // author homepage URL (or email "mailto:youremail@example.org") - 'homepage' => string           // plugin homepage URL - 'license' => string            // plugin license - 'license_homepage' => string   // license homepage URL - 'version' => string            // plugin version number; examples and 3rd party plugins must not use Version::VERSION; 3rd party plugins must increment the version number with each plugin release - 'theme' => bool                // Whether this plugin is a theme (a theme is a plugin, but a plugin is not necessarily a theme)
- [`getListHooksRegistered()`](#getListHooksRegistered) &mdash; Returns a list of hooks with associated event observers.
- [`postLoad()`](#postLoad) &mdash; This method is executed after a plugin is loaded and translations are registered.
- [`install()`](#install) &mdash; Installs the plugin.
- [`uninstall()`](#uninstall) &mdash; Uninstalls the plugins.
- [`activate()`](#activate) &mdash; Executed every time the plugin is enabled.
- [`deactivate()`](#deactivate) &mdash; Executed every time the plugin is disabled.
- [`getVersion()`](#getVersion) &mdash; Returns the plugin version number.
- [`isTheme()`](#isTheme) &mdash; Returns true if this plugin is a theme, false if otherwise.
- [`getPluginName()`](#getPluginName) &mdash; Returns the plugin's base class name without the namespace, e.g., "UserCountry" when the plugin class is "Piwik\Plugins\UserCountry\UserCountry".
- [`getPluginNameFromBacktrace()`](#getPluginNameFromBacktrace) &mdash; Extracts the plugin name from a backtrace array.

<a name="__construct" id="__construct"></a>
### `__construct()`

Constructor.

#### Signature

- It accepts the following parameter(s):
    - `$pluginName`
- It does not return anything.
- It throws one of the following exceptions:
    - [`Exception`](http://php.net/class.Exception) &mdash; If plugin metadata is defined in both the getInformation() method and the plugin.json file.

<a name="getinformation" id="getinformation"></a>
### `getInformation()`

Returns the plugin details - 'description' => string        // 1-2 sentence description of the plugin - 'author' => string             // plugin author - 'author_homepage' => string    // author homepage URL (or email "mailto:youremail@example.org") - 'homepage' => string           // plugin homepage URL - 'license' => string            // plugin license - 'license_homepage' => string   // license homepage URL - 'version' => string            // plugin version number; examples and 3rd party plugins must not use Version::VERSION; 3rd party plugins must increment the version number with each plugin release - 'theme' => bool                // Whether this plugin is a theme (a theme is a plugin, but a plugin is not necessarily a theme)

#### Signature

- It returns a(n) `array` value.

<a name="getlisthooksregistered" id="getlisthooksregistered"></a>
### `getListHooksRegistered()`

Returns a list of hooks with associated event observers.

#### Signature

- _Returns:_ eg, array( 'API.getReportMetadata' => 'myPluginFunction', 'Another.event'         => array( 'function' => 'myOtherPluginFunction', 'after'    => true // execute after callbacks w/o ordering ) 'Yet.Another.event'     => array( 'function' => 'myOtherPluginFunction', 'before'   => true // execute before callbacks w/o ordering ) )
    - `array`

<a name="postload" id="postload"></a>
### `postLoad()`

This method is executed after a plugin is loaded and translations are registered.

#### Description

Useful for initialization code that uses translated strings from the plugin.

#### Signature

- It does not return anything.

<a name="install" id="install"></a>
### `install()`

Installs the plugin.

#### Description

Derived classes should implement this class if the plugin
needs to:
- create tables
- update existing tables
- etc.

#### Signature

- It does not return anything.
- It throws one of the following exceptions:
    - [`Exception`](http://php.net/class.Exception) &mdash; if installation of fails for some reason.

<a name="uninstall" id="uninstall"></a>
### `uninstall()`

Uninstalls the plugins.

#### Description

Derived classes should implement this class if the changes
made in [install](#install) should be undone during uninstallation.

In most cases, if you have an [install](#install) method, you should provide 
an [uninstall](#uninstall) method.

#### Signature

- It does not return anything.
- It throws one of the following exceptions:
    - [`Exception`](http://php.net/class.Exception) &mdash; if uninstallation of fails for some reason.

<a name="activate" id="activate"></a>
### `activate()`

Executed every time the plugin is enabled.

#### Signature

- It does not return anything.

<a name="deactivate" id="deactivate"></a>
### `deactivate()`

Executed every time the plugin is disabled.

#### Signature

- It does not return anything.

<a name="getversion" id="getversion"></a>
### `getVersion()`

Returns the plugin version number.

#### Signature

- It is a **finalized** method.
- It returns a(n) `string` value.

<a name="istheme" id="istheme"></a>
### `isTheme()`

Returns true if this plugin is a theme, false if otherwise.

#### Signature

- It is a **finalized** method.
- It returns a(n) `bool` value.

<a name="getpluginname" id="getpluginname"></a>
### `getPluginName()`

Returns the plugin's base class name without the namespace, e.g., "UserCountry" when the plugin class is "Piwik\Plugins\UserCountry\UserCountry".

#### Signature

- It is a **finalized** method.
- It returns a(n) `string` value.

<a name="getpluginnamefrombacktrace" id="getpluginnamefrombacktrace"></a>
### `getPluginNameFromBacktrace()`

Extracts the plugin name from a backtrace array.

#### Description

Returns false if we can't find one.

#### Signature

- It accepts the following parameter(s):
    - `$backtrace`
- It can return one of the following values:
    - `string`
    - `Piwik\false`
