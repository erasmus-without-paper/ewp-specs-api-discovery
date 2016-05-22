Release notes
=============

This document describes all the changes made to the *Discovery API* document,
starting from its first released version.

3.1.0 (unreleased)
------------------

* Unknown API entries are no longer strictly validated ([more information]
  (https://github.com/erasmus-without-paper/ewp-specs-api-discovery/issues/9)).


3.0.0
-----

Backward-incompatible changes:

* Definitions of `<echo>` and `<registry>` API entries have been removed from
  the manifest's XML namespace. From now on, each API will be described in *its
  own* `manifest-entry.xsd` XML namespace (so that its documentation will be
  present only in its own repository). See [this issue]
  (https://github.com/erasmus-without-paper/ewp-specs-api-discovery/issues/6)
  for rationale.

* The above change would render `<dev-email>` and `<dev-notes>` elements to be
  duplicated in two separate namespaces, so - to keep it clean - they were
  moved to the [common-types namespace]
  (https://github.com/erasmus-without-paper/ewp-specs-architecture/blob/stable-v1/common-types.xsd).


2.0.0
-----

Backward-incompatible changes:

* The `<client-certificates-in-use>` element has been renamed to
  `<client-credentials-in-use>`.

* The `<common-name>` element was removed. [Click here]
  (https://github.com/erasmus-without-paper/ewp-specs-architecture/issues/2)
  for details.

* A single EWP Host is now allowed to serve multiple versions of a single API.
  Elements in `<apis-implemented>` are now `maxOccurs="unbounded"`. Details
  and reasoning can be found
  [here](https://github.com/erasmus-without-paper/ewp-specs-architecture/issues/6).

* EWP Hosts are now required to keep track of SCHAC ID changes (they must
  publish previous SCHAC IDs in the manifest file). Details and reasoning can
  be found [here](https://github.com/erasmus-without-paper/ewp-specs-api-discovery/issues/4).

* `SHA-1` hashes replaced with `SHA-256` ([reasoning]
  (https://github.com/erasmus-without-paper/ewp-specs-api-discovery/issues/2)).

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
