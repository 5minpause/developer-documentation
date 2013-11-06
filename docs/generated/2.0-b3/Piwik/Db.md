<small>Piwik</small>

Db
==

Helper class that contains SQL related helper functions.

Description
-----------

Plugins should use this class to execute SQL against the database.

### Examples

**Basic Usage**

    $rows = Db::fetchAll("SELECT col1, col2 FROM mytable WHERE thing = ?", array('thingvalue'));
    foreach ($rows as $row) {
        doSomething($row['col1'], $row['col2']);
    }

    $value = Db::fetchOne("SELECT MAX(col1) FROM mytable");

    Db::query("DELETE FROM mytable WHERE id < ?", array(23));


Properties
----------

This class defines the following properties:

- [`$lockPrivilegeGranted`](#$lockprivilegegranted) &mdash; Cached result of isLockprivilegeGranted function.

<a name="lockprivilegegranted" id="lockprivilegegranted"></a>
### `$lockPrivilegeGranted`

Cached result of isLockprivilegeGranted function.

#### Description

Public so tests can simulate the situation where the lock tables privilege isn't granted.

#### Signature

- It is a(n) `bool` value.

Methods
-------

The class defines the following methods:

- [`get()`](#get) &mdash; Returns the database connection and creates it if it hasn't been already.
- [`createDatabaseObject()`](#createdatabaseobject) &mdash; Create the database object and connects to the database.
- [`exec()`](#exec) &mdash; Executes an unprepared SQL query.
- [`query()`](#query) &mdash; Executes an SQL query and returns the Zend_Db_Statement object.
- [`fetchAll()`](#fetchall) &mdash; Executes the SQL query and fetches all the rows from the result set.
- [`fetchRow()`](#fetchrow) &mdash; Executes an SQL query and fetches the first row of the result.
- [`fetchOne()`](#fetchone) &mdash; Executes an SQL query and fetches the first column of the first row of result set.
- [`fetchAssoc()`](#fetchassoc) &mdash; Executes an SQL query and returns the entire result set indexed by the first selected field.
- [`deleteAllRows()`](#deleteallrows) &mdash; Deletes all desired rows in a table, while using a limit.
- [`optimizeTables()`](#optimizetables) &mdash; Runs an OPTIMIZE TABLE query on the supplied table or tables.
- [`dropTables()`](#droptables) &mdash; Drops the supplied table or tables.
- [`lockTables()`](#locktables) &mdash; Locks the supplied table or tables.
- [`unlockAllTables()`](#unlockalltables) &mdash; Releases all table locks.
- [`segmentedFetchFirst()`](#segmentedfetchfirst) &mdash; Performs a SELECT on a table one chunk at a time and returns the first successfully fetched value.
- [`segmentedFetchOne()`](#segmentedfetchone) &mdash; Performs a SELECT on a table one chunk at a time and returns an array of every fetched value.
- [`segmentedFetchAll()`](#segmentedfetchall) &mdash; Performs a SELECT on a table one chunk at a time and returns an array of every fetched row.
- [`segmentedQuery()`](#segmentedquery) &mdash; Performs a non-SELECT query on a table one chunk at a time.
- [`getDbLock()`](#getdblock) &mdash; Attempts to get a named lock.
- [`releaseDbLock()`](#releasedblock) &mdash; Releases a named lock.
- [`isLockPrivilegeGranted()`](#islockprivilegegranted) &mdash; Checks whether the database user is allowed to lock tables.

<a name="get" id="get"></a>
### `get()`

Returns the database connection and creates it if it hasn't been already.

#### Signature

- It can return one of the following values:
    - `Piwik\Tracker\Db`
    - `Piwik\Db\AdapterInterface`
    - [`Db`](../Piwik/Db.md)

<a name="createdatabaseobject" id="createdatabaseobject"></a>
### `createDatabaseObject()`

Create the database object and connects to the database.

#### Description

Shouldn't be called directly, use [get](#get).

#### Signature

- It accepts the following parameter(s):
    - `$dbInfos`
- It does not return anything.

<a name="exec" id="exec"></a>
### `exec()`

Executes an unprepared SQL query.

#### Description

Recommended for DDL statements like CREATE,
DROP and ALTER. The return value is DBMS-specific. For MySQLI, it returns the
number of rows affected. For PDO, it returns the `Zend_Db_Statement` object.

#### Signature

- It accepts the following parameter(s):
    - `$sql`
- It can return one of the following values:
    - `integer`
    - `Zend_Db_Statement`
- It throws one of the following exceptions:
    - [`Exception`](http://php.net/class.Exception) &mdash; If there is an error in the SQL.

<a name="query" id="query"></a>
### `query()`

Executes an SQL query and returns the Zend_Db_Statement object.

#### Description

If you want to fetch data from the DB you should use one of the fetch... functions.

See also [http://framework.zend.com/manual/en/zend.db.statement.html](http://framework.zend.com/manual/en/zend.db.statement.html).

#### Signature

- It accepts the following parameter(s):
    - `$sql`
    - `$parameters`
- It returns a(n) `Zend_Db_Statement` value.
- It throws one of the following exceptions:
    - [`Exception`](http://php.net/class.Exception) &mdash; If there is a problem with the SQL or bind parameters.

<a name="fetchall" id="fetchall"></a>
### `fetchAll()`

Executes the SQL query and fetches all the rows from the result set.

#### Signature

- It accepts the following parameter(s):
    - `$sql`
    - `$parameters`
- _Returns:_ (one row in the array per row fetched in the DB)
    - `array`
- It throws one of the following exceptions:
    - [`Exception`](http://php.net/class.Exception) &mdash; If there is a problem with the SQL or bind parameters.

<a name="fetchrow" id="fetchrow"></a>
### `fetchRow()`

Executes an SQL query and fetches the first row of the result.

#### Signature

- It accepts the following parameter(s):
    - `$sql`
    - `$parameters`
- It returns a(n) `array` value.
- It throws one of the following exceptions:
    - [`Exception`](http://php.net/class.Exception) &mdash; If there is a problem with the SQL or bind parameters.

<a name="fetchone" id="fetchone"></a>
### `fetchOne()`

Executes an SQL query and fetches the first column of the first row of result set.

#### Signature

- It accepts the following parameter(s):
    - `$sql`
    - `$parameters`
- It returns a(n) `string` value.
- It throws one of the following exceptions:
    - [`Exception`](http://php.net/class.Exception) &mdash; If there is a problem with the SQL or bind parameters.

<a name="fetchassoc" id="fetchassoc"></a>
### `fetchAssoc()`

Executes an SQL query and returns the entire result set indexed by the first selected field.

#### Signature

- It accepts the following parameter(s):
    - `$sql`
    - `$parameters`
- _Returns:_ eg, ``` array('col1value1' => array('col2' => '...', 'col3' => ...), 'col1value2' => array('col2' => '...', 'col3' => ...)) ```
    - `array`
- It throws one of the following exceptions:
    - [`Exception`](http://php.net/class.Exception) &mdash; If there is a problem with the SQL or bind parameters.

<a name="deleteallrows" id="deleteallrows"></a>
### `deleteAllRows()`

Deletes all desired rows in a table, while using a limit.

#### Description

This function will execute many
DELETE queries until there are no more rows to delete.

Use this function when you need to delete many thousands of rows from a table without
locking the table for too long.

**Example**

    $idVisit = // ...
    Db::deleteAllRows(Common::prefixTable('log_visit'), "WHERE idvisit <= ?", "idvisit ASC", 100000, array($idVisit));

#### Signature

- It accepts the following parameter(s):
    - `$table`
    - `$where`
    - `$orderBy`
    - `$maxRowsPerQuery`
    - `$parameters`
- _Returns:_ The total number of rows deleted.
    - `int`

<a name="optimizetables" id="optimizetables"></a>
### `optimizeTables()`

Runs an OPTIMIZE TABLE query on the supplied table or tables.

#### Description

The table names must be prefixed
(see [Common::prefixTable](#)).

Tables will only be optimized if the `[General] enable_sql_optimize_queries` config option is
set to **1**.

#### Signature

- It accepts the following parameter(s):
    - `$tables`
- It returns a(n) `Zend_Db_Statement` value.

<a name="droptables" id="droptables"></a>
### `dropTables()`

Drops the supplied table or tables.

#### Description

The table names must be prefixed (see [Common::prefixTable](#)).

#### Signature

- It accepts the following parameter(s):
    - `$tables`
- It returns a(n) `Zend_Db_Statement` value.

<a name="locktables" id="locktables"></a>
### `lockTables()`

Locks the supplied table or tables.

#### Description

The table names must be prefixed (see [Common::prefixTable](#)).

**NOTE:** Piwik does not require the LOCK TABLES privilege to be available. Piwik
should still work in case it is not granted.

#### Signature

- It accepts the following parameter(s):
    - `$tablesToRead`
    - `$tablesToWrite`
- It returns a(n) `Zend_Db_Statement` value.

<a name="unlockalltables" id="unlockalltables"></a>
### `unlockAllTables()`

Releases all table locks.

#### Description

**NOTE:** Piwik does not require the LOCK TABLES privilege to be available. Piwik
should still work in case it is not granted.

#### Signature

- It returns a(n) `Zend_Db_Statement` value.

<a name="segmentedfetchfirst" id="segmentedfetchfirst"></a>
### `segmentedFetchFirst()`

Performs a SELECT on a table one chunk at a time and returns the first successfully fetched value.

#### Description

In other words, if running a SELECT on one chunk of the table doesn't
return a value, we move on to the next chunk and we keep moving until
the SELECT returns a value.

This function will break up a SELECT into several smaller SELECTs and
should be used when performing a SELECT that can take a long time to finish.
Using several smaller SELECTs will ensure that the table will not be locked
for too long.

**Example**

    // find the most recent visit that is older than a certain date 
    $dateStart = // ...
    $sql = "SELECT idvisit
          FROM $logVisit
         WHERE '$dateStart' > visit_last_action_time
           AND idvisit <= ?
           AND idvisit > ?
      ORDER BY idvisit DESC
         LIMIT 1";

    // since visits
    return Db::segmentedFetchFirst($sql, $maxIdVisit, 0, -self::$selectSegmentSize);

#### Signature

- It accepts the following parameter(s):
    - `$sql`
    - `$first`
    - `$last`
    - `$step`
    - `$params`
- It returns a(n) `string` value.

<a name="segmentedfetchone" id="segmentedfetchone"></a>
### `segmentedFetchOne()`

Performs a SELECT on a table one chunk at a time and returns an array of every fetched value.

#### Description

This function will break up a SELECT into several smaller SELECTs and
accumulate the result. It should be used when performing a SELECT that can
take a long time to finish. Using several smaller SELECTs will ensure that
the table will not be locked for too long.

#### Signature

- It accepts the following parameter(s):
    - `$sql`
    - `$first`
    - `$last`
    - `$step`
    - `$params`
- _Returns:_ An array of primitive values.
    - `array`

<a name="segmentedfetchall" id="segmentedfetchall"></a>
### `segmentedFetchAll()`

Performs a SELECT on a table one chunk at a time and returns an array of every fetched row.

#### Description

This function will break up a SELECT into several smaller SELECTs and
accumulate the result. It should be used when performing a SELECT that can
take a long time to finish. Using several smaller SELECTs will ensure that
the table will not be locked for too long.

#### Signature

- It accepts the following parameter(s):
    - `$sql`
    - `$first`
    - `$last`
    - `$step`
    - `$params`
- _Returns:_ An array of rows that includes the result set of every executed query.
    - `array`

<a name="segmentedquery" id="segmentedquery"></a>
### `segmentedQuery()`

Performs a non-SELECT query on a table one chunk at a time.

#### Signature

- It accepts the following parameter(s):
    - `$sql`
    - `$first`
    - `$last`
    - `$step`
    - `$params`
- It does not return anything.

<a name="getdblock" id="getdblock"></a>
### `getDbLock()`

Attempts to get a named lock.

#### Description

This function uses a timeout of 1s, but will
retry a set number of time.

#### Signature

- It accepts the following parameter(s):
    - `$lockName`
    - `$maxRetries`
- _Returns:_ `true` if the lock was obtained, `false` if otherwise.
    - `bool`

<a name="releasedblock" id="releasedblock"></a>
### `releaseDbLock()`

Releases a named lock.

#### Signature

- It accepts the following parameter(s):
    - `$lockName`
- _Returns:_ `true` if the lock was released, `false` if otherwise.
    - `bool`

<a name="islockprivilegegranted" id="islockprivilegegranted"></a>
### `isLockPrivilegeGranted()`

Checks whether the database user is allowed to lock tables.

#### Signature

- It returns a(n) `bool` value.
