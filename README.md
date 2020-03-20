# Datasette for 2AJF

Drag and drop the CSV file to the project root and it will be converted into a SQLite database and loaded into a Datasette instance.

This is a Datasette for the [2AJF](https://www.rcsb.org/structure/2AJF) structure, all rights of the protien, data and structure go to its respective owners. 

DOI: [10.2210/pdb2AJF/pdb](10.2210/pdb2AJF/pdb)

Hit this Remix button to get your own copy of this project:

[![Remix on Glitch](https://cdn.glitch.com/2703baf2-b643-4da7-ab91-7ee2a2d00b5b%2Fremix-button.svg)](https://glitch.com/edit/#!/remix/datasette-csvs)

You can uncomment lines in `requirements.txt` to install extra plugins.

See [Running Datasette on Glitch](https://simonwillison.net/2019/Apr/23/datasette-glitch/) for more about this project.

## Configuring full-text search

Datasette supports SQLite full-text search. You can configure it for a table using the `sqlite-utils` command-line tool.

In the Glitch editor select Tools -> Full Page Console, then run the following:

    $ cd .data
    $ sqlite-utils tables data.db --table --columns
    table    columns
    -------  ------------------------------------
    example  ['headline', 'body', 'url', 'extra']

This shows you the tables and columns in your database.

If you want to make the `example` table searchable by `headline` and `body`, run the following command:

    $ sqlite-utils enable-fts data.db example headline body --fts4

Your Datasette instance will now display a search box that can be used to search the text in those columns.
