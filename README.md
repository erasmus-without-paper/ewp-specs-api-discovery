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


<a name='multi-manifest'></a>

Splitting your manifest
-----------------------

Most of you will host a single manifest file only. This allows you to define
the list of HEIs, APIs and certificates. Each certificate will be allowed to
access the data of every HEI, and each API will be implemented for every one of
these HEIs too. This is usually the simplest approach, and should be enough for
most of the cases.

However, what if your architecture is more complex? For example, what if the
number of APIs covered differs from HEI to HEI?

In its essence, each `<r:host>` element in the
[Registry's catalogue response][registry-api] is a
[cartesian product](https://en.wikipedia.org/wiki/Cartesian_product)
of many separate sets of elements: **HEIs**, **APIs**, **client certificates**,
**admin email addresses**... This means that you can *change*, or *cut out*
portions of the output product by defining **multiple** manifest files, with
**smaller input sets** in each.

For example:

 * You can declare one manifest file for each of your HEIs. This will allow you
   to "say" that you implement a different set of APIs for each of these HEIs.

 * Or, you can declare a separate set of manifest files with HEIs and client
   credentials only (without the APIs). This will allow you to say that
   **certificate X** should be allowed to request data as **HEI 1** only, while
   **certificate Y** should be allowed to request data as **HEI 2 or HEI 3**.

 * Or, you can declare that **administrator A** should be contacted in
   case of problems with any of the **APIs** implemented for **HEI B** *only*,
   even if you cover multiple HEIs.

All such configurations are valid, and the structure of the Registry's
catalogue will enforce all clients to respect that. However, this will make
the Registry's response more verbose, and more vague to understand for humans,
so we advise to *not* split your manifest unless you really need to.


[registry-intro]: https://github.com/erasmus-without-paper/ewp-specs-architecture/blob/stable-v1/README.md#registry
[registry-api]: https://github.com/erasmus-without-paper/ewp-specs-api-registry
[develhub]: http://developers.erasmuswithoutpaper.eu/
[statuses]: https://github.com/erasmus-without-paper/ewp-specs-management/blob/stable-v1/README.md#statuses
