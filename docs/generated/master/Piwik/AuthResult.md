<small>Piwik\</small>

AuthResult
==========

Authentication result.

This is what is returned by authentication attempts using [Auth](/api-reference/Piwik/Auth)
implementations.

Methods
-------

The class defines the following methods:

- [`__construct()`](#__construct) &mdash; Constructor for AuthResult
- [`getIdentity()`](#getidentity) &mdash; Returns the login used to authenticate.
- [`getTokenAuth()`](#gettokenauth) &mdash; Returns the token_auth to authenticate the current user in the API
- [`getCode()`](#getcode) &mdash; Returns the authentication result code.
- [`hasSuperUserAccess()`](#hassuperuseraccess) &mdash; Returns true if the user has Super User access, false otherwise.
- [`wasAuthenticationSuccessful()`](#wasauthenticationsuccessful) &mdash; Returns true if this result was successfully authentication.

<a name="__construct" id="__construct"></a>
<a name="__construct" id="__construct"></a>
### `__construct()`

Constructor for AuthResult

#### Signature

-  It accepts the following parameter(s):

   <ul>
   <li>
      <div markdown="1" class="parameter">
      `$code` (`int`) &mdash;

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$login` (`string`) &mdash;

      <div markdown="1" class="param-desc"> identity</div>

      <div style="clear:both;"/>

      </div>
   </li>
   <li>
      <div markdown="1" class="parameter">
      `$tokenAuth` (`string`) &mdash;

      <div markdown="1" class="param-desc"></div>

      <div style="clear:both;"/>

      </div>
   </li>
   </ul>

<a name="getidentity" id="getidentity"></a>
<a name="getIdentity" id="getIdentity"></a>
### `getIdentity()`

Returns the login used to authenticate.

#### Signature

- It returns a `string` value.

<a name="gettokenauth" id="gettokenauth"></a>
<a name="getTokenAuth" id="getTokenAuth"></a>
### `getTokenAuth()`

Returns the token_auth to authenticate the current user in the API

#### Signature

- It returns a `string` value.

<a name="getcode" id="getcode"></a>
<a name="getCode" id="getCode"></a>
### `getCode()`

Returns the authentication result code.

#### Signature

- It returns a `int` value.

<a name="hassuperuseraccess" id="hassuperuseraccess"></a>
<a name="hasSuperUserAccess" id="hasSuperUserAccess"></a>
### `hasSuperUserAccess()`

Returns true if the user has Super User access, false otherwise.

#### Signature

- It returns a `bool` value.

<a name="wasauthenticationsuccessful" id="wasauthenticationsuccessful"></a>
<a name="wasAuthenticationSuccessful" id="wasAuthenticationSuccessful"></a>
### `wasAuthenticationSuccessful()`

Returns true if this result was successfully authentication.

#### Signature

- It returns a `bool` value.

