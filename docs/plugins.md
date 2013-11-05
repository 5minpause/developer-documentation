# Implementing a plugin
## CLI tool
Piwik comes with a powerful command line tool to help you generating a plugin easily. The command line tool is called "console" and is located in the Piwik root directory.
To get familiar with the command line tool enter either `./console` or `php console`. As you haven't specified any command yet, it will list you all available commands along with their descriptions. 
The most interesting commands for developers are:

* `generate:plugin`
* `generate:theme`
* `generate:api`
* `generate:controller`
* `generate:visualizationplugin`
* `log:watch`
* `tests:run`

To execute a specific command just enter the name of the command as an argument:

`./console log:watch`

Some of the commands require further arguments or options. Use `help` to see which ones are available for a specific command:

`./console help generate:plugin`

Some of the arguments and options are required, whereas other are optional. If you do not specify a value, the command line tool will ask you to enter the missing values. So you do not have to care much about arguments and options. Easy!

### Creating a plugin
Execute the command `./console generate:plugin` in order to create a new plugin. The CLI tool will ask you to enter a name, a description and a version number. This creates a very basic plugin for you including all the necessary files. If you already know that you need a Controller and an API, the console tool can create those for you as well. 

## Building the plugin
### Namespaces
### Defining new widgets
### Defining new menus
### Using the database
#### Create a new table
#### Update schemaf
### Track additional data
### Understanding Hooks
### Understanding Archiving
### How to create an API

Start by using the CLI tool to create the needed files: `./console generate:api`. This script creates a file named `API.php` within your plugin.

Each public method within this class will be accessible over the API. Adding new actions is as easy as creating a new function, accepting any input parameter you need and returning any value.

#### Filename API.php, public/private
#### Getting data from another API
#### Returning data as an array or DataTable
#### Authenticate users
### How to create a Controller

Start by using the CLI tool to create the needed files: `./console generate:controller`. This script creates a file named `Controller.php` within your plugin. The Controller already comes with a default action and template which is located in the `templates` directory.

Each public method within the controller will be accessible over the Piwik UI.

MVC intro, uses of a controller 
#### Useful helpers 
parent:: methods, checkUser* auth helpers, ...
### How to add settings to the plugin
### How to use other APIs
#### API.php: getting data and modifying it
#### Controller.php: getting data and displaying it in a View
#### Controller.php: calling API for admin action
### Defining a new segment
### Make your custom reports visible in Email reports & Piwik Mobile
## Persisting data
#### Hint: Do not create any files in your plugins folder, it will be deleted on update --> use for instance tmp instead
## Templating
### Styling
### Testing
### Scheduled Tasks
### Translating your plugins
## Security
#### Handle user/untrusted input
#### Handling output
### Release in Marketplace
## Limitations