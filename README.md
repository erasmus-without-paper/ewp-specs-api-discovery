Discovery API
=============

* [What is the status of this document?][statuses]
* [See the index of all other EWP Specifications][develhub]


Summary
-------

**Discovery API** is the first API that the partner developer needs to
implement in order to become a basic member of the *Erasmus Without Paper*
Network.

Discovery manifest files serve to announce which HEIs your system covers, which
features (APIs) you have implemented, and which credentials your clients are
going to use when fetching the data from the EWP Network.


Older versions
--------------

Note, that there's also [an older version 5 of this API][discovery-v5], which
is still supported by the Registry Service, and documents in this format may
still appear in various places.

It is RECOMMENDED for all developers to upgrade their implementations to
version 6 though. Version 5 will be discontinued.


Server requirements
-------------------

Note, that this API doesn't currently follow rules of the *Authentication and
Security* document (the one that most other APIs explicitly follow). It
declares its own security requirements.

In order to implement the Discovery API, you will need to:

 * Host the Discovery Manifest file (described below) somewhere on your
   servers.

 * You MUST host it over HTTPS. The SSL certificate used MUST match your domain
   and be signed by a trusted CA.

 * You MUST keep the file up-to-date. Whenever a new version of any of the APIs
   is supported on your servers, it MUST be immediately reflected in the
   Discovery Manifest.

 * Once you have read and understood the above steps, contact the
   administrators of the [EWP Registry Service administrators][registry-intro]
   and request your EWP Host to be added to the Registry.


Client requirements
-------------------

In general, Manifest files **should be read by the Registry Service only**. You
SHOULD NOT process the Manifest files of other partners by yourself. Use the
Registry instead, to access this data.


Discovery Manifest File
-----------------------

 * "Discovery API response", "Discovery Manifest file", "EWP Host's Manifest" -
   all of these terms describe **exactly the same thing**. We use them
   interchangeably throughout the documentation. Similarly, "implementing the
   Discovery API" and "hosting the Manifest file" also have the same meaning.

 * Your Discovery API response MUST conform to the XML Schema provided in the
   attached [manifest.xsd](manifest.xsd) file.

 * See [manifest-example.xml](manifest-example.xml) for a complete example of a
   valid manifest file.


`manifest-entry.xsd` files
--------------------------

Each manifest file contains multiple API descriptions (in its
`<apis-implemented>` element). Each such API description is described by its
own XML namespace
([why?](https://github.com/erasmus-without-paper/ewp-specs-api-discovery/issues/6)),
and `manifest-entry.xsd` files describe these namespaces - **one namespace per
API**.

In other words, you will see a single `manifest-entry.xsd` file in **each** EWP
API specification (Discovery Manifest API also [has one](manifest-entry.xsd)).

For more information on `<apis-implemented>` element, see
[Registry API][registry-api]'s catalogue schema.


[registry-intro]: https://github.com/erasmus-without-paper/ewp-specs-architecture/blob/stable-v1/README.md#registry
[registry-api]: https://github.com/erasmus-without-paper/ewp-specs-api-registry
[develhub]: http://developers.erasmuswithoutpaper.eu/
[statuses]: https://github.com/erasmus-without-paper/ewp-specs-management/blob/stable-v1/README.md#statuses
[discovery-v5]: https://github.com/erasmus-without-paper/ewp-specs-api-discovery/tree/stable-v5
