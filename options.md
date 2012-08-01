
| name          | type      | default     | description                                                                                                                                            |
| ------------- | --------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **ensure**    | `Boolean` | `false`     | If true, intermediate keys that are `null` or `undefined` will be filled in with a new empty object `{}`, ensuring the get will return valid metadata. |
| **getter**    | `String`  | `"get"`     | Name of the sub-object getter method use if it exists.                                                                                                 |
| **setter**    | `String`  | `"set"`     | Name of the sub-object setter method use if it exists.                                                                                                 |
| **deleter**   | `String`  | `"unset"`   | Name of the sub-object deleter method use if it exists.                                                                                                |
| **tombstone** | `Object`  | `TOMBSTONE` | Sentinel value to be interpreted as no-passthrough, forcing the lookup to fail and return `undefined`. TODO: opts.returnTombstone                      |

