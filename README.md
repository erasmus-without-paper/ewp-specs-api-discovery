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
going to use when fetching the data from the EWP Network. Depending on your
system design, you may be required to serve multiple manifest files (e.g. if
the number of APIs covered differs from HEI to HEI).


Server requirements
-------------------

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
SHOULD NOT attempt to process the Manifest files of other EWP Hosts by
yourself. Use the Registry instead.


Discovery Manifest File
-----------------------

 * "Discovery API response", "Discovery Manifest file", "EWP Host's Manifest" -
   all of these terms describe **exactly the same thing**. We use them
   interchangeably throughout the documentation. Similarly, "implementing the
   Discovery API" and "hosting the Manifest file" also have the same meaning.

 * Your Discovery API response MUST conform to the XML Schema provided in the
   attached [manifest.xsd](manifest.xsd) file.

 * The [manifest-entry.xsd](manifest-entry.xsd) file describes a Discovery API
   entry to be placed within the `<apis-implemented>` section of the manifest
   file. This self-reference is required for completeness (since Discovery API
   lists *all* APIs hosted by you, then it should also include itself,
   shouldn't it?). Note, that other EWP APIs have similar `manifest-entry.xsd`
   files in their specs (you will use them to indicate which of those APIs you
   have implemented).

 * See [manifest-example.xml](manifest-example.xml) for a complete example of a
   valid manifest file.


[registry-intro]: https://github.com/erasmus-without-paper/ewp-specs-architecture/blob/stable-v1/README.md#registry
[develhub]: http://developers.erasmuswithoutpaper.eu/
[statuses]: https://github.com/erasmus-without-paper/ewp-specs-management/blob/stable-v1/README.md#statuses
