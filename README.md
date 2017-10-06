Changes to the schemas to make OCDS data more suitable for serving through an API.

It has the changes to the core schema.

* Add a links section to describe pagination.
* It adds a packageMetadata section to releases/records.  This is because for an API, package metadata may be vary in each release/record and can not be applied to all results in an API. i.e there may be a variaty of licenses in a single result.
* It removes mandatory metadata fields from the release/record package as its is now possible (due to the previous change) for this data to be in the release/records themselves.


The links section is described in https://github.com/open-contracting/api-specification.

## Issues

Report issues for this extension in the [ocds-extensions repository](https://github.com/open-contracting/ocds-extensions/issues), putting the extension's name in the issue's title.
