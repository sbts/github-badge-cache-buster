# github-badge-cache-buster
A small tool that uses curl to PURGE the github cache for badges displayed in README.md files

Unfortunately github caches badges ( on a server called camo.githubusercontent.com ) quite agressively.
This leads to badge data being out of date a lot of the time.

Theoretically if the src badge image correctly sets....
`Cache-Control: no-cache, no-store`
`Expire: Mon, 01 Jan 1990 00:00:00 GMT`
`Last-Modified: Mon, 01 Jan 2999 00:00:00 GMT`
and a unique to each request etag
`Etag: $UUID`
Everything should work just fine. However, many people find that not to be the case.

I found another possible workaround that calls for adding a dummy paramater to the URL of the badge.
This may or may not work for all badge sources.
```plain
[tv-nightly-image]: https://jimtru1979.blob.core.windows.net/badges/DailyBuildStatus.svg?dummy=unused
[![Coverage Status](https://coveralls.io/repos/github/ledgersmb/LedgerSMB/badge.svg?branch=master)](https://coveralls.io/github/ledgersmb/LedgerSMB?branch=master&dummy=unused)
```

There is a large list of bugs open (and incorrectly closed) relating to this.
The main issue is
- [#224](https://github.com/github/markup/issues/224) - Aggressive image caching breaks image badges

Some of the others are.....
- [#9](https://github.com/rvagg/nodei.co/issues/9) - GitHub Image Proxy breaking Nodei.co images in markdown
- [#15](https://github.com/badges/pypipins/issues/15) - Badges do not update with GitHubs caching
- [#111]() - can't find the URL for this one
- [#116]() - can't find the URL for this one
- [#134](https://github.com/badges/shields/issues/134) - Serve cached images upon request timeout
- [#137](https://github.com/badges/shields/issues/137) - Travis badges seem to be broken
- [#218](https://github.com/codecov/support/issues/218) - GitHub caching affecting my badge
- [#220](https://github.com/lemurheavy/coveralls-public/issues/220) - Set `Cache-Control` or `Expires` on S3 assets
- [#257](https://github.com/drone/drone/pull/257) - Badge caching
- [#414](https://github.com/lemurheavy/coveralls-public/issues/414) - Incorrect coverage badge
- [#1970](https://github.com/travis-ci/travis-ci/issues/1970) - Build status image cached by GitHub
- [#3122](https://github.com/PowerShell/PowerShell/issues/3122) - Code Coverage Status Badge is cached
- [#3150](https://github.com/PowerShell/PowerShell/issues/3150) - Unix nightly badge is inaccurate
- [#6040](https://github.com/pouchdb/pouchdb/pull/6040) - fix coveralls badge issue in README
- [#17057](https://gitlab.com/gitlab-org/gitlab-ce/issues/17057) - Aggressive GitHub caching breaks Gitlab badge images.