<small>Piwik\Menu\</small>

MenuAbstract
============

Base class for classes that manage one of Piwik's menus.

There are three menus in Piwik, the main menu, the top menu and the admin menu.
Each menu has a class that manages the menu's content. Each class invokes
a different event to allow plugins to add new menu items.

Methods
-------

The abstract class defines the following methods:

- [`getInstance()`](#getinstance) &mdash; Returns the singleton instance for the derived class. Inherited from [`Singleton`](../../Piwik/Singleton.md)
- [`addItem()`](#additem) &mdash; Adds a new entry to the menu.
- [`remove()`](#remove) &mdash; Removes an existing entry from the menu.
- [`rename()`](#rename) &mdash; Renames a single menu entry.
- [`editUrl()`](#editurl) &mdash; Edits a URL of an existing menu entry.

<a name="getinstance" id="getinstance"></a>
<a name="getInstance" id="getInstance"></a>
### `getInstance()`

Returns the singleton instance for the derived class.

If the singleton instance
has not been created, this method will create it.

#### Signature

- It returns a [`Singleton`](../../Piwik/Singleton.md) value.

<a name="additem" id="additem"></a>
<a name="addItem" id="addItem"></a>
### `addItem()`

Since Piwik 2.7.0

Adds a new entry to the menu.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$menuName` (`string`) &mdash;

      <div markdown="1" class="param-desc"> The menu's category name. Can be a translation token.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$subMenuName` (`string`) &mdash;

      <div markdown="1" class="param-desc"> The menu item's name. Can be a translation token.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$url` (`string`|`array`) &mdash;

      <div markdown="1" class="param-desc"> The URL the admin menu entry should link to, or an array of query parameters that can be used to build the URL.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$order` (`int`) &mdash;

      <div markdown="1" class="param-desc"> The order hint.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$tooltip` (`bool`|`string`) &mdash;

      <div markdown="1" class="param-desc"> An optional tooltip to display or false to display the tooltip.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It does not return anything.

<a name="remove" id="remove"></a>
<a name="remove" id="remove"></a>
### `remove()`

Removes an existing entry from the menu.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$menuName` (`string`) &mdash;

      <div markdown="1" class="param-desc"> The menu's category name. Can be a translation token.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$subMenuName` (`bool`|`string`) &mdash;

      <div markdown="1" class="param-desc"> The menu item's name. Can be a translation token.</div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It does not return anything.

<a name="rename" id="rename"></a>
<a name="rename" id="rename"></a>
### `rename()`

Renames a single menu entry.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$mainMenuOriginal` (`Piwik\Menu\$mainMenuOriginal`) &mdash;

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$subMenuOriginal` (`Piwik\Menu\$subMenuOriginal`) &mdash;

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$mainMenuRenamed` (`Piwik\Menu\$mainMenuRenamed`) &mdash;

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$subMenuRenamed` (`Piwik\Menu\$subMenuRenamed`) &mdash;

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It does not return anything.

<a name="editurl" id="editurl"></a>
<a name="editUrl" id="editUrl"></a>
### `editUrl()`

Edits a URL of an existing menu entry.

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$mainMenuToEdit` (`Piwik\Menu\$mainMenuToEdit`) &mdash;

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$subMenuToEdit` (`Piwik\Menu\$subMenuToEdit`) &mdash;

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$newUrl` (`Piwik\Menu\$newUrl`) &mdash;

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>
- It does not return anything.

