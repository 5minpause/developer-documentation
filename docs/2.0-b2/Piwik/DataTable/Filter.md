<small>Piwik\DataTable</small>

Filter
======

A filter is set of logic that manipulates a DataTable.

Description
-----------

Existing filters do things like,

- remove rows
- change column values (change string to lowercase, truncate, etc.)
- add/remove columns or metadata (compute percentage values, add an &#039;icon&#039; metadata based on the label, etc.)
- add/remove/edit subtable associated with rows
- etc.

Filters are called with a DataTable instance and extra parameters that are specified
in [DataTable::filter()](#) and [DataTable::queueFilter()](#).

To see examples of Filters look at the existing ones in the Piwik\DataTable\Filter
namespace.


Methods
-------

The abstract class defines the following methods:

- [`__construct()`](#__construct) &mdash; Constructor.
- [`filter()`](#filter) &mdash; Filters the supplied DataTable.
- [`enableRecursive()`](#enableRecursive) &mdash; Enables/Disables recursive filtering.
- [`filterSubTable()`](#filterSubTable) &mdash; Filters a row&#039;s subtable, if one exists and is loaded in memory.

### `__construct()` <a name="__construct"></a>

Constructor.

#### Signature

- It is a **public** method.
- It accepts the following parameter(s):
    - `$table` ([`DataTable`](../../Piwik/DataTable.md))
- It does not return anything.

### `filter()` <a name="filter"></a>

Filters the supplied DataTable.

#### Signature

- It is a **public abstract** method.
- It accepts the following parameter(s):
    - `$table`
- It does not return anything.

### `enableRecursive()` <a name="enableRecursive"></a>

Enables/Disables recursive filtering.

#### Description

Whether this property is actually used
is up to the derived Filter class.

#### Signature

- It is a **public** method.
- It accepts the following parameter(s):
    - `$enable`
- It does not return anything.

### `filterSubTable()` <a name="filterSubTable"></a>

Filters a row&#039;s subtable, if one exists and is loaded in memory.

#### Signature

- It is a **public** method.
- It accepts the following parameter(s):
    - `$row` ([`Row`](../../Piwik/DataTable/Row.md))
- It does not return anything.
