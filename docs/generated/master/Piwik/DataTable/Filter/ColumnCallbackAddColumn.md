<small>Piwik\DataTable\Filter\</small>

ColumnCallbackAddColumn
=======================

Adds a new column to every row of a DataTable based on the result of callback.

**Basic usage example**

    $callback = function ($visits, $timeSpent) {
        return round($timeSpent / $visits, 2);
    };

    $dataTable->filter('ColumnCallbackAddColumn', array(array('nb_visits', 'sum_time_spent'), 'avg_time_on_site', $callback));

Methods
-------

The class defines the following methods:

- [`__construct()`](#__construct) &mdash; Constructor.
- [`filter()`](#filter) &mdash; See [ColumnCallbackAddColumn](/api-reference/Piwik/DataTable/Filter/ColumnCallbackAddColumn).
- [`enableRecursive()`](#enablerecursive) &mdash; Enables/Disables recursive filtering. Inherited from [`BaseFilter`](../../../Piwik/DataTable/BaseFilter.md)
- [`filterSubTable()`](#filtersubtable) &mdash; Filters a row's subtable, if one exists and is loaded in memory. Inherited from [`BaseFilter`](../../../Piwik/DataTable/BaseFilter.md)

<a name="__construct" id="__construct"></a>
<a name="__construct" id="__construct"></a>
### `__construct()`

Constructor.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$table` ([`DataTable`](../../../Piwik/DataTable.md)) &mdash;

      <div markdown="1" class="param-desc"> The DataTable that will be filtered.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$columns` (`array`|`string`) &mdash;

      <div markdown="1" class="param-desc"> The names of the columns to pass to the callback.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$columnToAdd` (`string`) &mdash;

      <div markdown="1" class="param-desc"> The name of the column to add.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$functionToApply` (`callable`) &mdash;

      <div markdown="1" class="param-desc"> The callback to apply to each row of a DataTable. The columns specified in `$columns` are passed to this callback.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$functionParameters` (`array`) &mdash;

      <div markdown="1" class="param-desc"> deprecated - use an [anonymous function](http://php.net/manual/en/functions.anonymous.php) instead.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>

<a name="filter" id="filter"></a>
<a name="filter" id="filter"></a>
### `filter()`

See [ColumnCallbackAddColumn](/api-reference/Piwik/DataTable/Filter/ColumnCallbackAddColumn).

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$table` ([`DataTable`](../../../Piwik/DataTable.md)) &mdash;

      <div markdown="1" class="param-desc"> The table to filter.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It does not return anything.

<a name="enablerecursive" id="enablerecursive"></a>
<a name="enableRecursive" id="enableRecursive"></a>
### `enableRecursive()`

Enables/Disables recursive filtering.

Whether this property is actually used
is up to the derived BaseFilter class.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$enable` (`bool`) &mdash;

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It does not return anything.

<a name="filtersubtable" id="filtersubtable"></a>
<a name="filterSubTable" id="filterSubTable"></a>
### `filterSubTable()`

Filters a row's subtable, if one exists and is loaded in memory.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$row` ([`Row`](../../../Piwik/DataTable/Row.md)) &mdash;

      <div markdown="1" class="param-desc"> The row whose subtable should be filter.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It does not return anything.

