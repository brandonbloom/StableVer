# StableVer

This document describes the "StableVer" versioning scheme. Like SemVer and related schemes,
major version numbers convey semantic information about breaking changes. Unlike SemVer,
StableVer discourages breaking changes by adding semantics regarding feature stability,
deprecation, and migrations.

Version numbers have the short form:

`<major>.<minor>`

Breaking changes may only be introduced in major version bumps. However, no breaking change
may be made to a feature unless it was declared deprecated in the _previous_ major version bump.

A key property of projects that use StableVer is that it should always be possible to
migrate from major version N to major version N+1 without breaking changes -- provided that
you are not using any features that were marked deprecated in version N.

## Stability Status

Projects using StableVer are responsible for communicating the stability status
of individual APIs, data formats, and other features.

Functionality can be either **stable** or **unstable**. Stable features are not
subject to breaking changes, even in major version upgrades.

Unstable features fall in to five categories: **alpha**, **beta**,
**deprecated**, **internal**, and **undefined**.

**Alpha** features are subject to breaking changes at anytime and without
warning.

**Beta** features _may_ experience breaking changes, but the goal is for them to
stabilize, and so such breakage will be accompanied by guidance. It is not necessary
to bump the major version when making changes to beta features.

**Deprecated** features are previously _beta_ or _stable_ features that will be
_removed_ in the next major version release. Warning and a migration plan will be provided.

**Internal** features are also subject to breaking changes at anytime. They
differ from _alpha_ features in that they are not expected to stabilize.

**Undefined** behavior of features is the subset of functionality of any feature
-- include _stable_ features -- that has not been adequately documented. Undefined
behavior is treated as _internal_ for unstable features, and as _beta_ when associated
with otherwise _stable_ features.

## Version Numbering

When the major version is 0, it is called the "alpha release". All features are
considered _alpha_, unless explicitly declared otherwise. Even if designated
_stable_, functionality in an alpha release should should be treated as _beta_
at best.

For major version 1 and up, all _documented_ features are considered _stable_,
unless otherwise indicated. All _undocumented_ functionality is considered
_internal_.

Non-breaking bug fixes and _unstable_ features may be added or modified in any minor version
release. Bug fixes may introduce breaking changes within the _undefined_ portion of _stable_
features, but should be accompanied by guidance.

Major version bumps _may_ be used for marketing purposes, even if there are no new deprecations
or feature removals. This capacity should not be used to avoid providing sufficient migration
time for deprecations.
