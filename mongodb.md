# Sort

Unless use sort() or $near, the order of query results is not guaranteed.

If there is no query or query without index(collection scan), natural(storage) order is used, it's not guaranteed to be the same with insertion order(when a doc is moved or a new doc is inserted into a gap).

If an index is used, docs will be returned in the order they are found. If more than one index is used then the order depends internally on which index first identified the document during the de-duplication process.

The sort operation requires that the entire sort be able to complete within 32 megabytes, otherwise use index or limit()
