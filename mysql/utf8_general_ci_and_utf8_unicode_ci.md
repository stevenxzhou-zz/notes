## What's the difference between utf8_general_ci and utf8_unicode_ci


#### Accuracy
The unicode one has more accurate sorting implemetation as it covers more diverse languages. The general one can result in undesirable results when sorting centain languages.

#### Performance
The general one is faster at comparison and sorting as 'it takes a bunch of performance related shortcuts'. But for mordern servers, this performance boost can be neligible. The unicode one has a sligtly lower performance due to it has implematations to take care all languages to make it sort in a alphabetically order.

So for most latin languages, it would be mostly the same using these two encodings, however, when it comes to a asian language, the result coulddiverge a lot. Overall, the unicode would be more accurate in such cases.

#### When to use what?
As the modern moachine has much better performance than before, we should all prefer to use unicode. This should never be a bottleneck of database query performance, instead, when it comes to the issue, we should put more effort in investigating indexes and schema set up.

#### How to update a table's encoding from genral to unicode?
```SQL
ALTER TABLE 'TABLE_NAME' CONVERT TO CHARACTER SET utf8 COLLATE utf8_unicode_ci;
```

Reference:  
[1] [What's the difference between utf8_general_ci and utf8_unicode_ci](http://stackoverflow.com/questions/766809/whats-the-difference-between-utf8-general-ci-and-utf8-unicode-ci)