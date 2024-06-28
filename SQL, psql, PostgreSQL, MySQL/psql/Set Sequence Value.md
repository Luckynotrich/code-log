
Sets the sequence object's current value, and optionally its `is_called` flag. The two-parameter form sets the sequence's `last_value` field to the specified value and sets its `is_called` field to `true`, meaning that the next `nextval` will advance the sequence before returning a value. The value that will be reported by `currval` is also set to the specified value. In the three-parameter form, `is_called` can be set to either `true` or `false`. `true` has the same effect as the two-parameter form. If it is set to `false`, the next `nextval` will return exactly the specified value, and sequence advancement commences with the following `nextval`. Furthermore, the value reported by `currval` is not changed in this case. For example,
```
SELECT setval('myseq', 42);           _Next `nextval` will return 43_
SELECT setval('myseq', 42, true);     _Same as above_
SELECT setval('myseq', 42, false);    _Next `nextval` will return 42_
```
The result returned by `setval` is just the value of its second argument.

This function requires `UPDATE` privilege on the sequence.