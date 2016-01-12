Discovery API
=============

* [What is the status of this document?][statuses]
* [See the index of all other EWP Specifications][develhub]


Summary
-------

**Discovery API** is the first API that the partner developer needs to
implement in order to become a basic member of the *Erasmus Without Paper*
Network.

 * It serves to identify you, announce which HEIs your system covers, and which
   certificates you are going to use when you will be fetching the data from
   the EWP Network. It's like a simple "business card" of your EWP Host.

 * It serves to inform all **other** members of the network about which
   features (APIs) **you** have implemented. This list MAY include external
   APIs (unrelated to the EWP Project).


Requirements
------------

In order to implement the Discovery API, you will need to:

 * Host the Discovery Manifest file (described below) somewhere on your
   servers.

 * You MUST host it over HTTPS. The SSL certificate used MUST match your domain
   and be signed by a trusted CA.

 * You MUST keep the file up-to-date. Whenever a new version of any of the APIs
   is supported on your servers, it MUST be immediately reflected in the
   Discovery Manifest.

 * Once you have read and understood the above steps, contact the
   administrators of the [EWP Partners Registry][registry] and request your
   EWP Host to be added to the Registry.


Discovery Manifest File
-----------------------

The manifest itself is a simple XML file.

 * It MUST conform to the XML Schema provided in the attached [schema.xsd]
   (schema.xsd) file.
 * See [example.xml](example.xml) for an example of a valid manifest.


[registry]: https://github.com/erasmus-without-paper/ewp-specs-architecture/blob/master/README.md#registry)
[develhub]: http://developers.erasmuswithoutpaper.eu/
[statuses]: https://github.com/erasmus-without-paper/ewp-specs-management/blob/master/README.md#statuses
