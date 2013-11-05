<small>Piwik\ViewDataTable</small>

Factory
=======

This class is used to load (from the API) and customize the output of a given DataTable.

Description
-----------

The build() method will create an object implementing ViewInterface
You can customize the dataTable using the disable* methods.

Example:
In the Controller of the plugin VisitorInterest
<pre>
 function getNumberOfVisitsPerVisitDuration( $fetch = false)
 {
     $view = ViewDataTable/Factory::build( 'cloud', 'VisitorInterest.getNumberOfVisitsPerVisitDuration' );
     $view->config->show_search = true;
     $view->render();
 }
</pre>


Methods
-------

The class defines the following methods:

- [`build()`](#build) &mdash; Returns a Piwik_ViewDataTable_* object.
- [`renderReport()`](#renderReport) &mdash; Convenience method that creates and renders a ViewDataTable for a API method.

<a name="build" id="build"></a>
### `build()`

Returns a Piwik_ViewDataTable_* object.

#### Description

By default it will return a ViewDataTable_Html
If there is a viewDataTable parameter in the URL, a ViewDataTable of this 'viewDataTable' type will be returned.
If defaultType is specified and if there is no 'viewDataTable' in the URL, a ViewDataTable of this $defaultType will be returned.
If force is set to true, a ViewDataTable of the $defaultType will be returned in all cases.

#### Signature

- It accepts the following parameter(s):
    - `$defaultType`
    - `$apiAction`
    - `$controllerAction`
    - `$forceDefault`
- It can return one of the following values:
    - [`ViewDataTable`](../../Piwik/Plugin/ViewDataTable.md)
    - [`Visualization`](../../Piwik/Plugin/Visualization.md)
    - `Piwik\Plugins\CoreVisualizations\Visualizations\Sparkline;`
- It throws one of the following exceptions:
    - [`Exception`](http://php.net/class.Exception)

<a name="renderreport" id="renderreport"></a>
### `renderReport()`

Convenience method that creates and renders a ViewDataTable for a API method.

#### Signature

- It accepts the following parameter(s):
    - `$pluginName`
    - `$apiAction`
    - `$fetch`
- _Returns:_ See $fetch.
    - `string`
    - `null`
- It throws one of the following exceptions:
    - [`Exception`](http://php.net/class.Exception)
