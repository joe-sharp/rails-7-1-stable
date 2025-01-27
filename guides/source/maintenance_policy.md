**DO NOT READ THIS FILE ON GITHUB, GUIDES ARE PUBLISHED ON https://guides.rubyonrails.org.**

Maintenance Policy for Ruby on Rails
====================================

Support of the Rails framework is divided into four groups: New features, bug
fixes, security issues, and severe security issues. They are handled as
follows, all versions, except for security releases, in `X.Y.Z`, format.

--------------------------------------------------------------------------------

Versioning
------------

Rails follows a shifted version of [semver](https://semver.org/):

**Patch `Z`**

Only bug fixes, no API changes, no new features.
Except as necessary for security fixes.

**Minor `Y`**

New features, may contain API changes (Serve as major versions of Semver).
Breaking changes are paired with deprecation notices in the previous minor
or major release.

**Major `X`**

New features, will likely contain API changes. The difference between Rails'
minor and major releases is the magnitude of breaking changes, and usually
reserved for special occasions.

New Features
------------

New features are only added to the main branch and will not be made available
in point releases.

Bug Fixes
---------

Only the latest release series will receive bug fixes. Bug fixes are typically
added to the main branch, and backported to the x-y-stable branch of the latest
release series if there is sufficient need. When enough bugs fixes have been added
to an x-y-stable branch, a new patch release is built from it. For example, a
theoretical 1.2.2 patch release would be built from the 1-2-stable branch.

In special situations, where someone from the Core Team agrees to support more series,
they are included in the list of supported series.

For unsupported series, bug fixes may coincidentally land in a stable branch,
but won't be released in an official version. It is recommended to point your
application at the stable branch using Git for unsupported versions.

**Currently included series:** `7.1.Z`.

Security Issues
---------------

The current release series and the next most recent one will receive patches
and new versions in case of a security issue.

These releases are created by taking the last released version, applying the
security patches, and releasing. Those patches are then applied to the end of
the x-y-stable branch. For example, a theoretical 1.2.2.1 security release would
be built from 1.2.2, and then added to the end of 1-2-stable. This means that
security releases are easy to upgrade to if you're running the latest version
of Rails.

Only direct security patches will be included in security releases. Fixes for
non-security related bugs resulting from a security patch may be published on a
release's x-y-stable branch, and will only be released as a new gem in
accordance with the Bug Fixes policy.

Security releases are cut from the last security release branch/tag. Otherwise
there could be breaking changes in the security release. A security release
should only contain the changes needed to ensure the app is secure so that it's
easier for applications to remain upgraded.

**Currently included series:** `7.1.Z`, `7.0.Z`

Severe Security Issues
----------------------

For severe security issues all releases in the current major series, and also the
last release in the previous major series will receive patches and new versions. The
classification of the security issue is judged by the core team.

**Currently included series:** `7.1.Z`, `7.0.Z`, `6.1.Z`.

Unsupported Release Series
--------------------------

When a release series is no longer supported, it's your own responsibility to
deal with bugs and security issues. We may provide backports of the fixes and
merge them, however there will be no new versions released. We
recommend to point your application at the stable branch using Git. If you are
not comfortable maintaining your own versions, you should upgrade to a supported
version.

npm Packages
------------

Due to a constraint with npm, we are unable to use the 4th digit for security
releases of [npm packages][] provided by Rails. This means that instead of the
equivalent gem version `7.0.1.4`, the npm package will be versioned `7.0.1-4`.

The version will be calculated as `X.Y.Z0A`, where `A` is the security release.

[npm packages]: https://www.npmjs.com/org/rails
