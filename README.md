# fcc-ecfs-data

## What?

This repo contains data from the [Federal Communication Commission's Electronic Comment Filing System](http://apps.fcc.gov/ecfs/). 

## Why?

1. There currently is no official API for comments filed at the FCC.

2. This is a good use-case to experiment with the idea that a Github repo can be used as an open data API.

3. I already have this data (it powers [Dokket.com](http://dokket.com)), and publishing it is no sweat.

## How?

All data is JSON-encoded. Because it's just an export from a [Parse.com](http://parse.com) database, the format should be similar to MongoDB. Each datatype is in its own file with the format `Datatype.json`.

To get the data from one of these files, parse the JSON and get the value of the `"results"` key.

### Datatypes

#### Docket

A `Docket` represents a proceeding by the FCC. Sample:

```json
{
  "bureau_name": "Wireline Competition Bureau",
  "date_created": {
    "__type": "Date",
    "iso": "2012-12-26T00:00:00.000Z"
  },
  "filings_in_last_30_days": "49",
  "number": "12-375",
  "prepared_by": "Aleta.Bowers",
  "status": "Open",
  "subject": "Implementation of the Pay Telephone Reclassification and Compensation Provisions of the Telecommunications Act of 1996 et al.",
  "total_filings": "75",
  "createdAt": "2013-01-29T23:31:34.991Z",
  "updatedAt": "2013-03-13T23:41:34.698Z",
  "objectId": "nwzgZVTGhg"
}
```

#### Filing

A `Filing` belongs to a `Docket` and represents a filing made by a party (or parties) at the FCC for a given proceeding. Sample:

```json
{
  "docket": {
    "__type": "Pointer",
    "className": "Docket",
    "objectId": "nwzgZVTGhg"
  },
  "date_posted": {
    "__type": "Date",
    "iso": "2013-01-22T00:00:00.000Z"
  },
  "date_received": {
    "__type": "Date",
    "iso": "2012-12-24T00:00:00.000Z"
  },
  "docket_number": "12-375",
  "document_urls": [
    "http://apps.fcc.gov/ecfs/document/view?id=7022093344",
    "http://apps.fcc.gov/ecfs/document/view?id=7022093345",
    "http://apps.fcc.gov/ecfs/document/view?id=7022093346",
    "http://apps.fcc.gov/ecfs/document/view?id=7022093347",
    "http://apps.fcc.gov/ecfs/document/view?id=7022093348",
    "http://apps.fcc.gov/ecfs/document/view?id=7022093349"
  ],
  "lawfirm_name": "FCC",
  "md5": "a5dab4a3df0525102a4949aa48ee6a2d",
  "name_of_filer": "Wireline Competition Bureau",
  "type_of_filing": "NOTICE OF PROPOSED RULEMAKING",
  "createdAt": "2013-01-29T23:32:51.494Z",
  "updatedAt": "2013-01-29T23:34:00.232Z",
  "objectId": "lPdoEukAcs"
}
```

To get the actual text of a filing, view the URLs in the `document_urls` field. These are almost always PDFs.

## Warranty

There is no warranty for this data. Moreover, this data is far from comprehensive.