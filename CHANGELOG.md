Release notes
=============

This document describes all the changes made to the *Discovery API* document,
starting from its first released version.


5.1.0
-----

* Added note about using company aliases as admin-email.
* Imposed 1 to 1 communication in EWP.
  **It is no longer possible to have more than one host and one hei in a manifest!**


5.0.0
-----

New major version. **Backward-incompatible changes:**

* All manifest contents are now required to be enclosed in the `<host>`
  element.

* The manifest MAY now contain any number of `<host>` elements (from zero to
  infinity). Previously, the manifest could be used to describe exactly one EWP
  Host. See
  [this issue](https://github.com/erasmus-without-paper/ewp-specs-api-discovery/issues/7).

Other changes:

* Updated example reflecting recent changes in the Registry API.

Note, that at the moment, the Registry Service supports both major formats (4
and 5).


4.1.1
-----

* Added notices about version `4.x.x` being obsoleted by version `5.0.0`.
* Fixed some minor details in `manifest-example.xml`.


4.1.0
-----

* New optional element under `<client-credentials-in-use>`: `<rsa-public-key>`.
* New optional `<manifest>` section: `<server-credentials-in-use>`.
* Updated `manifest-example.xml`. Makes use of the newly introduced elements,
  and HTTP Signature authentication methods.


4.0.5
-----

* Updated `manifest-example.xml`. It now features Echo API 2.0.0, which in turn
  makes use of the new *Version 2* of *Authentication and Security*
  specification.


4.0.4
-----

* Use a bit more explicit wording in different parts of the specification.


4.0.3
-----

* Just updated some links (after splitting the Architecture and Security
  document).


4.0.2
-----

* `minOccurs` and `maxOccurs` are now provided explicitly
  ([why?](https://github.com/erasmus-without-paper/general-issues/issues/22)).


4.0.1
-----

* More details were added about `manifest-entry.xsd` files.
* Some examples were added describing scenarios when one might want to split
  his manifest file into a couple of smaller ones.


4.0.0
-----

* `<apis-implemented>` and `<hei>` elements were moved to the Registry API's
  XML namespace. Thanks to this change, the Registry's catalogue won't need to
  reuse elements from Discovery API's XML namespace (which is a good thing,
  because the latter one is more likely to change in a backward-incompatible
  manner).

* The deprecated `fingerprint` attribute of the `<certificate>` element was
  removed.

* For consistency, Discovery API's manifest entry has been moved to a separate
  namespace (all other APIs currently keep it in a separate namespace too).

* As with all major version changes, XML namespace identifiers were changed
  (`stable-v3` was replaced with `stable-v4`).


3.2.0
-----

* `fingerprint` attribute of the `<certificate>` element has been marked as
  deprecated (to be removed in a future major release). It's length has been
  also corrected (SHA-256 hex digests have 64 characters, not 40).

* Minor changes to the example manifest file (updated client certificate).


3.1.0
-----

* Unknown API entries are no longer strictly validated
  ([more information](https://github.com/erasmus-without-paper/ewp-specs-api-discovery/issues/9)).

* `<dev-email>` and `<dev-notes>` elements were renamed to `<admin-email>` and
  `<admin-notes>` respectively
  ([more information](https://github.com/erasmus-without-paper/ewp-specs-api-discovery/issues/8)).


3.0.0
-----

Backward-incompatible changes:

* Definitions of `<echo>` and `<registry>` API entries have been removed from
  the manifest's XML namespace. From now on, each API will be described in *its
  own* `manifest-entry.xsd` XML namespace (so that its documentation will be
  present only in its own repository). See
  [this issue](https://github.com/erasmus-without-paper/ewp-specs-api-discovery/issues/6)
  for rationale.

* The above change would render `<dev-email>` and `<dev-notes>` elements to be
  duplicated in two separate namespaces, so - to keep it clean - they were
  moved to the
  [common-types namespace](https://github.com/erasmus-without-paper/ewp-specs-architecture/blob/stable-v1/common-types.xsd).


2.0.0
-----

Backward-incompatible changes:

* The `<client-certificates-in-use>` element has been renamed to
  `<client-credentials-in-use>`.

* The `<common-name>` element was removed.
  [Click here](https://github.com/erasmus-without-paper/ewp-specs-architecture/issues/2)
  for details.

* A single EWP Host is now allowed to serve multiple versions of a single API.
  Elements in `<apis-implemented>` are now `maxOccurs="unbounded"`. Details
  and reasoning can be found
  [here](https://github.com/erasmus-without-paper/ewp-specs-architecture/issues/6).

* EWP Hosts are now required to keep track of SCHAC ID changes (they must
  publish previous SCHAC IDs in the manifest file). Details and reasoning can
  be found [here](https://github.com/erasmus-without-paper/ewp-specs-api-discovery/issues/4).

* `SHA-1` hashes replaced with `SHA-256`
  ([reasoning](https://github.com/erasmus-without-paper/ewp-specs-api-discovery/issues/2)).

Other changes:

* The `ApiEntry/dev-notes` element was missing a type (`MultilineString` was
  added).


1.0.1
-----

* Fixed links and XML namespaces
  ([details] (https://github.com/erasmus-without-paper/general-issues/issues/4)).


1.0.0
-----

Initial release. Reviewed
[here](https://github.com/erasmus-without-paper/ewp-specs-api-discovery/pull/1/files)
and initially accepted during the
[meeting](https://github.com/erasmus-without-paper/general-issues/issues/3)
on the 5th of February 2016.
