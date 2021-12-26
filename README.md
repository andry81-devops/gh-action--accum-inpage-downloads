<p align="center">
  <a href="#"><img src="https://img.shields.io/github/repo-size/andry81/gh-action--accum-inpage-downloads" valign="middle" alt="GitHub repo size in bytes" /></a>
• <a href="https://github.com/XAMPPRocky/tokei"><img src="https://tokei.rs/b1/github/andry81/gh-action--accum-inpage-downloads?category=lines" valign="middle" alt="lines of text by tokei.rs" /></a>
</p>

<p align="center">
  <a href="https://github.com/andry81/gh-action--accum-inpage-downloads--gh-stats/commits/master/traffic/views">
    <img src="https://img.shields.io/badge/dynamic/json?color=success&label=Github%20views|all&query=count&url=https://github.com/andry81/gh-action--accum-inpage-downloads--gh-stats/raw/master/traffic/views/latest-accum.json?raw=True&logo=github" valign="middle" alt="GitHub views|any|total" />
    <img src="https://img.shields.io/badge/dynamic/json?color=success&label=14d&query=count&url=https://github.com/andry81/gh-action--accum-inpage-downloads--gh-stats/raw/master/traffic/views/latest.json?raw=True" valign="middle" alt="GitHub views|any|14d" /></a>
• <a href="https://github.com/andry81/gh-action--accum-inpage-downloads--gh-stats/commits/master/traffic/views">
    <img src="https://img.shields.io/badge/dynamic/json?color=success&label=Github%20views|unq&query=uniques&url=https://github.com/andry81/gh-action--accum-inpage-downloads--gh-stats/raw/master/traffic/views/latest-accum.json?raw=True&logo=github" valign="middle" alt="GitHub views|unique per day|total" />
    <img src="https://img.shields.io/badge/dynamic/json?color=success&label=14d&query=uniques&url=https://github.com/andry81/gh-action--accum-inpage-downloads--gh-stats/raw/master/traffic/views/latest.json?raw=True" valign="middle" alt="GitHub views|unique per day|14d" /></a>
</p>

<p align="center">
  <a href="https://github.com/andry81/gh-action--accum-inpage-downloads--gh-stats/commits/master/traffic/clones">
    <img src="https://img.shields.io/badge/dynamic/json?color=success&label=Github%20clones|all&query=count&url=https://github.com/andry81/gh-action--accum-inpage-downloads--gh-stats/raw/master/traffic/clones/latest-accum.json?raw=True&logo=github" valign="middle" alt="GitHub clones|any|total" />
    <img src="https://img.shields.io/badge/dynamic/json?color=success&label=14d&query=count&url=https://github.com/andry81/gh-action--accum-inpage-downloads--gh-stats/raw/master/traffic/clones/latest.json?raw=True" valign="middle" alt="GitHub clones|any|14d" /></a>
• <a href="https://github.com/andry81/gh-action--accum-inpage-downloads--gh-stats/commits/master/traffic/clones">
    <img src="https://img.shields.io/badge/dynamic/json?color=success&label=Github%20clones|unq&query=uniques&url=https://github.com/andry81/gh-action--accum-inpage-downloads--gh-stats/raw/master/traffic/clones/latest-accum.json?raw=True&logo=github" valign="middle" alt="GitHub clones|unique per day|total" />
    <img src="https://img.shields.io/badge/dynamic/json?color=success&label=14d&query=uniques&url=https://github.com/andry81/gh-action--accum-inpage-downloads--gh-stats/raw/master/traffic/clones/latest.json?raw=True" valign="middle" alt="GitHub clones|unique per day|14d" /></a>
</p>

<p align="center">
  <a href="https://github.com/andry81/gh-action--accum-inpage-downloads/commits">
    <img src="https://img.shields.io/github/commits-since/andry81/gh-action--accum-inpage-downloads/latest?sort=semver&label=Github%20commits%20since%20latest" valign="middle" alt="GitHub commits since latest version" /></a>
  <a href="https://github.com/andry81/gh-action--accum-inpage-downloads/releases">
    <img src="https://img.shields.io/github/v/release/andry81/gh-action--accum-inpage-downloads?include_prereleases&label=latest" valign="middle" alt="latest release name" /></a>
