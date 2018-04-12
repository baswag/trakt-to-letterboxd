# trakt-to-letterboxd

## Description

A package to migrate your trakt movie history to letterboxd. Currently letterboxd only supports importing from a csv, so thats all this package does at the moment. When a proper API is added, I'll update this to push the data right into your letterboxd history.

## Usage

### Note
I haven't added unit tests and published to npm yet, bear with me. If you cant wait to use it then just clone the repo, run `yarn && yarn compile` in the repo directory, then run `./dist/ttl.js --help`.

The easiest way to use this currently is with npx. You can install that globally with `yarn global add npx` or `npm i -g npx`. Once you have that, just run:

```sh
npx trakt-to-letterboxd -u username -f filename
```

where username is the user whose data you want to export, and filename is the name of the csv file you want to output to.

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

#### Table of Contents

-   [traktHistoryToCsv](#trakthistorytocsv)
-   [headers](#headers)
-   [options](#options)
-   [fetchMovies](#fetchmovies)
-   [schema](#schema)
-   [builder](#builder)

### traktHistoryToCsv

[src/main/index.js:19-28](https://github.com/bbeesley/trakt-to-letterboxd/blob/71725c91561779003b4fc3e4687ce7a9487ba32b/src/main/index.js#L19-L28 "Source code on GitHub")

Export a trakt user's history to csv to be uploaded to letterboxd

**Parameters**

-   `props` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** Properties passed from argv
    -   `props.userName` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** The user whose data you want to export
    -   `props.fileName` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** The name of the file to output to

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;void>** We dont return anything

### headers

[src/main/fetcher.js:10-14](https://github.com/bbeesley/trakt-to-letterboxd/blob/71725c91561779003b4fc3e4687ce7a9487ba32b/src/main/fetcher.js#L10-L14 "Source code on GitHub")

HTTP headers to send with our request to trakt's api

### options

[src/main/fetcher.js:20-22](https://github.com/bbeesley/trakt-to-letterboxd/blob/71725c91561779003b4fc3e4687ce7a9487ba32b/src/main/fetcher.js#L20-L22 "Source code on GitHub")

The fetch options object (only really needs headers)

### fetchMovies

[src/main/fetcher.js:30-41](https://github.com/bbeesley/trakt-to-letterboxd/blob/71725c91561779003b4fc3e4687ce7a9487ba32b/src/main/fetcher.js#L30-L41 "Source code on GitHub")

Fetches the user's history data from the trakt api

**Parameters**

-   `user` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** The username we're getting data for

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;TraktMovieHistoryType>** Promise that resolves to trakt history array

### schema

[src/main/exporter.js:9-29](https://github.com/bbeesley/trakt-to-letterboxd/blob/71725c91561779003b4fc3e4687ce7a9487ba32b/src/main/exporter.js#L9-L29 "Source code on GitHub")

Schema for the output csv.
Based on <https://letterboxd.com/about/importing-data/>

### builder

[src/main/exporter.js:37-38](https://github.com/bbeesley/trakt-to-letterboxd/blob/71725c91561779003b4fc3e4687ce7a9487ba32b/src/main/exporter.js#L37-L38 "Source code on GitHub")

The instance of CsvBuilder we'll use to export the data.
We need to remap the format of the last watched date to YYYY-MM-DD
to comply with letterboxd's formatting
