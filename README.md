# underscore.nested

Nested and delegating object-graph extensions for [Underscore.js][underscore].


## Usage

For usage in [node.js][node], install it via [npm][npm]: `npm install underscore.nested`.

Once Then mix it into Underscore:

```js
var _ = require('underscore');
_.mixin require('underscore.nested');
```


## API

### Options

Many accessor functions take an options object with common fields. The sub-object delegation options
(`getter`, `setter`, and `deleter`) are used to specify where to look for the specific accessor method 
on a custom sub-object when performing that operation. (Functions that do not use that operation will ignore
these options, so you're welcome to specify them everywhere just to be safe.)

<table>
    <thead>
        <tr>
            <th>
                name
            </th>
            <th>
                type
            </th>
            <th>
                default
            </th>
            <th>
                description
            </th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td>
                <strong>ensure</strong>
            </td>
            <td>
                <code>Boolean</code>
            </td>
            <td>
                <code>false</code>
            </td>
            <td>
                If true, intermediate keys that are <code>null</code> or <code>undefined</code> will be filled in with a new empty object <code>{}</code>, ensuring the get will return valid metadata.
            </td>
        </tr>

        <tr>
            <td>
                <strong>getter</strong>
            </td>
            <td>
                <code>String</code>
            </td>
            <td>
                <code>"get"</code>
            </td>
            <td>
                Name of the sub-object getter method use if it exists.
            </td>
        </tr>

        <tr>
            <td>
                <strong>setter</strong>
            </td>
            <td>
                <code>String</code>
            </td>
            <td>
                <code>"set"</code>
            </td>
            <td>
                Name of the sub-object setter method use if it exists.
            </td>
        </tr>

        <tr>
            <td>
                <strong>deleter</strong>
            </td>
            <td>
                <code>String</code>
            </td>
            <td>
                <code>"unset"</code>
            </td>
            <td>
                Name of the sub-object deleter method use if it exists.
            </td>
        </tr>
    </tbody>
</table>


### Delegating Accessors

#### _.get(target, key, def, opts) -> value

Gets the value at `key` from the object if present, returning `def` otherwise.


#### _.set(target, key, value, opts) -> target

Puts a given value to `key` on the given target object. If an object is supplied as `key` instead of a String, 
each key-value pair on that object will be put to the target object. In this case, omit `value`. Returns the 
target object.


#### _.unset(target, key, opts) -> oldValue

Deletes `key` from the target object, returning whatever value was present prior to being removed.


#### _.isMember(object, ...values) -> Boolean

Tests whether all values are contained in the given collection (accepting Object or Array).



### Nested Delegating Accessors

These methods perform **nested** accessor operations, delegating like their non-nested counterparts to
the target object when an instance method is found matching the operation.


#### _.getNested(target, chain, def, opts) -> value

Searches a hierarchical object for a given subkey specified in dotted-property syntax, returning the value
if found, and `def` otherwise.


#### _.setNested(target, chain, value, opts) -> oldValue

Searches a hierarchical object for a given subkey specified in dotted-property syntax, setting it with the 
provided value if found.


#### _.unsetNested(target, chain, opts) -> target

Searches a hierarchical object for a potentially-nested key and removes it, returning whatever value was present 
there prior to being removed.


#### _.getNestedMeta(object, chain, opts) -> Object

*[Private]* Searches a hierarchical object for a given subkey (specified in dotted-property syntax),
respecting sub-object accessor-methods (e.g., 'get', 'set') if they exist. If found, returns an object 
of the form `{ key: Qualified key name, obj: Parent object of key, val: Value at obj[key], opts: Options }`,
and otherwise `undefined`.



### Collection Utilities

#### _.merge(target={}, ...donors) -> target

Recursively merges together any number of donor objects into the target object. (Modified from `jQuery.extend()`.)


#### _.isPlainObject(object) -> Boolean

Returns whether value is a plain object or not.


#### _.remove(object, value) -> Object

In-place removal of a value from an Array or Object. Returns the object.


#### _.items(object) -> Array

Converts the collection to a list of its items:

- Objects become a list of `[key, value]` pairs.
- Strings become a list of characters.
- Arguments objects become an array.
- Arrays are copied.



## Feedback

Find a bug or want to contribute? Open a ticket (or fork the source!) on [github][project]. 
You're also welcome to send me email at [dsc@less.ly][dsc_email].

--

`underscore.nested` was written by [David Schoonover][dsc]; it is open-source software and freely available under the [MIT License][mit_license].



[project]: http://github.com/dsc/underscore.nested "Underscore.nested on GitHub"
[dsc]: https://github.com/dsc/ "David Schoonover"
[dsc_email]: mailto:dsc+underscore.nested@less.ly?subject=underscore.nested "dsc@less.ly"
[mit_license]: http://dsc.mit-license.org/ "MIT License"

[node]: http://nodejs.org/ "node.js"
[npm]: http://npmjs.org/ "npm"
[underscore]: http://underscorejs.org "Underscore.js"