</p>

---

<p align="center">
  <a href="https://github.com/andry81/gh-action--accum-inpage-downloads/blob/master/userlog.md">Userlog</a>
• <a href="https://github.com/andry81/gh-action--accum-inpage-downloads/blob/master/changelog.txt">Changelog</a>
• <a href="#dependecies">Dependencies</a>
• <a href="#known_issues">Known issues</a>
• <a href="#copyright-and-license"><img src="https://github.com/andry81/andry81/raw/master/badges/mit-license.svg" valign="middle" alt="copyright and license" />&nbsp;Copyright and License</a>
</p>

<h4 align="center">GitHub composite action to request and accumulate inpage downloads.<br/>
<br/>
Tutorial to use with: https://github.com/andry81/github-accum-stats</h4>

##

# gh-action--accum-inpage-downloads@master

**Features**:

* Repository to track and repository to store traffic statistic can be different, and you may directly point the statistic as commits list:
  `https://github.com/{{REPO_OWNER}}/{{REPO}}--gh-stats/commits/master/traffic/board/phpbb`

* Workflow is used [accum-downloads.sh](https://github.com/andry81/gh-workflow/blob/master/bash/inpage/accum-downloads.sh) bash script to accumulate traffic downloads

* The script accumulates statistic both into a single file and into a set of files grouped by year and allocated per day:
  `traffic/downloads/mypage/by_year/YYYY/YYYY-MM-DD.json`

# USAGE

> :warning: You must replace all placeholder into respective values:

* `{{REPO_OWNER}}` -> repository owner
* `{{REPO}}` -> your repository

## Examples:

`.github/workflows/accum-mypage-download-stats.yml`:

```yml
# based on: https://github.com/andry81/github-accum-stats
#

name: mypage download stats updating every 4 hours

on:
  schedule:
    - cron: "0 */4 * * *"
  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

jobs:
  accum-mypage-download-stats:
    runs-on: ubuntu-latest


    steps:
      - uses: {{REPO_OWNER}}/gh-action--accum-inpage-downloads@master
        with:
          # CAUTION: Beware of double quotes strip in case of usage yaml `>-` operator or even a single-quotted string!
          query_url:                http://www.mypage.net/index.html
          downloads_sed_regexp:     s/.*Downloaded:[^0-9]*([0-9.]+).*/\1/p

          curl_flags: >-
            -H 'Cache-Control: no-cache'

          deps_repo_owner:          {{REPO_OWNER}}
          stat_entity_path:         mypage/{{REPO}}

          output_repo_owner:        {{REPO_OWNER}}
          output_repo:              {{REPO}}--download-stats
          output_repo_branch:       master
          output_repo_dir:          traffic/downloads/mypage
          output_repo_write_token:  ${{ secrets.READ_STATS_TOKEN }}
```

> :information_source: You can use `secrets.READ_STATS_TOKEN` instead of `secrets.WRITE_STATS_TOKEN` as long as both repositories under the same repository owner.

> :warning: You must use different values for `deps_repo_owner` and `output_repo_owner` if respective repositories actually under different repository owners.

> :information_source: See <a href="https://github.com/andry81/github-accum-stats/blob/master/README.md#reuse">REUSE</a> section for details if you have multiple repositories and want to store all workflow scripts in a single repository.

## Dependencies<a name="dependecies"></a>

* https://github.com/andry81/gh-workflow

## Known Issues<a name="known_issues"></a>

The action has supported not all features of a generic GitHub action: https://github.com/actions/runner/issues/646

> **What does Composite Run Steps Not Support**
>
> We don't support setting conditionals, continue-on-error, timeout-minutes, "uses", and secrets on individual steps within a composite action right now.
>
> (Note: we do support these attributes being set in workflows for a step that uses a composite run steps action)

## Copyright and License<a name="copyright-and-license"></a>

Code and documentation copyright 2021 Andrey Dibrov. Code released under [MIT License](https://github.com/andry81/gh-action--accum-inpage-downloads/blob/master/license.txt)
