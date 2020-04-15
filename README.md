# API extension

Changes to the schemas to make OCDS data more suitable for serving through an API.

It has the changes to the core schema.

* Add a [links section](https://github.com/open-contracting/api-specification) to describe pagination.
* It adds a packageMetadata section to releases/records.  This is because for an API, package metadata may be vary in each release/record and can not be applied to all results in an API. i.e there may be a variety of licenses in a single result.
* It removes mandatory metadata fields from the release/record package as its is now possible (due to the previous change) for this data to be in the release/records themselves.

## Examples

### Paginated releases

A publisher has a service to search releases by date. As the result may include many releases, the publisher returns a paginated package as:

```json
{
  "uri": "https://standard.open-contracting.org/examples/releases/ocds-213czf-000-00001-05-contract.json",
  "license": "http://opendatacommons.org/licenses/pddl/1.0/",
  "publicationPolicy": "https://github.com/open-contracting/sample-data/",
  "version": "1.1",
  "releases": [
    {
      "ocid": "ocds-213czf-000-00001",
      "id": "ocds-213czf-000-00001-05-contract",
      "date": "2010-05-10T10:30:00Z",
      "language": "en",
      "tag": [
        "contract"
      ],
      "initiationType": "tender"
    },
    {
      "ocid": "ocds-213czf-000-00001",
      "id": "ocds-213czf-000-00001-tender",
      "date": "2010-05-10T10:30:00Z",
      "language": "en",
      "tag": [
        "tender"
      ],
      "initiationType": "tender"
    }
  ],
  "links": {
    "next": "https://raw.githubusercontent.com/open-contracting/api-specification/master/multiple-file-api-next/releases-2015.json"
  }
}
```
### Releases with `packageMetadata`

Another publisher package the releases from two different sources, one for tenders and other for contracts. As users may want to know which release comes from which system, the publisher uses the `packageMetadata` field at release level:

```json
{
  "uri": "https://standard.open-contracting.org/examples/releases/ocds-213czf-000-00001-05-contract.json",
  "license": "http://opendatacommons.org/licenses/pddl/1.0/",
  "publicationPolicy": "https://github.com/open-contracting/sample-data/",
  "version": "1.1",
  "releases": [
    {
      "ocid": "ocds-213czf-000-00001",
      "id": "ocds-213czf-000-00001-05-contract",
      "date": "2010-05-10T10:30:00Z",
      "language": "en",
      "tag": [
        "contract"
      ],
      "initiationType": "tender",
      "packageMetadata": {
        "publishedDate": "2010-06-10T10:30:00Z",
        "publisher": {
          "scheme": "GB-COH",
          "uid": "09506232",
          "name": "Open Data Services Co-operative Limited",
          "uri": "https://standard.open-contracting.org/examples/"
        }
      }
    },
    {
      "ocid": "ocds-213czf-000-00001",
      "id": "ocds-213czf-000-00001-tender",
      "date": "2010-05-10T10:30:00Z",
      "language": "en",
      "tag": [
        "tender"
      ],
      "initiationType": "tender",
      "packageMetadata": {
        "publishedDate": "2010-06-10T10:30:00Z",
        "publisher": {
          "scheme": "GB-COH",
          "uid": "012345",
          "name": "Tender Data Services"
        }
      }
    }
  ]
}
```
## Issues

Report issues for this extension in the [ocds-extensions repository](https://github.com/open-contracting/ocds-extensions/issues), putting the extension's name in the issue's title.
