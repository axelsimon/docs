# Frequently Asked Questions

## How do I handle custom SSL certificates?

If you run your own CA, check out [the options](https://github.com/firefly-iii/data-importer/blob/main/.env.example#L51) in the `.env.example` file.

## How do I start over or reset the importer?

Browse to the `/flush`-URL on the data importer to reset it. There is also a button you can use on every page.

## My connection times out, even though the IP addresses are correct

This mainly applies to Docker. Make sure that both containers [are on the same network](https://old.reddit.com/r/FireflyIII/comments/fuur8o/csvimporter_connection_timeout/). Remember that Firefly III usually runs on port 8080.

Please open a ticket [on GitHub](https://github.com/firefly-iii/firefly-iii/) if you can't get it to work.

## Why can't I import duplicate transactions?

The Firefly III data importer can recognise two different types of duplicate transactions. By default, it will refuse to import both of these types.

1. Duplicate lines in your CSV files are skipped, unless you explicitly tell the data importer to import them anyway.
2. Firefly III itself will refuse to import transactions it believes already exist. You can overrule this.

## Why isn't the data importer built into Firefly III?

I turned the data importer into a separate tool. It allows me to keep track of two different tools with different development requirements and.

## Why isn't this a plugin, like WordPress?

It adds a whole layer of complexities to Firefly III. A plugin needs a framework to land in. For the data importer to be a plugin, I would first have to build it so Firefly III supports plugins. And then the data importer would be the only plugin.

The [API](../../firefly-iii/api.md) is a plugin system of sorts.

## How can I automate this?

The easiest way to automate imports is by using [the command line option to automatically import files](../usage/command_line.md).

<!--


## Common problems and errors

### UTF-8 encoding.

Make sure the file is UTF-8 encoded. Because it's hard for PHP to detect this properly and guarantee a hassle-free conversion, you must do any conversion to UTF-8 yourself.

### Extra lines

No extra text may be present before or after the data. This is bad form. A CSV file is for computers to read, not for humans. The CSV importer has no feature to remove a number of lines from the start of the file.

-->