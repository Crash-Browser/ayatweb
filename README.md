<p align="center">
  <a href="https://github.com/apps/pull">
    <img alt="Pull App" src="https://prod.download/pull-social-svg" />
  </a>
</p>
<p align="center">
  <a href="https://probot.github.io">
    <img alt="Probot Featured" src="https://badgen.net/badge/probot/featured/orange?icon=dependabot&cache=86400" />
  </a>
  <a href="https://github.com/wei/pull">
    <img alt="GitHub Stars" src="https://badgen.net/github/stars/wei/pull?icon=github" />
  </a>
  <br/>
  <a href="https://github.com/apps/pull">
    <img alt="Managing" src="https://badgen.net/https/raw.githack.com/pull-app/stats/master/badges/managing.json" />
  </a>
  <a href="https://github.com/apps/pull">
    <img alt="Installations" src="https://badgen.net/https/raw.githack.com/pull-app/stats/master/badges/installed.json" />
  </a>
  <a href="https://github.com/issues?q=author%3Aapp%2Fpull">
    <img alt="Triggered #" src="https://badgen.net/runkit/pull-triggered-badge-5e55hqhkhmid" />
  </a>
</p>

<h2>Table of Contents</h2>
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Introduction](#introduction)
- [Features](#features)
  - [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [Basic Setup](#basic-setup)
  - [Advanced Setup (with config)](#advanced-setup-with-config)
    - [Most Common](#most-common)
    - [Advanced usage](#advanced-usage)
- [For Repository Owners](#for-repository-owners)
- [Author](#author)
- [License](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## Introduction

[![GitHub Status](https://badgen.net/github/status/wei/pull?icon=github)](https://github.com/wei/pull)
[![TravisCI](https://badgen.net/travis/wei/pull?icon=travis&label=build)](https://travis-ci.com/wei/pull)
[![Codecov](https://badgen.net/codecov/c/github/wei/pull?icon=codecov)](https://codecov.io/gh/wei/pull)
[![Probot](https://badgen.net/badge/built%20with/probot/orange?icon=dependabot&cache=86400)](https://probot.github.io/)
[![JavaScript Style Guide](https://badgen.net/badge/code%20style/standard/f2a?cache=86400)](https://standardjs.com)
[![jest](https://facebook.github.io/jest/img/jest-badge.svg)](https://github.com/facebook/jest)
[![MIT License](https://badgen.net/badge/license/MIT/blue?cache=86400)](https://wei.mit-license.org)

> 🤖 a GitHub App built with [probot](https://github.com/probot/probot) that keeps your forks up-to-date with upstream via automated pull requests.

Trusted by [![Repository Count](https://badgen.net/https/raw.githack.com/pull-app/stats/master/badges/managing.plain.json?style=flat)](https://probot.github.io/apps/pull/) repositories, triggered [![Triggered #](https://badgen.net/runkit/pull-triggered-badge-5e55hqhkhmid?style=flat&label=)](https://github.com/issues?q=author%3Aapp%2Fpull).

_Can you help keep this open source service alive? **[💖 Please sponsor : )](https://prod.download/pull-readme-sponsor)**_


## Features

 - Ensure forks are updated.
 - Automatically integrate new changes from upstream.
 - Pull requests are created when upstreams are updated.
 - Automatically merge or hard reset pull requests to match upstream.
 - Add assignees and reviewers to pull requests.
 - Customize pull request label.
 - Honor branch protection rules.
 - Work well with pull request checks and reviews.

### Prerequisites
 - Upstream must be in the same fork network.
 - :warning: _Make a backup if you've made changes._

## Getting Started

**[⭐ Star this project](https://github.com/wei/pull)** (Highly recommended, starred users may receive priority over regular users)

### Basic Setup

 - Just install **[<img src="https://prod.download/pull-18h-svg" valign="bottom"/> Pull app](https://github.com/apps/pull)**.

Pull app will automatically watch and pull in upstream's default (master) branch to yours using **hard reset** every few hours. You can also manually [trigger](#trigger-manually) it anytime.

### Advanced Setup (with config)

 1. Create a new branch.
 2. Setup the new branch as default branch under repository Settings > Branches.
 3. Add `.github/pull.yml` to your default branch.

    #### Most Common
    (behaves the same as Basic Setup)
    ```yaml
    version: "1"
    rules:
      - base: master
        upstream: wei:master    # change `wei` to the owner of upstream repo
        mergeMethod: hardreset
    ```

    #### Advanced usage
    ```yaml
    version: "1"
    rules:                      # Array of rules
      - base: master            # Required. Target branch
        upstream: wei:master    # Required. Must be in the same fork network.
        mergeMethod: hardreset  # Optional, one of [none, merge, squash, rebase, hardreset], Default: none.
        mergeUnstable: false    # Optional, merge pull request even when the mergeable_state is not clean. Default: false
      - base: dev
        upstream: master        # Required. Can be a branch in the same forked repo.
        assignees:              # Optional
          - wei
        reviewers:              # Optional
          - wei
        conflictReviewers:      # Optional, on merge conflict assign a reviewer
          - wei
    label: ":arrow_heading_down: pull"  # Optional
    conflictLabel: "merge-conflict"     # Optional, on merge conflict assign a custom label, Default: merge-conflict
    ```

 4. Go to `https://pull.git.ci/check/${owner}/${repo}` to validate your `.github/pull.yml` (Public repos only). See [#234](https://github.com/wei/pull/issues/234) for another way to validate it.
 5. Install **[![<img src="https://prod.download/pull-18h-svg" valign="bottom"/> Pull](https://prod.download/pull-18h-svg) Pull app](https://github.com/apps/pull)**.

### Trigger manually

Go to `https://pull.git.ci/process/${owner}/${repo}` to manually trigger pull.
**Note:** Nothing will happen if your branch is already even with upstream.


## For Repository Owners

For the most common use case (a single `master` branch), you can just direct users to install Pull with no configurations.
If you need a more advanced setup (such as a `docs` branch in addition to `master`), consider adding `.github/pull.yml` to your repository pointing to yourself (see example). This will allow forks to install Pull and stay updated automatically.

Example (assuming `owner` is your user or organization name):
```yaml
version: "1"
rules:
  - base: master
    upstream: owner:master
    mergeMethod: hardreset
  - base: docs
    upstream: owner:docs
    mergeMethod: hardreset
```


## Author
[Wei He](https://github.com/wei) _github@weispot.com_


## License
[MIT](LICENSE)

<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8">

<!-- Begin Jekyll SEO tag v2.8.0 -->
<title>pull | 🤖 Keep your forks up-to-date via automated PRs</title>
<meta name="generator" content="Jekyll v3.9.3" />
<meta property="og:title" content="pull" />
<meta property="og:locale" content="en_US" />
<meta name="description" content="🤖 Keep your forks up-to-date via automated PRs" />
<meta property="og:description" content="🤖 Keep your forks up-to-date via automated PRs" />
<link rel="canonical" href="https://wei.github.io/pull/" />
<meta property="og:url" content="https://wei.github.io/pull/" />
<meta property="og:site_name" content="pull" />
<meta property="og:type" content="website" />
<meta name="twitter:card" content="summary" />
<meta property="twitter:title" content="pull" />
<script type="application/ld+json">
{"@context":"https://schema.org","@type":"WebSite","description":"🤖 Keep your forks up-to-date via automated PRs","headline":"pull","name":"pull","url":"https://wei.github.io/pull/"}</script>
<!-- End Jekyll SEO tag -->

    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link rel="preload" href="https://fonts.googleapis.com/css?family=Open+Sans:400,700&display=swap" as="style" type="text/css" crossorigin>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="theme-color" content="#157878">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <link rel="stylesheet" href="/pull/assets/css/style.css?v=95302f38ad37b88697a2095d8558bfc7ebcdfb6d">
    <!-- start custom head snippets, customize with your own _includes/head-custom.html file -->

<!-- Setup Google Analytics -->



<!-- You can set your favicon here -->
<!-- link rel="shortcut icon" type="image/x-icon" href="/pull/favicon.ico" -->

<!-- end custom head snippets -->

  </head>
  <body>
    <a id="skip-to-content" href="#content">Skip to the content.</a>

    <header class="page-header" role="banner">
      <h1 class="project-name">pull</h1>
      <h2 class="project-tagline">🤖 Keep your forks up-to-date via automated PRs</h2>
      
        <a href="https://github.com/wei/pull" class="btn">View on GitHub</a>
      
      
    </header>

    <main id="content" class="main-content" role="main">
      <p align="center">
  <a href="https://github.com/apps/pull">
    <img alt="Pull App" src="https://prod.download/pull-social-svg">
  </a>
</p>
<p align="center">
  <a href="https://probot.github.io">
    <img alt="Probot Featured" src="https://badgen.net/badge/probot/featured/orange?icon=dependabot&amp;cache=86400">
  </a>
  <a href="https://github.com/wei/pull">
    <img alt="GitHub Stars" src="https://badgen.net/github/stars/wei/pull?icon=github">
  </a>
  <br>
  <a href="https://github.com/apps/pull">
    <img alt="Managing" src="https://badgen.net/https/raw.githack.com/pull-app/stats/master/badges/managing.json">
  </a>
  <a href="https://github.com/apps/pull">
    <img alt="Installations" src="https://badgen.net/https/raw.githack.com/pull-app/stats/master/badges/installed.json">
  </a>
  <a href="https://github.com/issues?q=author%3Aapp%2Fpull">
    <img alt="Triggered #" src="https://badgen.net/runkit/pull-triggered-badge-5e55hqhkhmid">
  </a>
</p>

<h2>Table of Contents</h2>
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

<ul>
  <li><a href="#introduction">Introduction</a></li>
  <li>
<a href="#features">Features</a>
    <ul>
      <li><a href="#prerequisites">Prerequisites</a></li>
    </ul>
  </li>
  <li>
<a href="#getting-started">Getting Started</a>
    <ul>
      <li><a href="#basic-setup">Basic Setup</a></li>
      <li>
<a href="#advanced-setup-with-config">Advanced Setup (with config)</a>
        <ul>
          <li><a href="#most-common">Most Common</a></li>
          <li><a href="#advanced-usage">Advanced usage</a></li>
        </ul>
      </li>
    </ul>
  </li>
  <li><a href="#for-repository-owners">For Repository Owners</a></li>
  <li><a href="#author">Author</a></li>
  <li><a href="#license">License</a></li>
</ul>

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<h2 id="introduction">Introduction</h2>

<p><a href="https://github.com/wei/pull"><img src="https://badgen.net/github/status/wei/pull?icon=github" alt="GitHub Status"></a>
<a href="https://travis-ci.com/wei/pull"><img src="https://badgen.net/travis/wei/pull?icon=travis&amp;label=build" alt="TravisCI"></a>
<a href="https://codecov.io/gh/wei/pull"><img src="https://badgen.net/codecov/c/github/wei/pull?icon=codecov" alt="Codecov"></a>
<a href="https://probot.github.io/"><img src="https://badgen.net/badge/built%20with/probot/orange?icon=dependabot&amp;cache=86400" alt="Probot"></a>
<a href="https://standardjs.com"><img src="https://badgen.net/badge/code%20style/standard/f2a?cache=86400" alt="JavaScript Style Guide"></a>
<a href="https://github.com/facebook/jest"><img src="https://facebook.github.io/jest/img/jest-badge.svg" alt="jest"></a>
<a href="https://wei.mit-license.org"><img src="https://badgen.net/badge/license/MIT/blue?cache=86400" alt="MIT License"></a></p>

<blockquote>
  <p>🤖 a GitHub App built with <a href="https://github.com/probot/probot">probot</a> that keeps your forks up-to-date with upstream via automated pull requests.</p>
</blockquote>

<p>Trusted by <a href="https://probot.github.io/apps/pull/"><img src="https://badgen.net/https/raw.githack.com/pull-app/stats/master/badges/managing.plain.json?style=flat" alt="Repository Count"></a> repositories, triggered <a href="https://github.com/issues?q=author%3Aapp%2Fpull"><img src="https://badgen.net/runkit/pull-triggered-badge-5e55hqhkhmid?style=flat&amp;label=" alt="Triggered #"></a>.</p>

<p><em>Can you help keep this open source service alive? <strong><a href="https://prod.download/pull-readme-sponsor">💖 Please sponsor : )</a></strong></em></p>

<h2 id="features">Features</h2>

<ul>
  <li>Ensure forks are updated.</li>
  <li>Automatically integrate new changes from upstream.</li>
  <li>Pull requests are created when upstreams are updated.</li>
  <li>Automatically merge or hard reset pull requests to match upstream.</li>
  <li>Add assignees and reviewers to pull requests.</li>
  <li>Customize pull request label.</li>
  <li>Honor branch protection rules.</li>
  <li>Work well with pull request checks and reviews.</li>
</ul>

<h3 id="prerequisites">Prerequisites</h3>
<ul>
  <li>Upstream must be in the same fork network.</li>
  <li>
<img class="emoji" title=":warning:" alt=":warning:" src="https://github.githubassets.com/images/icons/emoji/unicode/26a0.png" height="20" width="20"> <em>Make a backup if you’ve made changes.</em>
</li>
</ul>

<h2 id="getting-started">Getting Started</h2>

<p><strong><a href="https://github.com/wei/pull">⭐ Star this project</a></strong> (Highly recommended, starred users may receive priority over regular users)</p>

<h3 id="basic-setup">Basic Setup</h3>

<ul>
  <li>Just install <strong><a href="https://github.com/apps/pull"><img src="https://prod.download/pull-18h-svg" valign="bottom"> Pull app</a></strong>.</li>
</ul>

<p>Pull app will automatically watch and pull in upstream’s default (master) branch to yours using <strong>hard reset</strong> every few hours. You can also manually <a href="#trigger-manually">trigger</a> it anytime.</p>

<h3 id="advanced-setup-with-config">Advanced Setup (with config)</h3>

<ol>
  <li>Create a new branch.</li>
  <li>Setup the new branch as default branch under repository Settings &gt; Branches.</li>
  <li>
    <p>Add <code class="language-plaintext highlighter-rouge">.github/pull.yml</code> to your default branch.</p>

    <h4 id="most-common">Most Common</h4>
    <p>(behaves the same as Basic Setup)</p>
    <div class="language-yaml highlighter-rouge">
<div class="highlight"><pre class="highlight"><code><span class="na">version</span><span class="pi">:</span> <span class="s2">"</span><span class="s">1"</span>
<span class="na">rules</span><span class="pi">:</span>
  <span class="pi">-</span> <span class="na">base</span><span class="pi">:</span> <span class="s">master</span>
    <span class="na">upstream</span><span class="pi">:</span> <span class="s">wei:master</span>    <span class="c1"># change `wei` to the owner of upstream repo</span>
    <span class="na">mergeMethod</span><span class="pi">:</span> <span class="s">hardreset</span>
</code></pre></div>    </div>

    <h4 id="advanced-usage">Advanced usage</h4>
    <div class="language-yaml highlighter-rouge">
<div class="highlight"><pre class="highlight"><code><span class="na">version</span><span class="pi">:</span> <span class="s2">"</span><span class="s">1"</span>
<span class="na">rules</span><span class="pi">:</span>                      <span class="c1"># Array of rules</span>
  <span class="pi">-</span> <span class="na">base</span><span class="pi">:</span> <span class="s">master</span>            <span class="c1"># Required. Target branch</span>
    <span class="na">upstream</span><span class="pi">:</span> <span class="s">wei:master</span>    <span class="c1"># Required. Must be in the same fork network.</span>
    <span class="na">mergeMethod</span><span class="pi">:</span> <span class="s">hardreset</span>  <span class="c1"># Optional, one of [none, merge, squash, rebase, hardreset], Default: none.</span>
    <span class="na">mergeUnstable</span><span class="pi">:</span> <span class="no">false</span>    <span class="c1"># Optional, merge pull request even when the mergeable_state is not clean. Default: false</span>
  <span class="pi">-</span> <span class="na">base</span><span class="pi">:</span> <span class="s">dev</span>
    <span class="na">upstream</span><span class="pi">:</span> <span class="s">master</span>        <span class="c1"># Required. Can be a branch in the same forked repo.</span>
    <span class="na">assignees</span><span class="pi">:</span>              <span class="c1"># Optional</span>
      <span class="pi">-</span> <span class="s">wei</span>
    <span class="na">reviewers</span><span class="pi">:</span>              <span class="c1"># Optional</span>
      <span class="pi">-</span> <span class="s">wei</span>
    <span class="na">conflictReviewers</span><span class="pi">:</span>      <span class="c1"># Optional, on merge conflict assign a reviewer</span>
      <span class="pi">-</span> <span class="s">wei</span>
<span class="na">label</span><span class="pi">:</span> <span class="s2">"</span><span class="s">:arrow_heading_down:</span><span class="nv"> </span><span class="s">pull"</span>  <span class="c1"># Optional</span>
<span class="na">conflictLabel</span><span class="pi">:</span> <span class="s2">"</span><span class="s">merge-conflict"</span>     <span class="c1"># Optional, on merge conflict assign a custom label, Default: merge-conflict</span>
</code></pre></div>    </div>
  </li>
  <li>Go to <code class="language-plaintext highlighter-rouge">https://pull.git.ci/check/${owner}/${repo}</code> to validate your <code class="language-plaintext highlighter-rouge">.github/pull.yml</code> (Public repos only). See <a href="https://github.com/wei/pull/issues/234">#234</a> for another way to validate it.</li>
  <li>Install <strong><a href="https://github.com/apps/pull"><img src="https://prod.download/pull-18h-svg" alt='&lt;img src="https://prod.download/pull-18h-svg" valign="bottom"/&gt; Pull'> Pull app</a></strong>.</li>
</ol>

<h3 id="trigger-manually">Trigger manually</h3>

<p>Go to <code class="language-plaintext highlighter-rouge">https://pull.git.ci/process/${owner}/${repo}</code> to manually trigger pull.
<strong>Note:</strong> Nothing will happen if your branch is already even with upstream.</p>

<h2 id="for-repository-owners">For Repository Owners</h2>

<p>For the most common use case (a single <code class="language-plaintext highlighter-rouge">master</code> branch), you can just direct users to install Pull with no configurations.
If you need a more advanced setup (such as a <code class="language-plaintext highlighter-rouge">docs</code> branch in addition to <code class="language-plaintext highlighter-rouge">master</code>), consider adding <code class="language-plaintext highlighter-rouge">.github/pull.yml</code> to your repository pointing to yourself (see example). This will allow forks to install Pull and stay updated automatically.</p>

<p>Example (assuming <code class="language-plaintext highlighter-rouge">owner</code> is your user or organization name):</p>
<div class="language-yaml highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="na">version</span><span class="pi">:</span> <span class="s2">"</span><span class="s">1"</span>
<span class="na">rules</span><span class="pi">:</span>
  <span class="pi">-</span> <span class="na">base</span><span class="pi">:</span> <span class="s">master</span>
    <span class="na">upstream</span><span class="pi">:</span> <span class="s">owner:master</span>
    <span class="na">mergeMethod</span><span class="pi">:</span> <span class="s">hardreset</span>
  <span class="pi">-</span> <span class="na">base</span><span class="pi">:</span> <span class="s">docs</span>
    <span class="na">upstream</span><span class="pi">:</span> <span class="s">owner:docs</span>
    <span class="na">mergeMethod</span><span class="pi">:</span> <span class="s">hardreset</span>
</code></pre></div></div>

<h2 id="author">Author</h2>
<p><a href="https://github.com/wei">Wei He</a> <em>github@weispot.com</em></p>

<h2 id="license">License</h2>
<p><a href="/pull/LICENSE">MIT</a></p>


      <footer class="site-footer">
        
          <span class="site-footer-owner"><a href="https://github.com/wei/pull">pull</a> is maintained by <a href="https://github.com/wei">wei</a>.</span>
        
        <span class="site-footer-credits">This page was generated by <a href="https://pages.github.com">GitHub Pages</a>.</span>
      </footer>
    </main>
  </body>
</html>

<!doctype html>
<html lang="fr-FR">
<head>
	<meta charset="UTF-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1" />
	<link rel="profile" href="https://gmpg.org/xfn/11" />
	<title>#coder &#8211; phytosanitary products by Start Export</title>
<meta name='robots' content='max-image-preview:large' />
<link rel='dns-prefetch' href='//s0.wp.com' />
<link rel='dns-prefetch' href='//wordpress.com' />
<link rel='dns-prefetch' href='//fonts-api.wp.com' />
<link rel='dns-prefetch' href='//s.pubmine.com' />
<link rel='dns-prefetch' href='//x.bidswitch.net' />
<link rel='dns-prefetch' href='//static.criteo.net' />
<link rel='dns-prefetch' href='//ib.adnxs.com' />
<link rel='dns-prefetch' href='//aax.amazon-adsystem.com' />
<link rel='dns-prefetch' href='//bidder.criteo.com' />
<link rel='dns-prefetch' href='//cas.criteo.com' />
<link rel='dns-prefetch' href='//gum.criteo.com' />
<link rel='dns-prefetch' href='//ads.pubmatic.com' />
<link rel='dns-prefetch' href='//gads.pubmatic.com' />
<link rel='dns-prefetch' href='//tpc.googlesyndication.com' />
<link rel='dns-prefetch' href='//ad.doubleclick.net' />
<link rel='dns-prefetch' href='//googleads.g.doubleclick.net' />
<link rel='dns-prefetch' href='//www.googletagservices.com' />
<link rel='dns-prefetch' href='//cdn.switchadhub.com' />
<link rel='dns-prefetch' href='//delivery.g.switchadhub.com' />
<link rel='dns-prefetch' href='//delivery.swid.switchadhub.com' />
<link rel='dns-prefetch' href='//a.teads.tv' />
<link rel='dns-prefetch' href='//prebid.media.net' />
<link rel='dns-prefetch' href='//adserver-us.adtech.advertising.com' />
<link rel='dns-prefetch' href='//fastlane.rubiconproject.com' />
<link rel='dns-prefetch' href='//prebid-server.rubiconproject.com' />
<link rel='dns-prefetch' href='//hb-api.omnitagjs.com' />
<link rel='dns-prefetch' href='//mtrx.go.sonobi.com' />
<link rel='dns-prefetch' href='//apex.go.sonobi.com' />
<link rel='dns-prefetch' href='//u.openx.net' />
<link rel="alternate" type="application/rss+xml" title="phytosanitary products by Start Export &raquo; Flux" href="https://importdotexport.wordpress.com/feed/" />
<link rel="alternate" type="application/rss+xml" title="phytosanitary products by Start Export &raquo; Flux des commentaires" href="https://importdotexport.wordpress.com/comments/feed/" />
<link rel="alternate" type="application/rss+xml" title="phytosanitary products by Start Export &raquo; #coder Flux des commentaires" href="https://importdotexport.wordpress.com/2024/01/11/coder/feed/" />
	<script type="text/javascript">
		/* <![CDATA[ */
		function addLoadEvent(func) {
			var oldonload = window.onload;
			if (typeof window.onload != 'function') {
				window.onload = func;
			} else {
				window.onload = function () {
					oldonload();
					func();
				}
			}
		}
		/* ]]> */
	</script>
	<script type="text/javascript">
/* <![CDATA[ */
window._wpemojiSettings = {"baseUrl":"https:\/\/s0.wp.com\/wp-content\/mu-plugins\/wpcom-smileys\/twemoji\/2\/72x72\/","ext":".png","svgUrl":"https:\/\/s0.wp.com\/wp-content\/mu-plugins\/wpcom-smileys\/twemoji\/2\/svg\/","svgExt":".svg","source":{"concatemoji":"https:\/\/s0.wp.com\/wp-includes\/js\/wp-emoji-release.min.js?m=1677072837i&ver=6.5-alpha-57239"}};
/*! This file is auto-generated */
!function(i,n){var o,s,e;function c(e){try{var t={supportTests:e,timestamp:(new Date).valueOf()};sessionStorage.setItem(o,JSON.stringify(t))}catch(e){}}function p(e,t,n){e.clearRect(0,0,e.canvas.width,e.canvas.height),e.fillText(t,0,0);var t=new Uint32Array(e.getImageData(0,0,e.canvas.width,e.canvas.height).data),r=(e.clearRect(0,0,e.canvas.width,e.canvas.height),e.fillText(n,0,0),new Uint32Array(e.getImageData(0,0,e.canvas.width,e.canvas.height).data));return t.every(function(e,t){return e===r[t]})}function u(e,t,n){switch(t){case"flag":return n(e,"\ud83c\udff3\ufe0f\u200d\u26a7\ufe0f","\ud83c\udff3\ufe0f\u200b\u26a7\ufe0f")?!1:!n(e,"\ud83c\uddfa\ud83c\uddf3","\ud83c\uddfa\u200b\ud83c\uddf3")&&!n(e,"\ud83c\udff4\udb40\udc67\udb40\udc62\udb40\udc65\udb40\udc6e\udb40\udc67\udb40\udc7f","\ud83c\udff4\u200b\udb40\udc67\u200b\udb40\udc62\u200b\udb40\udc65\u200b\udb40\udc6e\u200b\udb40\udc67\u200b\udb40\udc7f");case"emoji":return!n(e,"\ud83e\udef1\ud83c\udffb\u200d\ud83e\udef2\ud83c\udfff","\ud83e\udef1\ud83c\udffb\u200b\ud83e\udef2\ud83c\udfff")}return!1}function f(e,t,n){var r="undefined"!=typeof WorkerGlobalScope&&self instanceof WorkerGlobalScope?new OffscreenCanvas(300,150):i.createElement("canvas"),a=r.getContext("2d",{willReadFrequently:!0}),o=(a.textBaseline="top",a.font="600 32px Arial",{});return e.forEach(function(e){o[e]=t(a,e,n)}),o}function t(e){var t=i.createElement("script");t.src=e,t.defer=!0,i.head.appendChild(t)}"undefined"!=typeof Promise&&(o="wpEmojiSettingsSupports",s=["flag","emoji"],n.supports={everything:!0,everythingExceptFlag:!0},e=new Promise(function(e){i.addEventListener("DOMContentLoaded",e,{once:!0})}),new Promise(function(t){var n=function(){try{var e=JSON.parse(sessionStorage.getItem(o));if("object"==typeof e&&"number"==typeof e.timestamp&&(new Date).valueOf()<e.timestamp+604800&&"object"==typeof e.supportTests)return e.supportTests}catch(e){}return null}();if(!n){if("undefined"!=typeof Worker&&"undefined"!=typeof OffscreenCanvas&&"undefined"!=typeof URL&&URL.createObjectURL&&"undefined"!=typeof Blob)try{var e="postMessage("+f.toString()+"("+[JSON.stringify(s),u.toString(),p.toString()].join(",")+"));",r=new Blob([e],{type:"text/javascript"}),a=new Worker(URL.createObjectURL(r),{name:"wpTestEmojiSupports"});return void(a.onmessage=function(e){c(n=e.data),a.terminate(),t(n)})}catch(e){}c(n=f(s,u,p))}t(n)}).then(function(e){for(var t in e)n.supports[t]=e[t],n.supports.everything=n.supports.everything&&n.supports[t],"flag"!==t&&(n.supports.everythingExceptFlag=n.supports.everythingExceptFlag&&n.supports[t]);n.supports.everythingExceptFlag=n.supports.everythingExceptFlag&&!n.supports.flag,n.DOMReady=!1,n.readyCallback=function(){n.DOMReady=!0}}).then(function(){return e}).then(function(){var e;n.supports.everything||(n.readyCallback(),(e=n.source||{}).concatemoji?t(e.concatemoji):e.wpemoji&&e.twemoji&&(t(e.twemoji),t(e.wpemoji)))}))}((window,document),window._wpemojiSettings);
/* ]]> */
</script>
<link crossorigin='anonymous' rel='stylesheet' id='all-css-0-1' href='https://s0.wp.com/_static/??-eJx9kMsOgjAQRX/IOhhJ0IXxWwqd1ML0EWYa4t9biBHRhOV9ncWFKakuBsEg0FK0KlG2LjBMcTTaMFiKraZjx3yAr67Pa9MZi8KAuaRxcKhITyDoE2lBBpYn4R6gR0m6G94aOAfw0WQq2xFnhlEpsvyoPSK5AVfuoj51FzrKpsTFAKP54QqAj96FP+LmEK/HAcUFq1o9LuONM4/v/nZqqvp8rZpL3b8AuhOB9w==&cssminify=yes' type='text/css' media='all' />
<style id='wp-emoji-styles-inline-css'>

	img.wp-smiley, img.emoji {
		display: inline !important;
		border: none !important;
		box-shadow: none !important;
		height: 1em !important;
		width: 1em !important;
		margin: 0 0.07em !important;
		vertical-align: -0.1em !important;
		background: none !important;
		padding: 0 !important;
	}
</style>
<link crossorigin='anonymous' rel='stylesheet' id='all-css-2-1' href='https://s0.wp.com/_static/??-eJylzFsKgCAQQNENlZMhZB/RWtIGsyYVH4W7L9pCn5cLB+7Qau8yugyBirEugSlvKozmPRHh4gMTjIMqllZQ5PXRklVxiRVSroRMp9TAPyhveH7QfE586ITsxSjl/gAmEzhj&cssminify=yes' type='text/css' media='all' />
<style id='wp-block-library-inline-css'>
.has-text-align-justify {
	text-align:justify;
}
.wp-block-cover__image-background.has-parallax {
	background-size: cover;
}
</style>
<link crossorigin='anonymous' rel='stylesheet' id='all-css-4-1' href='https://s0.wp.com/_static/??-eJyVjV0OwiAQBi8kEKrR+mA8C4UN2br8hAVNby8mprEvGh8n+82semSB0VJzwGpmFcChAYIAsW4gk1mgCAJv7CIDRmmZd+qb3m+fvJFsivW1ydQ8Rla+dZygeDFRsrceg5qNvYn+NrUqfEGnuC4E/yeKqRg9/9BtemuD1KPUgjFkAlHgLg/KIdd1IdbQNVz0cdTjfhjOp/kJMmh7kg==&cssminify=yes' type='text/css' media='all' />
<style id='classic-theme-styles-inline-css'>
/*! This file is auto-generated */
.wp-block-button__link{color:#fff;background-color:#32373c;border-radius:9999px;box-shadow:none;text-decoration:none;padding:calc(.667em + 2px) calc(1.333em + 2px);font-size:1.125em}.wp-block-file__button{background:#32373c;color:#fff;text-decoration:none}
</style>
<link crossorigin='anonymous' rel='stylesheet' id='all-css-6-1' href='https://s0.wp.com/_static/??-eJx9jdsKwjAMhl/IGMXJ2IX4LD0EjSxtaVLn49sx2JV4E3L4vvy4FAg5GSVDaVDm9uCk6KJwAu8qLiVkgX0+BtUDMqZs3D3dm+3w+1vIlfpeirOVEIrsaCbp2D9ti/a+VFKFXoWbgD27+DfuTdU3wchqyCnSZ4XvcjuPp2EaL9NwfX0BBGxbqQ==&cssminify=yes' type='text/css' media='all' />
<style id='wpcom-admin-bar-inline-css'>

		@media screen { html { margin-top: 32px !important; } }
		@media screen and ( max-width: 782px ) { html { margin-top: 46px !important; } }
	
@media print { #wpadminbar { display:none; } }

			.admin-bar {
				position: inherit !important;
				top: auto !important;
			}
			.admin-bar .goog-te-banner-frame {
				top: 32px !important
			}
			@media screen and (max-width: 782px) {
				.admin-bar .goog-te-banner-frame {
					top: 46px !important;
				}
			}
			@media screen and (max-width: 480px) {
				.admin-bar .goog-te-banner-frame {
					position: absolute;
				}
			}
		
</style>
<style id='global-styles-inline-css'>
body{--wp--preset--color--black: #000000;--wp--preset--color--cyan-bluish-gray: #abb8c3;--wp--preset--color--white: #ffffff;--wp--preset--color--pale-pink: #f78da7;--wp--preset--color--vivid-red: #cf2e2e;--wp--preset--color--luminous-vivid-orange: #ff6900;--wp--preset--color--luminous-vivid-amber: #fcb900;--wp--preset--color--light-green-cyan: #7bdcb5;--wp--preset--color--vivid-green-cyan: #00d084;--wp--preset--color--pale-cyan-blue: #8ed1fc;--wp--preset--color--vivid-cyan-blue: #0693e3;--wp--preset--color--vivid-purple: #9b51e0;--wp--preset--color--primary: #CD2220;--wp--preset--color--secondary: #007AB7;--wp--preset--color--foreground: #303030;--wp--preset--color--background: #FFFFFF;--wp--preset--gradient--vivid-cyan-blue-to-vivid-purple: linear-gradient(135deg,rgba(6,147,227,1) 0%,rgb(155,81,224) 100%);--wp--preset--gradient--light-green-cyan-to-vivid-green-cyan: linear-gradient(135deg,rgb(122,220,180) 0%,rgb(0,208,130) 100%);--wp--preset--gradient--luminous-vivid-amber-to-luminous-vivid-orange: linear-gradient(135deg,rgba(252,185,0,1) 0%,rgba(255,105,0,1) 100%);--wp--preset--gradient--luminous-vivid-orange-to-vivid-red: linear-gradient(135deg,rgba(255,105,0,1) 0%,rgb(207,46,46) 100%);--wp--preset--gradient--very-light-gray-to-cyan-bluish-gray: linear-gradient(135deg,rgb(238,238,238) 0%,rgb(169,184,195) 100%);--wp--preset--gradient--cool-to-warm-spectrum: linear-gradient(135deg,rgb(74,234,220) 0%,rgb(151,120,209) 20%,rgb(207,42,186) 40%,rgb(238,44,130) 60%,rgb(251,105,98) 80%,rgb(254,248,76) 100%);--wp--preset--gradient--blush-light-purple: linear-gradient(135deg,rgb(255,206,236) 0%,rgb(152,150,240) 100%);--wp--preset--gradient--blush-bordeaux: linear-gradient(135deg,rgb(254,205,165) 0%,rgb(254,45,45) 50%,rgb(107,0,62) 100%);--wp--preset--gradient--luminous-dusk: linear-gradient(135deg,rgb(255,203,112) 0%,rgb(199,81,192) 50%,rgb(65,88,208) 100%);--wp--preset--gradient--pale-ocean: linear-gradient(135deg,rgb(255,245,203) 0%,rgb(182,227,212) 50%,rgb(51,167,181) 100%);--wp--preset--gradient--electric-grass: linear-gradient(135deg,rgb(202,248,128) 0%,rgb(113,206,126) 100%);--wp--preset--gradient--midnight: linear-gradient(135deg,rgb(2,3,129) 0%,rgb(40,116,252) 100%);--wp--preset--font-size--small: 16.6px;--wp--preset--font-size--medium: 20px;--wp--preset--font-size--large: 26.45px;--wp--preset--font-size--x-large: 42px;--wp--preset--font-size--normal: 20px;--wp--preset--font-size--huge: 30.4174px;--wp--preset--font-family--albert-sans: 'Albert Sans', sans-serif;--wp--preset--font-family--alegreya: Alegreya, serif;--wp--preset--font-family--arvo: Arvo, serif;--wp--preset--font-family--bodoni-moda: 'Bodoni Moda', serif;--wp--preset--font-family--cabin: Cabin, sans-serif;--wp--preset--font-family--chivo: Chivo, sans-serif;--wp--preset--font-family--commissioner: Commissioner, sans-serif;--wp--preset--font-family--cormorant: Cormorant, serif;--wp--preset--font-family--courier-prime: 'Courier Prime', monospace;--wp--preset--font-family--crimson-pro: 'Crimson Pro', serif;--wp--preset--font-family--dm-mono: 'DM Mono', monospace;--wp--preset--font-family--dm-sans: 'DM Sans', sans-serif;--wp--preset--font-family--domine: Domine, serif;--wp--preset--font-family--eb-garamond: 'EB Garamond', serif;--wp--preset--font-family--epilogue: Epilogue, sans-serif;--wp--preset--font-family--figtree: Figtree, sans-serif;--wp--preset--font-family--fira-sans: 'Fira Sans', sans-serif;--wp--preset--font-family--fraunces: Fraunces, serif;--wp--preset--font-family--ibm-plex-mono: 'IBM Plex Mono', monospace;--wp--preset--font-family--ibm-plex-sans: 'IBM Plex Sans', sans-serif;--wp--preset--font-family--inter: Inter, sans-serif;--wp--preset--font-family--josefin-sans: 'Josefin Sans', sans-serif;--wp--preset--font-family--jost: Jost, sans-serif;--wp--preset--font-family--libre-baskerville: 'Libre Baskerville', serif;--wp--preset--font-family--libre-franklin: 'Libre Franklin', sans-serif;--wp--preset--font-family--literata: Literata, serif;--wp--preset--font-family--lora: Lora, serif;--wp--preset--font-family--merriweather: Merriweather, serif;--wp--preset--font-family--montserrat: Montserrat, sans-serif;--wp--preset--font-family--newsreader: Newsreader, serif;--wp--preset--font-family--nunito: Nunito, sans-serif;--wp--preset--font-family--open-sans: 'Open Sans', sans-serif;--wp--preset--font-family--overpass: Overpass, sans-serif;--wp--preset--font-family--petrona: Petrona, serif;--wp--preset--font-family--piazzolla: Piazzolla, serif;--wp--preset--font-family--playfair-display: 'Playfair Display', serif;--wp--preset--font-family--plus-jakarta-sans: 'Plus Jakarta Sans', sans-serif;--wp--preset--font-family--poppins: Poppins, sans-serif;--wp--preset--font-family--raleway: Raleway, sans-serif;--wp--preset--font-family--roboto: Roboto, sans-serif;--wp--preset--font-family--roboto-slab: 'Roboto Slab', serif;--wp--preset--font-family--rubik: Rubik, sans-serif;--wp--preset--font-family--sora: Sora, sans-serif;--wp--preset--font-family--source-sans-3: 'Source Sans 3', sans-serif;--wp--preset--font-family--source-serif-4: 'Source Serif 4', serif;--wp--preset--font-family--space-mono: 'Space Mono', monospace;--wp--preset--font-family--texturina: Texturina, serif;--wp--preset--font-family--work-sans: 'Work Sans', sans-serif;--wp--preset--spacing--20: 0.44rem;--wp--preset--spacing--30: 0.67rem;--wp--preset--spacing--40: 1rem;--wp--preset--spacing--50: 1.5rem;--wp--preset--spacing--60: 2.25rem;--wp--preset--spacing--70: 3.38rem;--wp--preset--spacing--80: 5.06rem;--wp--preset--shadow--natural: 6px 6px 9px rgba(0, 0, 0, 0.2);--wp--preset--shadow--deep: 12px 12px 50px rgba(0, 0, 0, 0.4);--wp--preset--shadow--sharp: 6px 6px 0px rgba(0, 0, 0, 0.2);--wp--preset--shadow--outlined: 6px 6px 0px -3px rgba(255, 255, 255, 1), 6px 6px rgba(0, 0, 0, 1);--wp--preset--shadow--crisp: 6px 6px 0px rgba(0, 0, 0, 1);}:where(body .is-layout-flow)  > :first-child:first-child{margin-block-start: 0;}:where(body .is-layout-flow)  > :last-child:last-child{margin-block-end: 0;}:where(body .is-layout-flow)  > *{margin-block-start: 24px;margin-block-end: 0;}:where(body .is-layout-constrained)  > :first-child:first-child{margin-block-start: 0;}:where(body .is-layout-constrained)  > :last-child:last-child{margin-block-end: 0;}:where(body .is-layout-constrained)  > *{margin-block-start: 24px;margin-block-end: 0;}:where(body .is-layout-flex) {gap: 24px;}:where(body .is-layout-grid) {gap: 24px;}body .is-layout-flow > .alignleft{float: left;margin-inline-start: 0;margin-inline-end: 2em;}body .is-layout-flow > .alignright{float: right;margin-inline-start: 2em;margin-inline-end: 0;}body .is-layout-flow > .aligncenter{margin-left: auto !important;margin-right: auto !important;}body .is-layout-constrained > .alignleft{float: left;margin-inline-start: 0;margin-inline-end: 2em;}body .is-layout-constrained > .alignright{float: right;margin-inline-start: 2em;margin-inline-end: 0;}body .is-layout-constrained > .aligncenter{margin-left: auto !important;margin-right: auto !important;}body .is-layout-constrained > :where(:not(.alignleft):not(.alignright):not(.alignfull)){max-width: var(--wp--style--global--content-size);margin-left: auto !important;margin-right: auto !important;}body .is-layout-constrained > .alignwide{max-width: var(--wp--style--global--wide-size);}body .is-layout-flex{display: flex;}body .is-layout-flex{flex-wrap: wrap;align-items: center;}body .is-layout-flex > *{margin: 0;}body .is-layout-grid{display: grid;}body .is-layout-grid > *{margin: 0;}.has-black-color{color: var(--wp--preset--color--black) !important;}.has-cyan-bluish-gray-color{color: var(--wp--preset--color--cyan-bluish-gray) !important;}.has-white-color{color: var(--wp--preset--color--white) !important;}.has-pale-pink-color{color: var(--wp--preset--color--pale-pink) !important;}.has-vivid-red-color{color: var(--wp--preset--color--vivid-red) !important;}.has-luminous-vivid-orange-color{color: var(--wp--preset--color--luminous-vivid-orange) !important;}.has-luminous-vivid-amber-color{color: var(--wp--preset--color--luminous-vivid-amber) !important;}.has-light-green-cyan-color{color: var(--wp--preset--color--light-green-cyan) !important;}.has-vivid-green-cyan-color{color: var(--wp--preset--color--vivid-green-cyan) !important;}.has-pale-cyan-blue-color{color: var(--wp--preset--color--pale-cyan-blue) !important;}.has-vivid-cyan-blue-color{color: var(--wp--preset--color--vivid-cyan-blue) !important;}.has-vivid-purple-color{color: var(--wp--preset--color--vivid-purple) !important;}.has-primary-color{color: var(--wp--preset--color--primary) !important;}.has-secondary-color{color: var(--wp--preset--color--secondary) !important;}.has-foreground-color{color: var(--wp--preset--color--foreground) !important;}.has-background-color{color: var(--wp--preset--color--background) !important;}.has-black-background-color{background-color: var(--wp--preset--color--black) !important;}.has-cyan-bluish-gray-background-color{background-color: var(--wp--preset--color--cyan-bluish-gray) !important;}.has-white-background-color{background-color: var(--wp--preset--color--white) !important;}.has-pale-pink-background-color{background-color: var(--wp--preset--color--pale-pink) !important;}.has-vivid-red-background-color{background-color: var(--wp--preset--color--vivid-red) !important;}.has-luminous-vivid-orange-background-color{background-color: var(--wp--preset--color--luminous-vivid-orange) !important;}.has-luminous-vivid-amber-background-color{background-color: var(--wp--preset--color--luminous-vivid-amber) !important;}.has-light-green-cyan-background-color{background-color: var(--wp--preset--color--light-green-cyan) !important;}.has-vivid-green-cyan-background-color{background-color: var(--wp--preset--color--vivid-green-cyan) !important;}.has-pale-cyan-blue-background-color{background-color: var(--wp--preset--color--pale-cyan-blue) !important;}.has-vivid-cyan-blue-background-color{background-color: var(--wp--preset--color--vivid-cyan-blue) !important;}.has-vivid-purple-background-color{background-color: var(--wp--preset--color--vivid-purple) !important;}.has-primary-background-color{background-color: var(--wp--preset--color--primary) !important;}.has-secondary-background-color{background-color: var(--wp--preset--color--secondary) !important;}.has-foreground-background-color{background-color: var(--wp--preset--color--foreground) !important;}.has-background-background-color{background-color: var(--wp--preset--color--background) !important;}.has-black-border-color{border-color: var(--wp--preset--color--black) !important;}.has-cyan-bluish-gray-border-color{border-color: var(--wp--preset--color--cyan-bluish-gray) !important;}.has-white-border-color{border-color: var(--wp--preset--color--white) !important;}.has-pale-pink-border-color{border-color: var(--wp--preset--color--pale-pink) !important;}.has-vivid-red-border-color{border-color: var(--wp--preset--color--vivid-red) !important;}.has-luminous-vivid-orange-border-color{border-color: var(--wp--preset--color--luminous-vivid-orange) !important;}.has-luminous-vivid-amber-border-color{border-color: var(--wp--preset--color--luminous-vivid-amber) !important;}.has-light-green-cyan-border-color{border-color: var(--wp--preset--color--light-green-cyan) !important;}.has-vivid-green-cyan-border-color{border-color: var(--wp--preset--color--vivid-green-cyan) !important;}.has-pale-cyan-blue-border-color{border-color: var(--wp--preset--color--pale-cyan-blue) !important;}.has-vivid-cyan-blue-border-color{border-color: var(--wp--preset--color--vivid-cyan-blue) !important;}.has-vivid-purple-border-color{border-color: var(--wp--preset--color--vivid-purple) !important;}.has-primary-border-color{border-color: var(--wp--preset--color--primary) !important;}.has-secondary-border-color{border-color: var(--wp--preset--color--secondary) !important;}.has-foreground-border-color{border-color: var(--wp--preset--color--foreground) !important;}.has-background-border-color{border-color: var(--wp--preset--color--background) !important;}.has-vivid-cyan-blue-to-vivid-purple-gradient-background{background: var(--wp--preset--gradient--vivid-cyan-blue-to-vivid-purple) !important;}.has-light-green-cyan-to-vivid-green-cyan-gradient-background{background: var(--wp--preset--gradient--light-green-cyan-to-vivid-green-cyan) !important;}.has-luminous-vivid-amber-to-luminous-vivid-orange-gradient-background{background: var(--wp--preset--gradient--luminous-vivid-amber-to-luminous-vivid-orange) !important;}.has-luminous-vivid-orange-to-vivid-red-gradient-background{background: var(--wp--preset--gradient--luminous-vivid-orange-to-vivid-red) !important;}.has-very-light-gray-to-cyan-bluish-gray-gradient-background{background: var(--wp--preset--gradient--very-light-gray-to-cyan-bluish-gray) !important;}.has-cool-to-warm-spectrum-gradient-background{background: var(--wp--preset--gradient--cool-to-warm-spectrum) !important;}.has-blush-light-purple-gradient-background{background: var(--wp--preset--gradient--blush-light-purple) !important;}.has-blush-bordeaux-gradient-background{background: var(--wp--preset--gradient--blush-bordeaux) !important;}.has-luminous-dusk-gradient-background{background: var(--wp--preset--gradient--luminous-dusk) !important;}.has-pale-ocean-gradient-background{background: var(--wp--preset--gradient--pale-ocean) !important;}.has-electric-grass-gradient-background{background: var(--wp--preset--gradient--electric-grass) !important;}.has-midnight-gradient-background{background: var(--wp--preset--gradient--midnight) !important;}.has-small-font-size{font-size: var(--wp--preset--font-size--small) !important;}.has-medium-font-size{font-size: var(--wp--preset--font-size--medium) !important;}.has-large-font-size{font-size: var(--wp--preset--font-size--large) !important;}.has-x-large-font-size{font-size: var(--wp--preset--font-size--x-large) !important;}.has-normal-font-size{font-size: var(--wp--preset--font-size--normal) !important;}.has-huge-font-size{font-size: var(--wp--preset--font-size--huge) !important;}.has-albert-sans-font-family{font-family: var(--wp--preset--font-family--albert-sans) !important;}.has-alegreya-font-family{font-family: var(--wp--preset--font-family--alegreya) !important;}.has-arvo-font-family{font-family: var(--wp--preset--font-family--arvo) !important;}.has-bodoni-moda-font-family{font-family: var(--wp--preset--font-family--bodoni-moda) !important;}.has-cabin-font-family{font-family: var(--wp--preset--font-family--cabin) !important;}.has-chivo-font-family{font-family: var(--wp--preset--font-family--chivo) !important;}.has-commissioner-font-family{font-family: var(--wp--preset--font-family--commissioner) !important;}.has-cormorant-font-family{font-family: var(--wp--preset--font-family--cormorant) !important;}.has-courier-prime-font-family{font-family: var(--wp--preset--font-family--courier-prime) !important;}.has-crimson-pro-font-family{font-family: var(--wp--preset--font-family--crimson-pro) !important;}.has-dm-mono-font-family{font-family: var(--wp--preset--font-family--dm-mono) !important;}.has-dm-sans-font-family{font-family: var(--wp--preset--font-family--dm-sans) !important;}.has-domine-font-family{font-family: var(--wp--preset--font-family--domine) !important;}.has-eb-garamond-font-family{font-family: var(--wp--preset--font-family--eb-garamond) !important;}.has-epilogue-font-family{font-family: var(--wp--preset--font-family--epilogue) !important;}.has-figtree-font-family{font-family: var(--wp--preset--font-family--figtree) !important;}.has-fira-sans-font-family{font-family: var(--wp--preset--font-family--fira-sans) !important;}.has-fraunces-font-family{font-family: var(--wp--preset--font-family--fraunces) !important;}.has-ibm-plex-mono-font-family{font-family: var(--wp--preset--font-family--ibm-plex-mono) !important;}.has-ibm-plex-sans-font-family{font-family: var(--wp--preset--font-family--ibm-plex-sans) !important;}.has-inter-font-family{font-family: var(--wp--preset--font-family--inter) !important;}.has-josefin-sans-font-family{font-family: var(--wp--preset--font-family--josefin-sans) !important;}.has-jost-font-family{font-family: var(--wp--preset--font-family--jost) !important;}.has-libre-baskerville-font-family{font-family: var(--wp--preset--font-family--libre-baskerville) !important;}.has-libre-franklin-font-family{font-family: var(--wp--preset--font-family--libre-franklin) !important;}.has-literata-font-family{font-family: var(--wp--preset--font-family--literata) !important;}.has-lora-font-family{font-family: var(--wp--preset--font-family--lora) !important;}.has-merriweather-font-family{font-family: var(--wp--preset--font-family--merriweather) !important;}.has-montserrat-font-family{font-family: var(--wp--preset--font-family--montserrat) !important;}.has-newsreader-font-family{font-family: var(--wp--preset--font-family--newsreader) !important;}.has-nunito-font-family{font-family: var(--wp--preset--font-family--nunito) !important;}.has-open-sans-font-family{font-family: var(--wp--preset--font-family--open-sans) !important;}.has-overpass-font-family{font-family: var(--wp--preset--font-family--overpass) !important;}.has-petrona-font-family{font-family: var(--wp--preset--font-family--petrona) !important;}.has-piazzolla-font-family{font-family: var(--wp--preset--font-family--piazzolla) !important;}.has-playfair-display-font-family{font-family: var(--wp--preset--font-family--playfair-display) !important;}.has-plus-jakarta-sans-font-family{font-family: var(--wp--preset--font-family--plus-jakarta-sans) !important;}.has-poppins-font-family{font-family: var(--wp--preset--font-family--poppins) !important;}.has-raleway-font-family{font-family: var(--wp--preset--font-family--raleway) !important;}.has-roboto-font-family{font-family: var(--wp--preset--font-family--roboto) !important;}.has-roboto-slab-font-family{font-family: var(--wp--preset--font-family--roboto-slab) !important;}.has-rubik-font-family{font-family: var(--wp--preset--font-family--rubik) !important;}.has-sora-font-family{font-family: var(--wp--preset--font-family--sora) !important;}.has-source-sans-3-font-family{font-family: var(--wp--preset--font-family--source-sans-3) !important;}.has-source-serif-4-font-family{font-family: var(--wp--preset--font-family--source-serif-4) !important;}.has-space-mono-font-family{font-family: var(--wp--preset--font-family--space-mono) !important;}.has-texturina-font-family{font-family: var(--wp--preset--font-family--texturina) !important;}.has-work-sans-font-family{font-family: var(--wp--preset--font-family--work-sans) !important;}
.wp-block-pullquote{font-size: 1.5em;line-height: 1.6;}
.wp-block-navigation a:where(:not(.wp-element-button)){color: inherit;}
</style>
<link crossorigin='anonymous' rel='stylesheet' id='all-css-8-1' href='https://s0.wp.com/wp-content/mu-plugins/comment-likes/css/comment-likes.css?m=1407378799i&cssminify=yes' type='text/css' media='all' />
<link crossorigin='anonymous' rel='stylesheet' id='print-css-9-1' href='https://s0.wp.com/wp-content/themes/pub/varia/print.css?m=1571655471i&cssminify=yes' type='text/css' media='print' />
<link crossorigin='anonymous' rel='stylesheet' id='all-css-10-1' href='https://s0.wp.com/_static/??-eJx9jcsKwjAQRX/IcUgphS7Eb0nSMUaSmZBHS//eiBtF6e4eOIeLWwIrXIkr1jtFKpiawSh5IcZS90BnW8oJ/3urzl6jZ/tWYUtW4k8QG6TQnOeCjgSCWF298BfALWifj1KW2l/1Ej2D0RnW4cjOZIK4Ph126wNf0TVe1DSrcVbDOD2e3qhgGA==&cssminify=yes' type='text/css' media='all' />
<link rel='stylesheet' id='morden-fonts-css' href='https://fonts-api.wp.com/css?family=Noto+Sans%3A400%2C400i%2C700%2C700i&#038;subset=latin%2Clatin-ext' media='all' />
<link crossorigin='anonymous' rel='stylesheet' id='all-css-12-1' href='https://s0.wp.com/_static/??/wp-content/themes/pub/morden/style.css,/wp-content/mu-plugins/admin-bar/masterbar-overrides/masterbar.css?m=1704807416j&cssminify=yes' type='text/css' media='all' />
<style id='jetpack-global-styles-frontend-style-inline-css'>
@import url('https://fonts-api.wp.com/css?family=Roboto:thin,extralight,light,regular,medium,semibold,bold,italic,bolditalic,extrabold,black|Libre Franklin:thin,extralight,light,regular,medium,semibold,bold,italic,bolditalic,extrabold,black|');:root { --font-headings: Libre Franklin; --font-base: Roboto; --font-headings-default: -apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Oxygen-Sans,Ubuntu,Cantarell,"Helvetica Neue",sans-serif; --font-base-default: -apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Oxygen-Sans,Ubuntu,Cantarell,"Helvetica Neue",sans-serif;}
</style>
<link crossorigin='anonymous' rel='stylesheet' id='all-css-14-1' href='https://s0.wp.com/_static/??-eJyNjcsKAjEMRX/IGsdR1IX4KRLT0nZMkzJpEf/eB27Ejbt74HIO3KojlRakQemuco9ZDKbQKtL1w2BdoKjvHAws4Rw8en9/zyxxSWYL+Ft0zkJgShnZsUa1L/iRtRTKM5s2EFkvyK/DqRyH3WrcDodxv54euNBIXw==&cssminify=yes' type='text/css' media='all' />
<script type="text/javascript" id="jetpack_related-posts-js-extra">
/* <![CDATA[ */
var related_posts_js_options = {"post_heading":"h4"};
/* ]]> */
</script>
<script type="text/javascript" id="notes-common-lite-js-extra">
/* <![CDATA[ */
var wpNotesArgs = {"cacheBuster":"intentional_failure-2692-g99140bffb8","iframeUrl":"https:\/\/widgets.wp.com\/notifications\/","iframeAppend":"2","iframeScroll":"no","wide":"1"};
/* ]]> */
</script>
<script type="text/javascript" id="media-video-jwt-bridge-js-extra">
/* <![CDATA[ */
var videopressAjax = {"ajaxUrl":"https:\/\/importdotexport.wordpress.com\/wp-admin\/admin-ajax.php","bridgeUrl":"\/wp-content\/mu-plugins\/jetpack-plugin\/sun\/jetpack_vendor\/automattic\/jetpack-videopress\/build\/lib\/token-bridge.js","post_id":"2078"};
/* ]]> */
</script>
<script type="text/javascript" id="wpcom-actionbar-placeholder-js-extra">
/* <![CDATA[ */
var actionbardata = {"siteID":"177426086","postID":"2078","siteURL":"http:\/\/importdotexport.wordpress.com","xhrURL":"https:\/\/importdotexport.wordpress.com\/wp-admin\/admin-ajax.php","nonce":"c0a15b6920","isLoggedIn":"1","statusMessage":"","subsEmailDefault":"instantly","proxyScriptUrl":"https:\/\/s0.wp.com\/wp-content\/js\/wpcom-proxy-request.js?ver=20211021","shortlink":"https:\/\/wp.me\/sc0sD4-coder","i18n":{"followedText":"New posts from this site will now appear in your <a href=\"https:\/\/wordpress.com\/read\">Reader<\/a>","foldBar":"Collapse this bar","unfoldBar":"Expand this bar"}};
/* ]]> */
</script>
<script crossorigin='anonymous' type='text/javascript' src='https://s0.wp.com/_static/??-eJyVUF1PwzAM/ENkhj5U6wPip0xpYyJ3SRwcp9v+PZko1RgfEi+27JzvcgenbCZOiklhLhB5pICmFhTr285QeuXdXB7gBheryaF6SgVm1Gyn4zpDqQkOlCYYKwUHgsEqOpO5aPk67SKle96mL0FNFj5f/tBMrLjW9hwjJxNI8SfGb1fWNZQZrZil+5+tdXVYMDkWsFU5WlWaNvBCDjkLlrLaDzSC8hGboJDzeC84Bvab5InFWdccBVtK+2kLY4oZlu7aTGomvcvySdEyDtV9wOa3inJZ220Kv4JMJC92i+wlPj/1wzDs+65/nN8BjLLGNQ=='></script>
<script type="text/javascript" id="rlt-proxy-js-after">
/* <![CDATA[ */
	window.addEventListener( 'DOMContentLoaded', function() {
		rltInitialize( {"token":"rlt-MnxqKzBqblNobjhDSzVQMVZmWVJ4cjRySWJwcWUxWGVTSlg0SWtoc2pEU3dPZ2x3TjNscEV1Y2xtcnNLRVRpVnM4S2NzYWVWNjNRVVVraVBsSGdzbFlSS2licTBxemlKQkdHd1pwbklHTGdraFZ5U051YVo4SVdzOXR0eGFOWGRqYVAxUUpLOXBDV1dud0FLeEZOTUdYdjUvbjRaekxjZWRkSDhHVUZUVkRGdlA4ejRFYWZBY1RmZjg4KzRDdHdGRzBjTDdPR0FmVWZkbGE3UkZUNnU3dmh3MXBSb1BOQzRNWFc4b0o5Kyt6cks2MjRTMjh1NDBzRzdnQy9PTVFsdTBsL2pBZTRIMjl6N3E5S1pUK3FDRVFaTXhqeDE5ejEweTYzVnU4K1AwdW01NU9nV3JvT1loQVRqYz18MzdjNTdkYTc1OWE3ZGJiMWQ5NDM5MmIzMGFhMTY5MGNiMTUwNThkZWI1M2M4NGYyfGNkYjQ5MzdlM2RmMjFhOTkzZDIxODQ1ZjU1NmE0YmIzYTFhNWEzMjA0NTM0ZDhkYTE4NDhlMGY4YTNiODk5NWE4YWMwMTI2ZjkzMWNjNDAxNzI2ZDBhNmFkM2JkNThiMmExOGUxOWQ5MmUyNDA0MjdlNWRiZWFlNWJjMDY3ZTJj","iframeOrigins":["https:\/\/widgets.wp.com"]} );
	} );
/* ]]> */
</script>
<link rel="EditURI" type="application/rsd+xml" title="RSD" href="https://importdotexport.wordpress.com/xmlrpc.php?rsd" />
<meta name="generator" content="WordPress.com" />
<link rel="canonical" href="https://importdotexport.wordpress.com/2024/01/11/coder/" />
<link rel='shortlink' href='https://wp.me/sc0sD4-coder' />
<link rel="alternate" type="application/json+oembed" href="https://public-api.wordpress.com/oembed/?format=json&amp;url=https%3A%2F%2Fimportdotexport.wordpress.com%2F2024%2F01%2F11%2Fcoder%2F&amp;for=wpcom-auto-discovery" /><link rel="alternate" type="application/xml+oembed" href="https://public-api.wordpress.com/oembed/?format=xml&amp;url=https%3A%2F%2Fimportdotexport.wordpress.com%2F2024%2F01%2F11%2Fcoder%2F&amp;for=wpcom-auto-discovery" />
<!-- Jetpack Open Graph Tags -->
<meta property="og:type" content="article" />
<meta property="og:title" content="#coder" />
<meta property="og:url" content="https://importdotexport.wordpress.com/2024/01/11/coder/" />
<meta property="og:description" content="### hi ![image]( # npm &#8211; a JavaScript package manager ![main]( ![Capture d’écran du 2023-12-28 19-52-07]( Editing ayatweb/README.md at main · ayatweb/ayatweb" />
<meta property="article:published_time" content="2024-01-11T19:53:53+00:00" />
<meta property="article:modified_time" content="2024-01-11T19:53:53+00:00" />
<meta property="og:site_name" content="phytosanitary products by Start Export" />
<meta property="og:image" content="https://importdotexport.files.wordpress.com/2020/05/apple-logo.jpg?w=200" />
<meta property="og:image:width" content="200" />
<meta property="og:image:height" content="200" />
<meta property="og:image:alt" content="" />
<meta property="og:locale" content="fr_FR" />
<meta property="fb:app_id" content="249643311490" />
<meta property="article:publisher" content="https://www.facebook.com/WordPresscom" />
<meta name="twitter:creator" content="@skyperx1" />
<meta name="twitter:site" content="@skyperx1" />
<meta name="twitter:text:title" content="#coder" />
<meta name="twitter:image" content="https://importdotexport.files.wordpress.com/2020/05/apple-logo.jpg?w=240" />
<meta name="twitter:card" content="summary" />

<!-- End Jetpack Open Graph Tags -->
<link rel="search" type="application/opensearchdescription+xml" href="https://importdotexport.wordpress.com/osd.xml" title="phytosanitary products by Start Export" />
<link rel="search" type="application/opensearchdescription+xml" href="https://s1.wp.com/opensearch.xml" title="WordPress.com" />
<link rel="pingback" href="https://importdotexport.wordpress.com/xmlrpc.php"><meta name="application-name" content="phytosanitary products by Start Export" /><meta name="msapplication-window" content="width=device-width;height=device-height" /><meta name="msapplication-tooltip" content="B2B" /><meta name="msapplication-task" content="name=Modifier l’article;action-uri=https://wordpress.com/post/importdotexport.wordpress.com/2078;icon-uri=https://s0.wp.com/i/icons/post.ico" /><meta name="msapplication-task" content="name=Écrire un article;action-uri=https://wordpress.com/post/importdotexport.wordpress.com;icon-uri=https://s0.wp.com/i/icons/post.ico" /><meta name="msapplication-task" content="name=Modérer les commentaires;action-uri=https://importdotexport.wordpress.com/wp-admin/edit-comments.php?comment_status=moderated;icon-uri=https://s0.wp.com/i/icons/comment.ico" /><meta name="msapplication-task" content="name=Envoi d’un nouveau média;action-uri=https://importdotexport.wordpress.com/wp-admin/media-new.php;icon-uri=https://s0.wp.com/i/icons/media.ico" /><meta name="msapplication-task" content="name=Stats du site;action-uri=https://importdotexport.wordpress.com/wp-admin/index.php?page=stats;icon-uri=https://s0.wp.com/i/icons/stats.ico" /><meta name="description" content="### hi https://github.com/ayatweb/ayatweb/assets/145841131/622946b9-f3c8-414a-bb1b-1dea6157568a[![learn-github-actions](https://github.com/ayatweb/ayatweb/actions/workflows/env.yml/badge.svg)](https://github.com/ayatweb/ayatweb/actions/workflows/env.yml)https://github.com/ayatweb/ayatweb/assets/145841131/ba8fa9a1-cc57-4619-a92c-c4490765fb91 ![image](https://github.com/ayatweb/ayatweb/assets/145841131/4c4d0cdd-6f1f-4998-834e-7f1cfd3c7b8c) # npm - a JavaScript package manager ![main](https://github.com/ayatweb/ayatweb/assets/145841131/8410bfa9-e5d4-4fd5-af3f-7a991b35d985) ![Capture d’écran du 2023-12-28 19-52-07](https://github.com/ayatweb/ayatweb/assets/145841131/8400bcea-f732-49ac-a545-05ea2512b00a) https://chat.openai.com/share/8b24837e-955c-466f-8900-821b73784a1f Editing ayatweb/README.md at main · ayatweb/ayatweb https://github.com/ayatweb/ayatweb/edit/main/README.md" />
		<script type="text/javascript">
		function __ATA_CC() {var v = document.cookie.match('(^|;) ?personalized-ads-consent=([^;]*)(;|$)');return v ? 1 : 0;}
		var __ATA_PP = { 'pt': 1, 'ht': 0, 'tn': 'morden', 'uloggedin': 1, 'amp': false, 'consent': __ATA_CC(), 'gdpr_applies': false, 'ad': { 'label': { 'text': 'Publicités' }, 'reportAd': { 'text': 'Report this Ad' } }, 'disabled_slot_formats': [], 'siteid': 8982, 'blogid': 177426086 };
		var __ATA = __ATA || {};
		__ATA.cmd = __ATA.cmd || [];
		__ATA.criteo = __ATA.criteo || {};
		__ATA.criteo.cmd = __ATA.criteo.cmd || [];
		</script>
		<script type="text/javascript">
		(function(){var g=Date.now||function(){return+new Date};function h(a,b){a:{for(var c=a.length,d="string"==typeof a?a.split(""):a,e=0;e<c;e++)if(e in d&&b.call(void 0,d[e],e,a)){b=e;break a}b=-1}return 0>b?null:"string"==typeof a?a.charAt(b):a[b]};function k(a,b,c){c=null!=c?"="+encodeURIComponent(String(c)):"";if(b+=c){c=a.indexOf("#");0>c&&(c=a.length);var d=a.indexOf("?");if(0>d||d>c){d=c;var e=""}else e=a.substring(d+1,c);a=[a.substr(0,d),e,a.substr(c)];c=a[1];a[1]=b?c?c+"&"+b:b:c;a=a[0]+(a[1]?"?"+a[1]:"")+a[2]}return a};var l=0;function m(a,b){var c=document.createElement("script");c.src=a;c.onload=function(){b&&b(void 0)};c.onerror=function(){b&&b("error")};a=document.getElementsByTagName("head");var d;a&&0!==a.length?d=a[0]:d=document.documentElement;d.appendChild(c)}function n(a){var b=void 0===b?document.cookie:b;return(b=h(b.split("; "),function(c){return-1!=c.indexOf(a+"=")}))?b.split("=")[1]:""}function p(a){return"string"==typeof a&&0<a.length}
		function r(a,b,c){b=void 0===b?"":b;c=void 0===c?".":c;var d=[];Object.keys(a).forEach(function(e){var f=a[e],q=typeof f;"object"==q&&null!=f||"function"==q?d.push(r(f,b+e+c)):null!==f&&void 0!==f&&(e=encodeURIComponent(b+e),d.push(e+"="+encodeURIComponent(f)))});return d.filter(p).join("&")}function t(a,b){a||((window.__ATA||{}).config=b.c,m(b.url))}var u=Math.floor(1E13*Math.random()),v=window.__ATA||{};window.__ATA=v;window.__ATA.cmd=v.cmd||[];v.rid=u;v.createdAt=g();var w=window.__ATA||{},x="s.pubmine.com";
		w&&w.serverDomain&&(x=w.serverDomain);var y="//"+x+"/conf",z=window.top===window,A=window.__ATA_PP&&window.__ATA_PP.gdpr_applies,B="boolean"===typeof A?Number(A):null,C=window.__ATA_PP||null,D=z?document.referrer?document.referrer:null:null,E=z?window.location.href:document.referrer?document.referrer:null,F,G=n("__ATA_tuuid");F=G?G:null;var H=window.innerWidth+"x"+window.innerHeight,I=n("usprivacy"),J=r({gdpr:B,pp:C,rid:u,src:D,ref:E,tuuid:F,vp:H,us_privacy:I?I:null},"",".");
		(function(a){var b=void 0===b?"cb":b;l++;var c="callback__"+g().toString(36)+"_"+l.toString(36);a=k(a,b,c);window[c]=function(d){t(void 0,d)};m(a,function(d){d&&t(d)})})(y+"?"+J);}).call(this);
		</script>	<script>
		var sas_fallback = sas_fallback || [];
		sas_fallback.push(
			{ tag: "&lt;div id=&quot;atatags-26942-65a0476a3317a&quot;&gt;&lt;/div&gt;&lt;script&gt;__ATA.cmd.push(function() {__ATA.initDynamicSlot({id: \'atatags-26942-65a0476a3317a\',location: 120,formFactor: \'001\',label: {text: \'Publicités\',},creative: {reportAd: {text: \'Report this Ad\',},privacySettings: {text: \'Confidentialité\',}}});});&lt;/script&gt;", type: 'belowpost' },
			{ tag: "&lt;div id=&quot;atatags-26942-{{unique_id}}&quot;&gt;&lt;/div&gt;&lt;script&gt;__ATA.cmd.push(function() {__ATA.initDynamicSlot({id: \'atatags-26942-{{unique_id}}\',location: 310,formFactor: \'001\',label: {text: \'Publicités\',},creative: {reportAd: {text: \'Report this Ad\',},privacySettings: {text: \'Confidentialité\',}}});});&lt;/script&gt;", type: 'inline' }
		);
	</script>		<script type="text/javascript">

			window.doNotSellCallback = function() {

				var linkElements = [
					'a[href="https://wordpress.com/?ref=footer_blog"]',
					'a[href="https://wordpress.com/?ref=footer_website"]',
					'a[href="https://wordpress.com/?ref=vertical_footer"]',
					'a[href^="https://wordpress.com/?ref=footer_segment_"]',
				].join(',');

				var dnsLink = document.createElement( 'a' );
				dnsLink.href = 'https://wordpress.com/fr/advertising-program-optout/';
				dnsLink.classList.add( 'do-not-sell-link' );
				dnsLink.rel = 'nofollow';
				dnsLink.style.marginLeft = '0.5em';
				dnsLink.textContent = 'Ne pas vendre ni partager mes informations personnelles';

				var creditLinks = document.querySelectorAll( linkElements );

				if ( 0 === creditLinks.length ) {
					return false;
				}

				Array.prototype.forEach.call( creditLinks, function( el ) {
					el.insertAdjacentElement( 'afterend', dnsLink );
				});

				return true;
			};

		</script>
		<link rel="icon" href="https://importdotexport.files.wordpress.com/2020/05/apple-logo.jpg?w=32" sizes="32x32" />
<link rel="icon" href="https://importdotexport.files.wordpress.com/2020/05/apple-logo.jpg?w=192" sizes="192x192" />
<link rel="apple-touch-icon" href="https://importdotexport.files.wordpress.com/2020/05/apple-logo.jpg?w=180" />
<meta name="msapplication-TileImage" content="https://importdotexport.files.wordpress.com/2020/05/apple-logo.jpg?w=270" />
<script type="text/javascript">
	window.google_analytics_uacct = "UA-52447-2";
</script>

<script type="text/javascript">
	var _gaq = _gaq || [];
	_gaq.push(['_setAccount', 'UA-52447-2']);
	_gaq.push(['_gat._anonymizeIp']);
	_gaq.push(['_setDomainName', 'wordpress.com']);
	_gaq.push(['_initData']);
	_gaq.push(['_trackPageview']);

	(function() {
		var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
		ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
		(document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(ga);
	})();
</script>
</head>

<body class="post-template-default single single-post postid-2078 single-format-standard logged-in admin-bar no-customize-support wp-embed-responsive customizer-styles-applied singular image-filters-enabled jetpack-reblog-enabled has-marketing-bar has-marketing-bar-theme-morden">

		<div id="wpadminbar" class="nojq nojs ltr nav-unification">
							<a class="screen-reader-shortcut" href="#wp-toolbar" tabindex="1">Skip to toolbar</a>
						<div class="quicklinks" id="wp-toolbar" role="navigation" aria-label="Toolbar" tabindex="0">
						<ul id="wp-admin-bar-root-default" class="ab-top-menu">
			
		<li id="wp-admin-bar-blog" class="my-sites mb-trackable"><a class="ab-item"  href="https://wordpress.com/sites/importdotexport.wordpress.com">My Sites</a>		</li>
		<li id="wp-admin-bar-jumptotop-button-menu"><a class="ab-item"  href="#"><div id="jumptotop"><span class="noticon noticon-top"></span></div></a>		</li>
		<li id="wp-admin-bar-newdash" class="mb-trackable"><a class="ab-item"  href="https://wordpress.com/read">Reader</a>		</li>		</ul>
			<ul id="wp-admin-bar-top-secondary" class="ab-top-secondary ab-top-menu">
			
		<li id="wp-admin-bar-notes" class="menupop"><a class="ab-item"  href="https://wordpress.com/notifications"><span id="wpnt-notes-unread-count" class="wpnt-loading wpn-read"></span><span class="noticon noticon-bell"></span><span class="ab-text">Notifications</span></a><div id="wpnt-notes-panel2" style="display:none" lang="en" dir="ltr"><div class="wpnt-notes-panel-header"><span class="wpnt-notes-header"></span><span class="wpnt-notes-panel-link"></span></div></div>		</li>
		<li id="wp-admin-bar-my-account" class="with-avatar mb-trackable"><a class="ab-item"  href="https://wordpress.com/me/"><img alt='' src='https://2.gravatar.com/avatar/b5b9824ceae24bfd4f1014aec909d057c7dd5400075008e865def6bc25d34d34?s=32&#038;d=mm&#038;r=G' srcset='https://2.gravatar.com/avatar/b5b9824ceae24bfd4f1014aec909d057c7dd5400075008e865def6bc25d34d34?s=32&#038;d=mm&#038;r=G 1x, https://2.gravatar.com/avatar/b5b9824ceae24bfd4f1014aec909d057c7dd5400075008e865def6bc25d34d34?s=48&#038;d=mm&#038;r=G 1.5x, https://2.gravatar.com/avatar/b5b9824ceae24bfd4f1014aec909d057c7dd5400075008e865def6bc25d34d34?s=64&#038;d=mm&#038;r=G 2x, https://2.gravatar.com/avatar/b5b9824ceae24bfd4f1014aec909d057c7dd5400075008e865def6bc25d34d34?s=96&#038;d=mm&#038;r=G 3x, https://2.gravatar.com/avatar/b5b9824ceae24bfd4f1014aec909d057c7dd5400075008e865def6bc25d34d34?s=128&#038;d=mm&#038;r=G 4x' class='avatar avatar-32' height='32' width='32' loading='lazy' decoding='async' /><span class="ab-text">Me</span></a>		</li>
		<li id="wp-admin-bar-ab-new-post" class="mb-trackable"><a class="ab-item"  href="https://wordpress.com/post/importdotexport.wordpress.com"><span>Write</span></a>		</li>		</ul>
				</div>
							<a class="screen-reader-shortcut" href="https://importdotexport.wordpress.com/wp-login.php?action=logout&#038;_wpnonce=87f9614ae8">Log Out</a>
					</div>

	
<script type="text/javascript">
/* <![CDATA[ */
(function() {
	function init() {
		document.addEventListener( 'load', function() {
			// hack to hide the gravatar hovercard
			document.querySelectorAll( '#wpadminbar img.grav-hashed' ).forEach( function (el) {
				el.classList.remove( 'grav-hashed' );
			} );
		} )

		// debug bar extra
		window.clickDebugLink = function( parentId, obj ) {
			if ( ! window.jQuery ) {
				return;
			}
			var $ = window.jQuery;

			$( '#' + parentId ).children( 'div' ).hide();

			document.getElementById( obj.href.substr( obj.href.indexOf( '#' ) + 1 ) ).style.display = 'block';
			$( obj.href.substr( obj.href.indexOf( '#' ) ) ).show()

			$( obj ).parent().addClass( 'current' ).siblings( 'li' ).removeClass( 'current' );

			return false;
		};
	}

	if ( document.readyState !== 'loading' ) {
		init();
	} else {
		document.addEventListener( 'DOMContentLoaded', init );
	}
})();
/* ]]> */
</script>
	<div class="wpcom-bubble action-bubble">
		<div class="bubble-txt"></div>
	</div>
	<script type="text/javascript">
	function hideBubble() {
		var bubble = document.querySelector( 'div.wpcom-bubble' );
		if ( ! bubble ) {
			return;
		}
		bubble.parentElement.removeChild( bubble );

		bubble = document.createElement( 'div' );
		bubble.classList.add( 'wpcom-bubble' );
		bubble.classList.add( 'action-bubble' );
		bubble.innerHTML = '<div class="bubble-txt"></div>';
		document.body.appendChild( bubble );
	}
	</script>
		<script type="text/javascript">
		(function () {
			'use strict';

			var isShowing = false;

			document.querySelectorAll( '#wp-admin-bar-jumptotop-button-menu a' ).forEach( function ( el ) {
				el.addEventListener( 'click', function ( e ) {
					e.preventDefault();
					if ( window.CSS && window.CSS.supports && window.CSS.supports( 'scroll-behavior', 'smooth' ) ) {
						window.scroll( { top: 0, left: 0, behavior: 'smooth' } );
					} else {
						window.scroll( 0, 0 );
					}
				} );
			} );

			function hideShowButton() {
				var jumpToTop = document.querySelector( '#jumptotop' );
				if ( isShowing ) {
					jumpToTop.style.transform = 'translateY( 0 )';
				} else {
					jumpToTop.style.transform = 'translateY( -50px )';
				}
			}

			function hideShowTbJumpToTop() {
				var total_width = 0;
				// Calculate total width taken by items minus our button to see if it'll
				// overlap with other toolbar menus.
				document.querySelectorAll( '#wp-admin-bar-root-default > li' ).forEach( function( el ) {
					if ( el.getAttribute( 'id' ) !== 'wp-admin-bar-jumptotop-button-menu' ) {
						total_width += el.offsetWidth;
					}
				} );
				var menu = document.querySelector( '#wp-admin-bar-jumptotop-button-menu' );
				if ( ! menu ) {
					return;
				}

				if ( menu.offsetLeft - total_width < 10 ) {
					isShowing = false;
				} else if ( window.scrollY >= 350 && ! isShowing ) {
					if ( menu.offsetLeft - total_width < 10 ) {
						return;
					}
					isShowing = true;
				} else if ( window.scrollY < 1 && isShowing ) {
					isShowing = false;
				}
				hideShowButton();
			}

			// handle on page load if auto scrolling to a position
			hideShowTbJumpToTop();

			// Bind to scroll event
			var jumpToTopTimer = null;
			window.addEventListener( 'scroll', function() {
				clearTimeout( jumpToTopTimer );
				jumpToTopTimer = setTimeout( hideShowTbJumpToTop, 150 );
			}, { passive: true } );
		})();
	</script>
	
<div id="page" class="site">
	<a class="skip-link screen-reader-text" href="#content">Accéder au contenu</a>

	
<header id="masthead" class="site-header" role="banner">
	<div class="site-header-wrap responsive-max-width has-title-and-tagline has-menu">
		

			<p class="site-title"><a href="https://importdotexport.wordpress.com/" rel="home">phytosanitary products by Start Export</a></p>
	
		<p class="site-description">
			B2B		</p>
			<nav id="site-navigation" class="main-navigation" aria-label="Navigation principale">

		<input type="checkbox" role="button" aria-haspopup="true" id="toggle" class="hide-visually">
		<label for="toggle" id="toggle-menu" class="button">
			Menu			<span class="dropdown-icon open">+</span>
			<span class="dropdown-icon close">&times;</span>
			<span class="hide-visually expanded-text">déplié</span>
			<span class="hide-visually collapsed-text">réduit</span>
		</label>

		<div class="menu-social-container"><ul id="menu-social-1" class="main-menu" aria-label="submenu"><li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-24"><a href="https://facebook.com">Facebook</a></li>
<li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-25"><a href="https://twitter.com">Twitter</a></li>
<li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-26"><a href="https://instagram.com">Instagram</a></li>
<li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-27"><a href="https://pinterest.com">Pinterest</a></li>
<li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-28"><a href="https://wordpress.com">WordPress</a></li>
<li class="menu-item menu-item-type-post_type menu-item-object-page menu-item-705"><a href="https://importdotexport.wordpress.com/next-level/">next level</a></li>
<li class="menu-item menu-item-type-post_type menu-item-object-page menu-item-2058"><a href="https://importdotexport.wordpress.com/images-et-paragraphes-dans-une-grille/">Images et paragraphes dans une grille</a></li>
</ul></div>	</nav><!-- #site-navigation -->
			<nav class="social-navigation" role="navigation" aria-label="Menu des liens de réseaux sociaux">
		<div class="menu-social-container"><ul id="menu-social-2" class="social-links-menu"><li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-24"><a href="https://facebook.com"><span class="screen-reader-text">Facebook</span><svg class="svg-icon" width="26" height="26" aria-hidden="true" role="img" focusable="false" viewBox="0 0 24 24" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path d="M20.007,3H3.993C3.445,3,3,3.445,3,3.993v16.013C3,20.555,3.445,21,3.993,21h8.621v-6.971h-2.346v-2.717h2.346V9.31 c0-2.325,1.42-3.591,3.494-3.591c0.993,0,1.847,0.074,2.096,0.107v2.43l-1.438,0.001c-1.128,0-1.346,0.536-1.346,1.323v1.734h2.69 l-0.35,2.717h-2.34V21h4.587C20.555,21,21,20.555,21,20.007V3.993C21,3.445,20.555,3,20.007,3z"></path></svg></a></li>
<li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-25"><a href="https://twitter.com"><span class="screen-reader-text">Twitter</span><svg class="svg-icon" width="26" height="26" aria-hidden="true" role="img" focusable="false" viewBox="0 0 24 24" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path d="M22.23,5.924c-0.736,0.326-1.527,0.547-2.357,0.646c0.847-0.508,1.498-1.312,1.804-2.27 c-0.793,0.47-1.671,0.812-2.606,0.996C18.324,4.498,17.257,4,16.077,4c-2.266,0-4.103,1.837-4.103,4.103 c0,0.322,0.036,0.635,0.106,0.935C8.67,8.867,5.647,7.234,3.623,4.751C3.27,5.357,3.067,6.062,3.067,6.814 c0,1.424,0.724,2.679,1.825,3.415c-0.673-0.021-1.305-0.206-1.859-0.513c0,0.017,0,0.034,0,0.052c0,1.988,1.414,3.647,3.292,4.023 c-0.344,0.094-0.707,0.144-1.081,0.144c-0.264,0-0.521-0.026-0.772-0.074c0.522,1.63,2.038,2.816,3.833,2.85 c-1.404,1.1-3.174,1.756-5.096,1.756c-0.331,0-0.658-0.019-0.979-0.057c1.816,1.164,3.973,1.843,6.29,1.843 c7.547,0,11.675-6.252,11.675-11.675c0-0.178-0.004-0.355-0.012-0.531C20.985,7.47,21.68,6.747,22.23,5.924z"></path></svg></a></li>
<li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-26"><a href="https://instagram.com"><span class="screen-reader-text">Instagram</span><svg class="svg-icon" width="26" height="26" aria-hidden="true" role="img" focusable="false" viewBox="0 0 24 24" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path d="M12,4.622c2.403,0,2.688,0.009,3.637,0.052c0.877,0.04,1.354,0.187,1.671,0.31c0.42,0.163,0.72,0.358,1.035,0.673 c0.315,0.315,0.51,0.615,0.673,1.035c0.123,0.317,0.27,0.794,0.31,1.671c0.043,0.949,0.052,1.234,0.052,3.637 s-0.009,2.688-0.052,3.637c-0.04,0.877-0.187,1.354-0.31,1.671c-0.163,0.42-0.358,0.72-0.673,1.035 c-0.315,0.315-0.615,0.51-1.035,0.673c-0.317,0.123-0.794,0.27-1.671,0.31c-0.949,0.043-1.233,0.052-3.637,0.052 s-2.688-0.009-3.637-0.052c-0.877-0.04-1.354-0.187-1.671-0.31c-0.42-0.163-0.72-0.358-1.035-0.673 c-0.315-0.315-0.51-0.615-0.673-1.035c-0.123-0.317-0.27-0.794-0.31-1.671C4.631,14.688,4.622,14.403,4.622,12 s0.009-2.688,0.052-3.637c0.04-0.877,0.187-1.354,0.31-1.671c0.163-0.42,0.358-0.72,0.673-1.035 c0.315-0.315,0.615-0.51,1.035-0.673c0.317-0.123,0.794-0.27,1.671-0.31C9.312,4.631,9.597,4.622,12,4.622 M12,3 C9.556,3,9.249,3.01,8.289,3.054C7.331,3.098,6.677,3.25,6.105,3.472C5.513,3.702,5.011,4.01,4.511,4.511 c-0.5,0.5-0.808,1.002-1.038,1.594C3.25,6.677,3.098,7.331,3.054,8.289C3.01,9.249,3,9.556,3,12c0,2.444,0.01,2.751,0.054,3.711 c0.044,0.958,0.196,1.612,0.418,2.185c0.23,0.592,0.538,1.094,1.038,1.594c0.5,0.5,1.002,0.808,1.594,1.038 c0.572,0.222,1.227,0.375,2.185,0.418C9.249,20.99,9.556,21,12,21s2.751-0.01,3.711-0.054c0.958-0.044,1.612-0.196,2.185-0.418 c0.592-0.23,1.094-0.538,1.594-1.038c0.5-0.5,0.808-1.002,1.038-1.594c0.222-0.572,0.375-1.227,0.418-2.185 C20.99,14.751,21,14.444,21,12s-0.01-2.751-0.054-3.711c-0.044-0.958-0.196-1.612-0.418-2.185c-0.23-0.592-0.538-1.094-1.038-1.594 c-0.5-0.5-1.002-0.808-1.594-1.038c-0.572-0.222-1.227-0.375-2.185-0.418C14.751,3.01,14.444,3,12,3L12,3z M12,7.378 c-2.552,0-4.622,2.069-4.622,4.622S9.448,16.622,12,16.622s4.622-2.069,4.622-4.622S14.552,7.378,12,7.378z M12,15 c-1.657,0-3-1.343-3-3s1.343-3,3-3s3,1.343,3,3S13.657,15,12,15z M16.804,6.116c-0.596,0-1.08,0.484-1.08,1.08 s0.484,1.08,1.08,1.08c0.596,0,1.08-0.484,1.08-1.08S17.401,6.116,16.804,6.116z"></path></svg></a></li>
<li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-27"><a href="https://pinterest.com"><span class="screen-reader-text">Pinterest</span><svg class="svg-icon" width="26" height="26" aria-hidden="true" role="img" focusable="false" viewBox="0 0 24 24" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path d="M12.289,2C6.617,2,3.606,5.648,3.606,9.622c0,1.846,1.025,4.146,2.666,4.878c0.25,0.111,0.381,0.063,0.439-0.169 c0.044-0.175,0.267-1.029,0.365-1.428c0.032-0.128,0.017-0.237-0.091-0.362C6.445,11.911,6.01,10.75,6.01,9.668 c0-2.777,2.194-5.464,5.933-5.464c3.23,0,5.49,2.108,5.49,5.122c0,3.407-1.794,5.768-4.13,5.768c-1.291,0-2.257-1.021-1.948-2.277 c0.372-1.495,1.089-3.112,1.089-4.191c0-0.967-0.542-1.775-1.663-1.775c-1.319,0-2.379,1.309-2.379,3.059 c0,1.115,0.394,1.869,0.394,1.869s-1.302,5.279-1.54,6.261c-0.405,1.666,0.053,4.368,0.094,4.604 c0.021,0.126,0.167,0.169,0.25,0.063c0.129-0.165,1.699-2.419,2.142-4.051c0.158-0.59,0.817-2.995,0.817-2.995 c0.43,0.784,1.681,1.446,3.013,1.446c3.963,0,6.822-3.494,6.822-7.833C20.394,5.112,16.849,2,12.289,2"></path></svg></a></li>
<li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-28"><a href="https://wordpress.com"><span class="screen-reader-text">WordPress</span><svg class="svg-icon" width="26" height="26" aria-hidden="true" role="img" focusable="false" viewBox="0 0 24 24" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path d="M12.158,12.786L9.46,20.625c0.806,0.237,1.657,0.366,2.54,0.366c1.047,0,2.051-0.181,2.986-0.51 c-0.024-0.038-0.046-0.079-0.065-0.124L12.158,12.786z M3.009,12c0,3.559,2.068,6.634,5.067,8.092L3.788,8.341 C3.289,9.459,3.009,10.696,3.009,12z M18.069,11.546c0-1.112-0.399-1.881-0.741-2.48c-0.456-0.741-0.883-1.368-0.883-2.109 c0-0.826,0.627-1.596,1.51-1.596c0.04,0,0.078,0.005,0.116,0.007C16.472,3.904,14.34,3.009,12,3.009 c-3.141,0-5.904,1.612-7.512,4.052c0.211,0.007,0.41,0.011,0.579,0.011c0.94,0,2.396-0.114,2.396-0.114 C7.947,6.93,8.004,7.642,7.52,7.699c0,0-0.487,0.057-1.029,0.085l3.274,9.739l1.968-5.901l-1.401-3.838 C9.848,7.756,9.389,7.699,9.389,7.699C8.904,7.67,8.961,6.93,9.446,6.958c0,0,1.484,0.114,2.368,0.114 c0.94,0,2.397-0.114,2.397-0.114c0.485-0.028,0.542,0.684,0.057,0.741c0,0-0.488,0.057-1.029,0.085l3.249,9.665l0.897-2.996 C17.841,13.284,18.069,12.316,18.069,11.546z M19.889,7.686c0.039,0.286,0.06,0.593,0.06,0.924c0,0.912-0.171,1.938-0.684,3.22 l-2.746,7.94c2.673-1.558,4.47-4.454,4.47-7.771C20.991,10.436,20.591,8.967,19.889,7.686z M12,22C6.486,22,2,17.514,2,12 C2,6.486,6.486,2,12,2c5.514,0,10,4.486,10,10C22,17.514,17.514,22,12,22z"></path></svg></a></li>
<li class="menu-item menu-item-type-post_type menu-item-object-page menu-item-705"><a href="https://importdotexport.wordpress.com/next-level/"><span class="screen-reader-text">next level</span><svg class="svg-icon" width="26" height="26" aria-hidden="true" role="img" focusable="false" viewBox="0 0 24 24" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path d="M12.158,12.786L9.46,20.625c0.806,0.237,1.657,0.366,2.54,0.366c1.047,0,2.051-0.181,2.986-0.51 c-0.024-0.038-0.046-0.079-0.065-0.124L12.158,12.786z M3.009,12c0,3.559,2.068,6.634,5.067,8.092L3.788,8.341 C3.289,9.459,3.009,10.696,3.009,12z M18.069,11.546c0-1.112-0.399-1.881-0.741-2.48c-0.456-0.741-0.883-1.368-0.883-2.109 c0-0.826,0.627-1.596,1.51-1.596c0.04,0,0.078,0.005,0.116,0.007C16.472,3.904,14.34,3.009,12,3.009 c-3.141,0-5.904,1.612-7.512,4.052c0.211,0.007,0.41,0.011,0.579,0.011c0.94,0,2.396-0.114,2.396-0.114 C7.947,6.93,8.004,7.642,7.52,7.699c0,0-0.487,0.057-1.029,0.085l3.274,9.739l1.968-5.901l-1.401-3.838 C9.848,7.756,9.389,7.699,9.389,7.699C8.904,7.67,8.961,6.93,9.446,6.958c0,0,1.484,0.114,2.368,0.114 c0.94,0,2.397-0.114,2.397-0.114c0.485-0.028,0.542,0.684,0.057,0.741c0,0-0.488,0.057-1.029,0.085l3.249,9.665l0.897-2.996 C17.841,13.284,18.069,12.316,18.069,11.546z M19.889,7.686c0.039,0.286,0.06,0.593,0.06,0.924c0,0.912-0.171,1.938-0.684,3.22 l-2.746,7.94c2.673-1.558,4.47-4.454,4.47-7.771C20.991,10.436,20.591,8.967,19.889,7.686z M12,22C6.486,22,2,17.514,2,12 C2,6.486,6.486,2,12,2c5.514,0,10,4.486,10,10C22,17.514,17.514,22,12,22z"></path></svg></a></li>
<li class="menu-item menu-item-type-post_type menu-item-object-page menu-item-2058"><a href="https://importdotexport.wordpress.com/images-et-paragraphes-dans-une-grille/"><span class="screen-reader-text">Images et paragraphes dans une grille</span><svg class="svg-icon" width="26" height="26" aria-hidden="true" role="img" focusable="false" viewBox="0 0 24 24" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path d="M12.158,12.786L9.46,20.625c0.806,0.237,1.657,0.366,2.54,0.366c1.047,0,2.051-0.181,2.986-0.51 c-0.024-0.038-0.046-0.079-0.065-0.124L12.158,12.786z M3.009,12c0,3.559,2.068,6.634,5.067,8.092L3.788,8.341 C3.289,9.459,3.009,10.696,3.009,12z M18.069,11.546c0-1.112-0.399-1.881-0.741-2.48c-0.456-0.741-0.883-1.368-0.883-2.109 c0-0.826,0.627-1.596,1.51-1.596c0.04,0,0.078,0.005,0.116,0.007C16.472,3.904,14.34,3.009,12,3.009 c-3.141,0-5.904,1.612-7.512,4.052c0.211,0.007,0.41,0.011,0.579,0.011c0.94,0,2.396-0.114,2.396-0.114 C7.947,6.93,8.004,7.642,7.52,7.699c0,0-0.487,0.057-1.029,0.085l3.274,9.739l1.968-5.901l-1.401-3.838 C9.848,7.756,9.389,7.699,9.389,7.699C8.904,7.67,8.961,6.93,9.446,6.958c0,0,1.484,0.114,2.368,0.114 c0.94,0,2.397-0.114,2.397-0.114c0.485-0.028,0.542,0.684,0.057,0.741c0,0-0.488,0.057-1.029,0.085l3.249,9.665l0.897-2.996 C17.841,13.284,18.069,12.316,18.069,11.546z M19.889,7.686c0.039,0.286,0.06,0.593,0.06,0.924c0,0.912-0.171,1.938-0.684,3.22 l-2.746,7.94c2.673-1.558,4.47-4.454,4.47-7.771C20.991,10.436,20.591,8.967,19.889,7.686z M12,22C6.486,22,2,17.514,2,12 C2,6.486,6.486,2,12,2c5.514,0,10,4.486,10,10C22,17.514,17.514,22,12,22z"></path></svg></a></li>
</ul></div>	</nav><!-- .social-navigation -->
	</div><!-- .site-header-wrap -->
</header><!-- #masthead -->

	<div id="content" class="site-content">

	<section id="primary" class="content-area">
		<main id="main" class="site-main">

			
<article id="post-2078" class="post-2078 post type-post status-publish format-standard hentry category-non-classe entry">

	<header class="entry-header">
		<h1 class="entry-title">#coder</h1>				<div class="entry-meta">
			<span class="byline"><svg class="svg-icon" width="16" height="16" aria-hidden="true" role="img" focusable="false" viewBox="0 0 24 24" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"></path><path d="M0 0h24v24H0z" fill="none"></path></svg><span class="screen-reader-text">Publié par</span><span class="author vcard"><a class="url fn n" href="https://importdotexport.wordpress.com/author/startexpor/">Start Export</a></span></span><span class="posted-on"><svg class="svg-icon" width="16" height="16" aria-hidden="true" role="img" focusable="false" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><defs><path id="a" d="M0 0h24v24H0V0z"></path></defs><clipPath id="b"><use xlink:href="#a" overflow="visible"></use></clipPath><path clip-path="url(#b)" d="M12 2C6.5 2 2 6.5 2 12s4.5 10 10 10 10-4.5 10-10S17.5 2 12 2zm4.2 14.2L11 13V7h1.5v5.2l4.5 2.7-.8 1.3z"></path></svg><a href="https://importdotexport.wordpress.com/2024/01/11/coder/" rel="bookmark"><time class="entry-date published updated" datetime="2024-01-11T19:53:53+00:00">11 janvier 2024</time></a></span><span class="cat-links"><svg class="svg-icon" width="16" height="16" aria-hidden="true" role="img" focusable="false" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M10 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V8c0-1.1-.9-2-2-2h-8l-2-2z"></path><path d="M0 0h24v24H0z" fill="none"></path></svg><span class="screen-reader-text">Publié dans</span><a href="https://importdotexport.wordpress.com/category/non-classe/" rel="category tag">Non classé</a></span><span class="edit-link"><svg class="svg-icon" width="16" height="16" aria-hidden="true" role="img" focusable="false" viewBox="0 0 24 24" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04c.39-.39.39-1.02 0-1.41l-2.34-2.34c-.39-.39-1.02-.39-1.41 0l-1.83 1.83 3.75 3.75 1.83-1.83z"></path><path d="M0 0h24v24H0z" fill="none"></path></svg><a class="post-edit-link" href="https://wordpress.com/post/importdotexport.wordpress.com/2078">Modifier <span class="screen-reader-text">#coder</span></a></span>		</div><!-- .meta-info -->
			</header>

	
	<div class="entry-content">
		
<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p>### hi     <a href="https://github.com/ayatweb/ayatweb/assets/145841131/622946b9-f3c8-414a-bb1b-1dea6157568a%5B!%5Blearn-github-actions%5D(https://github.com/ayatweb/ayatweb/actions/workflows/env.yml/badge.svg)%5D(https://github.com/ayatweb/ayatweb/actions/workflows/env.yml)https://github.com/ayatweb/ayatweb/assets/145841131/ba8fa9a1-cc57-4619-a92c-c4490765fb91" rel="nofollow">https://github.com/ayatweb/ayatweb/assets/145841131/622946b9-f3c8-414a-bb1b-1dea6157568a%5B!%5Blearn-github-actions%5D(https://github.com/ayatweb/ayatweb/actions/workflows/env.yml/badge.svg)%5D(https://github.com/ayatweb/ayatweb/actions/workflows/env.yml)https://github.com/ayatweb/ayatweb/assets/145841131/ba8fa9a1-cc57-4619-a92c-c4490765fb91</a> ![image](<a href="https://github.com/ayatweb/ayatweb/assets/145841131/4c4d0cdd-6f1f-4998-834e-7f1cfd3c7b8c" rel="nofollow">https://github.com/ayatweb/ayatweb/assets/145841131/4c4d0cdd-6f1f-4998-834e-7f1cfd3c7b8c</a>)  # npm &#8211; a JavaScript package manager ![main](<a href="https://github.com/ayatweb/ayatweb/assets/145841131/8410bfa9-e5d4-4fd5-af3f-7a991b35d985" rel="nofollow">https://github.com/ayatweb/ayatweb/assets/145841131/8410bfa9-e5d4-4fd5-af3f-7a991b35d985</a>)    ![Capture d’écran du 2023-12-28 19-52-07](<a href="https://github.com/ayatweb/ayatweb/assets/145841131/8400bcea-f732-49ac-a545-05ea2512b00a" rel="nofollow">https://github.com/ayatweb/ayatweb/assets/145841131/8400bcea-f732-49ac-a545-05ea2512b00a</a>)       <a href="https://chat.openai.com/share/8b24837e-955c-466f-8900-821b73784a1f" rel="nofollow">https://chat.openai.com/share/8b24837e-955c-466f-8900-821b73784a1f</a> </p>
<cite><a href="https://github.com/ayatweb/ayatweb/edit/main/README.md">Editing ayatweb/README.md at main · ayatweb/ayatweb</a></cite></blockquote>



<p><a href="https://github.com/ayatweb/ayatweb/edit/main/README.md" rel="nofollow">https://github.com/ayatweb/ayatweb/edit/main/README.md</a></p>
<div id="atatags-370373-65a0476a61d7b">
		<script type="text/javascript">
			__ATA.cmd.push(function() {
				__ATA.initVideoSlot('atatags-370373-65a0476a61d7b', {
					sectionId: '370373',
					format: 'inread'
				});
			});
		</script>
	</div>		<div id="wordads-preview-parent" class="wpcnt">
			<div class="wpa">
				<span class="wpa-about">Publicités</span>
				<div class="u">
					<div class="wpa-notice">
						<p>De temps en temps, vos visiteurs peuvent voir de la publicité à cet emplacement, <br /> ainsi qu’une <a href="https://en.support.wordpress.com/cookie-widget/" target="_blank">bannière de Confidentialité & Cookies</a> au bas de la page.<br/>Vous pouvez masquer complètement ces publicités grâce à une mise à niveau vers l’un de nos plans payants.</p>
						<p class="wpa-buttons">
							<a class="wpa-button is-primary" id="wordads-preview-more" href="https://wordpress.com/plans/177426086/?feature=no-adverts&utm_campaign=removeadsnotive" rel="nofollow" target="_blank">Mettre à niveau maintenant</a>
							<a class="wpa-button" id="wordads-preview-dismiss" href="#">Supprimer le message</a>
						</p>
					</div>
				</div>
			</div>
		</div>			<div id="atatags-26942-65a0476a61e61"></div>
			
			<script>
				__ATA.cmd.push(function() {
					__ATA.initDynamicSlot({
						id: 'atatags-26942-65a0476a61e61',
						location: 120,
						formFactor: '001',
						label: {
							text: 'Publicités',
						},
						creative: {
							reportAd: {
								text: 'Report this Ad',
							},
							privacySettings: {
								text: 'Confidentialité',
								
							}
						}
					});
				});
			</script><div id="jp-post-flair" class="sharedaddy sd-like-enabled sd-sharing-enabled"><div class="sharedaddy sd-sharing-enabled"><div class="robots-nocontent sd-block sd-social sd-social-official sd-sharing"><h3 class="sd-title">Partager :</h3><div class="sd-content"><ul><li class="share-telegram"><a rel="nofollow noopener noreferrer" data-shared="" class="share-telegram sd-button" href="https://importdotexport.wordpress.com/2024/01/11/coder/?share=telegram" target="_blank" title="Cliquez pour partager sur Telegram" ><span>Telegram</span></a></li><li class="share-linkedin"><div class="linkedin_button"><script type="in/share" data-url="https://importdotexport.wordpress.com/2024/01/11/coder/" data-counter="right"></script></div></li><li class="share-skype share-deprecated"><a rel="nofollow" data-shared="" class="share-skype sd-button" href="https://importdotexport.wordpress.com/2024/01/11/coder/" title="Le service de partage Skype  a fermé ou cessé de prendre en charge les boutons de partage. Ce bouton de partage n’est plus visible par vos visiteurs. Vous devriez le supprimer." ><span>Skype  n’est plus pris en charge</span></a></li><li class="share-tumblr"><a class="tumblr-share-button" target="_blank" href="https://www.tumblr.com/share" data-title="#coder" data-content="https://importdotexport.wordpress.com/2024/01/11/coder/" title="Partager sur Tumblr">Partager sur Tumblr</a></li><li class="share-print"><a rel="nofollow noopener noreferrer" data-shared="" class="share-print sd-button" href="https://importdotexport.wordpress.com/2024/01/11/coder/#print" target="_blank" title="Cliquer pour imprimer" ><span>Imprimer</span></a></li><li class="share-twitter"><a href="https://twitter.com/share" class="twitter-share-button" data-url="https://importdotexport.wordpress.com/2024/01/11/coder/" data-text="#coder" data-via="skyperx1" data-related="wordpressdotcom">Tweet</a></li><li class="share-pinterest"><div class="pinterest_button"><a href="https://www.pinterest.com/pin/create/button/?url=https%3A%2F%2Fimportdotexport.wordpress.com%2F2024%2F01%2F11%2Fcoder%2F&#038;media=https%3A%2F%2Fimportdotexport.files.wordpress.com%2F2020%2F05%2Fapple-logo.jpg%3Fw%3D96&#038;description=%23coder" data-pin-do="buttonPin" data-pin-config="beside"><img src="//assets.pinterest.com/images/pidgets/pinit_fg_en_rect_gray_20.png" /></a></div></li><li class="share-reddit"><a rel="nofollow noopener noreferrer" data-shared="" class="share-reddit sd-button" href="https://importdotexport.wordpress.com/2024/01/11/coder/?share=reddit" target="_blank" title="Cliquez pour partager sur Reddit" ><span>Reddit</span></a></li><li class="share-press-this"><a rel="nofollow noopener noreferrer" data-shared="" class="share-press-this sd-button" href="https://importdotexport.wordpress.com/2024/01/11/coder/?share=press-this" target="_blank" title="Click to Press This!" ><span>Publier un article</span></a></li><li class="share-facebook"><div class="fb-share-button" data-href="https://importdotexport.wordpress.com/2024/01/11/coder/" data-layout="button_count"></div></li><li class="share-pocket"><div class="pocket_button"><a href="https://getpocket.com/save" class="pocket-btn" data-lang="en" data-save-url="https://importdotexport.wordpress.com/2024/01/11/coder/" data-pocket-count="horizontal" >Pocket</a></div></li><li class="share-email"><a rel="nofollow noopener noreferrer" data-shared="" class="share-email sd-button" href="mailto:?subject=%5BArticle%20partag%C3%A9%5D%20%23coder&body=https%3A%2F%2Fimportdotexport.wordpress.com%2F2024%2F01%2F11%2Fcoder%2F&share=email" target="_blank" title="Cliquer pour envoyer un lien par e-mail à un ami" data-email-share-error-title="Votre messagerie est-elle configurée ?" data-email-share-error-text="Si vous rencontrez des problèmes de partage par e-mail, votre messagerie n’est peut-être pas configurée pour votre navigateur. Vous devrez peut-être créer vous-même une nouvelle messagerie." data-email-share-nonce="550c83b479" data-email-share-track-url="https://importdotexport.wordpress.com/2024/01/11/coder/?share=email"><span>E-mail</span></a></li><li class="share-jetpack-whatsapp"><a rel="nofollow noopener noreferrer" data-shared="" class="share-jetpack-whatsapp sd-button" href="https://importdotexport.wordpress.com/2024/01/11/coder/?share=jetpack-whatsapp" target="_blank" title="Cliquez pour partager sur WhatsApp" ><span>WhatsApp</span></a></li><li class="share-end"></li></ul><p class="share-customize-link"><a href="https://jetpack.com/redirect/?source=calypso-marketing-sharing-buttons&#038;site=importdotexport.wordpress.com" target="_blank" rel="noopener noreferrer">Personnaliser les boutons</a></p></div></div></div><div class='sharedaddy sd-block sd-like jetpack-likes-widget-wrapper jetpack-likes-widget-unloaded' id='like-post-wrapper-177426086-2078-65a0476a62eff' data-src='//widgets.wp.com/likes/index.html?ver=20240111#blog_id=177426086&amp;post_id=2078&amp;origin=importdotexport.wordpress.com&amp;obj_id=177426086-2078-65a0476a62eff&amp;n=1' data-name='like-post-frame-177426086-2078-65a0476a62eff' data-title='Aimer ou rebloguer'><div class='likes-widget-placeholder post-likes-widget-placeholder' style='height: 55px;'><span class='button'><span>J’aime</span></span> <span class='loading'>chargement&hellip;</span></div><span class='sd-text-color'></span><a class='sd-link-color'></a></div>
<div id='jp-relatedposts' class='jp-relatedposts' >
	<h3 class="jp-relatedposts-headline"><em>Articles similaires</em></h3>
</div></div>	</div><!-- .entry-content -->

	<footer class="entry-footer responsive-max-width">
		<span class="byline"><svg class="svg-icon" width="16" height="16" aria-hidden="true" role="img" focusable="false" viewBox="0 0 24 24" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"></path><path d="M0 0h24v24H0z" fill="none"></path></svg><span class="screen-reader-text">Publié par</span><span class="author vcard"><a class="url fn n" href="https://importdotexport.wordpress.com/author/startexpor/">Start Export</a></span></span><span class="posted-on"><svg class="svg-icon" width="16" height="16" aria-hidden="true" role="img" focusable="false" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><defs><path id="a" d="M0 0h24v24H0V0z"></path></defs><clipPath id="b"><use xlink:href="#a" overflow="visible"></use></clipPath><path clip-path="url(#b)" d="M12 2C6.5 2 2 6.5 2 12s4.5 10 10 10 10-4.5 10-10S17.5 2 12 2zm4.2 14.2L11 13V7h1.5v5.2l4.5 2.7-.8 1.3z"></path></svg><a href="https://importdotexport.wordpress.com/2024/01/11/coder/" rel="bookmark"><time class="entry-date published updated" datetime="2024-01-11T19:53:53+00:00">11 janvier 2024</time></a></span><span class="cat-links"><svg class="svg-icon" width="16" height="16" aria-hidden="true" role="img" focusable="false" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M10 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V8c0-1.1-.9-2-2-2h-8l-2-2z"></path><path d="M0 0h24v24H0z" fill="none"></path></svg><span class="screen-reader-text">Publié dans</span><a href="https://importdotexport.wordpress.com/category/non-classe/" rel="category tag">Non classé</a></span><span class="edit-link"><svg class="svg-icon" width="16" height="16" aria-hidden="true" role="img" focusable="false" viewBox="0 0 24 24" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04c.39-.39.39-1.02 0-1.41l-2.34-2.34c-.39-.39-1.02-.39-1.41 0l-1.83 1.83 3.75 3.75 1.83-1.83z"></path><path d="M0 0h24v24H0z" fill="none"></path></svg><a class="post-edit-link" href="https://wordpress.com/post/importdotexport.wordpress.com/2078">Modifier <span class="screen-reader-text">#coder</span></a></span>	</footer><!-- .entry-footer -->

			<div class="author-bio responsive-max-width">
	<h2 class="author-title">
		<span class="author-heading">
			Publié par Start Export		</span>
	</h2>
	<p class="author-description">
		B2B
Import
Export		<a class="author-link" href="https://importdotexport.wordpress.com/author/startexpor/" rel="author">
			Voir plus d’articles		</a>
	</p><!-- .author-description -->
</div><!-- .author-bio -->
	
</article><!-- #post-${ID} -->

	<nav class="navigation post-navigation" aria-label="Articles">
		<h2 class="screen-reader-text">Navigation des articles</h2>
		<div class="nav-links"><div class="nav-previous"><a href="https://importdotexport.wordpress.com/2024/01/10/ayatweb-fastx/" rel="prev"><span class="meta-nav" aria-hidden="true">Article précédent</span> <span class="screen-reader-text">Article précédent :</span> <br/><span class="post-title">@ayatweb #fastx</span></a></div></div>
	</nav>
<div id="comments" class="comments-area responsive-max-width">

		<div id="respond" class="comment-respond">
		<h3 id="reply-title" class="comment-reply-title">Votre commentaire <small><a rel="nofollow" id="cancel-comment-reply-link" href="/2024/01/11/coder/#respond" style="display:none;">Annuler la réponse.</a></small></h3><form action="https://importdotexport.wordpress.com/wp-comments-post.php" method="post" id="commentform" class="comment-form" novalidate><div id="comment-form__verbum" class="transparent"></div><div class="verbum-form-meta"><input type='hidden' name='comment_post_ID' value='2078' id='comment_post_ID' />
<input type='hidden' name='comment_parent' id='comment_parent' value='0' />

			<input type="hidden" name="highlander_comment_nonce" id="highlander_comment_nonce" value="5800d1c573" />
			<input type="hidden" name="verbum_show_subscription_modal" value="hidden_is_blog_member" /></div><p style="display: none;"><input type="hidden" id="akismet_comment_nonce" name="akismet_comment_nonce" value="dd07566663" /></p><p style="display: none !important;" class="akismet-fields-container" data-prefix="ak_"><label>&#916;<textarea name="ak_hp_textarea" cols="45" rows="8" maxlength="100"></textarea></label><input type="hidden" id="ak_js_1" name="ak_js" value="226"/><script>document.getElementById( "ak_js_1" ).setAttribute( "value", ( new Date() ).getTime() );</script></p></form>	</div><!-- #respond -->
	
</div><!-- #comments -->

		</main><!-- #main -->
	</section><!-- #primary -->


	</div><!-- #content -->

	
	<footer id="colophon" class="site-footer responsive-max-width">
				<nav class="footer-navigation" aria-label="Menu du pied de page">
		<div class="menu-social-container"><ul id="menu-social-3" class="footer-menu"><li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-24"><a href="https://facebook.com">Facebook</a></li>
<li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-25"><a href="https://twitter.com">Twitter</a></li>
<li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-26"><a href="https://instagram.com">Instagram</a></li>
<li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-27"><a href="https://pinterest.com">Pinterest</a></li>
<li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-28"><a href="https://wordpress.com">WordPress</a></li>
<li class="menu-item menu-item-type-post_type menu-item-object-page menu-item-705"><a href="https://importdotexport.wordpress.com/next-level/">next level</a></li>
<li class="menu-item menu-item-type-post_type menu-item-object-page menu-item-2058"><a href="https://importdotexport.wordpress.com/images-et-paragraphes-dans-une-grille/">Images et paragraphes dans une grille</a></li>
</ul></div>	</nav><!-- .footer-navigation -->

	
		<div class="site-info">
		<a class="site-name" href="https://importdotexport.wordpress.com/" rel="home">phytosanitary products by Start Export</a><span class="comma">,</span>
<a href="https://wordpress.com/?ref=footer_custom_powered" rel="nofollow">Un site Web propulsé par WordPress.com</a>.	</div><!-- .site-info -->
	</footer><!-- #colophon -->

</div><!-- #page -->

<!--  -->
<script type="text/javascript" src="//0.gravatar.com/js/hovercards/hovercards.min.js?ver=202402131f6b765e798866d728f95661b78bbf269c86482ffff0fa8c08e18a1a65cc89" id="grofiles-cards-js"></script>
<script type="text/javascript" id="wpgroho-js-extra">
/* <![CDATA[ */
var WPGroHo = {"my_hash":"f91e4af369f32331ae0e1a23eaa91b37"};
/* ]]> */
</script>
<script crossorigin='anonymous' type='text/javascript' src='https://s0.wp.com/wp-content/mu-plugins/gravatar-hovercards/wpgroho.js?m=1610363240i'></script>

	<script>
		// Initialize and attach hovercards to all gravatars
		( function() {
			function init() {
				if ( typeof Gravatar === 'undefined' ) {
					return;
				}

				if ( typeof Gravatar.init !== 'function' ) {
					return;
				}

				Gravatar.profile_cb = function ( hash, id ) {
					WPGroHo.syncProfileData( hash, id );
				};

				Gravatar.my_hash = WPGroHo.my_hash;
				Gravatar.init(
					'body',
					'#wp-admin-bar-my-account',
					{
						i18n: {
							'Edit your profile': 'Modifier votre profil',
							'View profile': 'View profile',
							'Sorry, we are unable to load this Gravatar profile.': 'Sorry, we are unable to load this Gravatar profile.',
							'Sorry, we are unable to load this Gravatar profile. Please check your internet connection.': 'Sorry, we are unable to load this Gravatar profile. Please check your internet connection.',
						},
					}
				);
			}

			if ( document.readyState !== 'loading' ) {
				init();
			} else {
				document.addEventListener( 'DOMContentLoaded', init );
			}
		} )();
	</script>

		<div style="display:none">
	<div class="grofile-hash-map-f91e4af369f32331ae0e1a23eaa91b37">
	</div>
	</div>
		<!-- CCPA [start] -->
		<script type="text/javascript">
			( function () {

				var setupPrivacy = function() {

					// Minimal Mozilla Cookie library
					// https://developer.mozilla.org/en-US/docs/Web/API/Document/cookie/Simple_document.cookie_framework
					var cookieLib = window.cookieLib = {getItem:function(e){return e&&decodeURIComponent(document.cookie.replace(new RegExp("(?:(?:^|.*;)\\s*"+encodeURIComponent(e).replace(/[\-\.\+\*]/g,"\\$&")+"\\s*\\=\\s*([^;]*).*$)|^.*$"),"$1"))||null},setItem:function(e,o,n,t,r,i){if(!e||/^(?:expires|max\-age|path|domain|secure)$/i.test(e))return!1;var c="";if(n)switch(n.constructor){case Number:c=n===1/0?"; expires=Fri, 31 Dec 9999 23:59:59 GMT":"; max-age="+n;break;case String:c="; expires="+n;break;case Date:c="; expires="+n.toUTCString()}return"rootDomain"!==r&&".rootDomain"!==r||(r=(".rootDomain"===r?".":"")+document.location.hostname.split(".").slice(-2).join(".")),document.cookie=encodeURIComponent(e)+"="+encodeURIComponent(o)+c+(r?"; domain="+r:"")+(t?"; path="+t:"")+(i?"; secure":""),!0}};

					// Implement IAB USP API.
					window.__uspapi = function( command, version, callback ) {

						// Validate callback.
						if ( typeof callback !== 'function' ) {
							return;
						}

						// Validate the given command.
						if ( command !== 'getUSPData' || version !== 1 ) {
							callback( null, false );
							return;
						}

						// Check for GPC. If set, override any stored cookie.
						if ( navigator.globalPrivacyControl ) {
							callback( { version: 1, uspString: '1YYN' }, true );
							return;
						}

						// Check for cookie.
						var consent = cookieLib.getItem( 'usprivacy' );

						// Invalid cookie.
						if ( null === consent ) {
							callback( null, false );
							return;
						}

						// Everything checks out. Fire the provided callback with the consent data.
						callback( { version: 1, uspString: consent }, true );
					};

					// Initialization.
					document.addEventListener( 'DOMContentLoaded', function() {

						// Internal functions.
						var setDefaultOptInCookie = function() {
							var value = '1YNN';
							var domain = '.wordpress.com' === location.hostname.slice( -14 ) ? '.rootDomain' : location.hostname;
							cookieLib.setItem( 'usprivacy', value, 365 * 24 * 60 * 60, '/', domain );
						};

						var setDefaultOptOutCookie = function() {
							var value = '1YYN';
							var domain = '.wordpress.com' === location.hostname.slice( -14 ) ? '.rootDomain' : location.hostname;
							cookieLib.setItem( 'usprivacy', value, 24 * 60 * 60, '/', domain );
						};

						var setDefaultNotApplicableCookie = function() {
							var value = '1---';
							var domain = '.wordpress.com' === location.hostname.slice( -14 ) ? '.rootDomain' : location.hostname;
							cookieLib.setItem( 'usprivacy', value, 24 * 60 * 60, '/', domain );
						};

						var setCcpaAppliesCookie = function( applies ) {
							var domain = '.wordpress.com' === location.hostname.slice( -14 ) ? '.rootDomain' : location.hostname;
							cookieLib.setItem( 'ccpa_applies', applies, 24 * 60 * 60, '/', domain );
						}

						var maybeCallDoNotSellCallback = function() {
							if ( 'function' === typeof window.doNotSellCallback ) {
								return window.doNotSellCallback();
							}

							return false;
						}

						// Look for usprivacy cookie first.
						var usprivacyCookie = cookieLib.getItem( 'usprivacy' );

						// Found a usprivacy cookie.
						if ( null !== usprivacyCookie ) {

							// If the cookie indicates that CCPA does not apply, then bail.
							if ( '1---' === usprivacyCookie ) {
								return;
							}

							// CCPA applies, so call our callback to add Do Not Sell link to the page.
							maybeCallDoNotSellCallback();

							// We're all done, no more processing needed.
							return;
						}

						// We don't have a usprivacy cookie, so check to see if we have a CCPA applies cookie.
						var ccpaCookie = cookieLib.getItem( 'ccpa_applies' );

						// No CCPA applies cookie found, so we'll need to geolocate if this visitor is from California.
						// This needs to happen client side because we do not have region geo data in our $SERVER headers,
						// only country data -- therefore we can't vary cache on the region.
						if ( null === ccpaCookie ) {

							var request = new XMLHttpRequest();
							request.open( 'GET', 'https://public-api.wordpress.com/geo/', true );

							request.onreadystatechange = function () {
								if ( 4 === this.readyState ) {
									if ( 200 === this.status ) {

										// Got a geo response. Parse out the region data.
										var data = JSON.parse( this.response );
										var region      = data.region ? data.region.toLowerCase() : '';
										var ccpa_applies = ['california', 'colorado', 'connecticut', 'utah', 'virginia'].indexOf( region ) > -1;
										// Set CCPA applies cookie. This keeps us from having to make a geo request too frequently.
										setCcpaAppliesCookie( ccpa_applies );

										// Check if CCPA applies to set the proper usprivacy cookie.
										if ( ccpa_applies ) {
											if ( maybeCallDoNotSellCallback() ) {
												// Do Not Sell link added, so set default opt-in.
												setDefaultOptInCookie();
											} else {
												// Failed showing Do Not Sell link as required, so default to opt-OUT just to be safe.
												setDefaultOptOutCookie();
											}
										} else {
											// CCPA does not apply.
											setDefaultNotApplicableCookie();
										}
									} else {
										// Could not geo, so let's assume for now that CCPA applies to be safe.
										setCcpaAppliesCookie( true );
										if ( maybeCallDoNotSellCallback() ) {
											// Do Not Sell link added, so set default opt-in.
											setDefaultOptInCookie();
										} else {
											// Failed showing Do Not Sell link as required, so default to opt-OUT just to be safe.
											setDefaultOptOutCookie();
										}
									}
								}
							};

							// Send the geo request.
							request.send();
						} else {
							// We found a CCPA applies cookie.
							if ( ccpaCookie === 'true' ) {
								if ( maybeCallDoNotSellCallback() ) {
									// Do Not Sell link added, so set default opt-in.
									setDefaultOptInCookie();
								} else {
									// Failed showing Do Not Sell link as required, so default to opt-OUT just to be safe.
									setDefaultOptOutCookie();
								}
							} else {
								// CCPA does not apply.
								setDefaultNotApplicableCookie();
							}
						}
					} );
				};

				// Kickoff initialization.
				if ( window.defQueue && defQueue.isLOHP && defQueue.isLOHP === 2020 ) {
					defQueue.items.push( setupPrivacy );
				} else {
					setupPrivacy();
				}

			} )();
		</script>

		<!-- CCPA [end] -->
		<div class="widget widget_eu_cookie_law_widget">
<div
	class="hide-on-button ads-active"
	data-hide-timeout="30"
	data-consent-expiration="180"
	id="eu-cookie-law"
	style="display: none"
>
	<form method="post">
		<input type="submit" value="Fermer et accepter" class="accept" />

		Confidentialité &amp; Cookies : Ce site utilise des cookies. En continuant à utiliser ce site, vous acceptez leur utilisation.<br />
Pour en savoir davantage, y compris comment contrôler les cookies, voir :
				<a href="https://automattic.com/cookies/" rel="nofollow">
			Politique relative aux cookies		</a>
 </form>
</div>
</div><script type="text/javascript">
	window._tkq = window._tkq || [];
	if ( Math.random() <= 0.01 ) {
		window._tkq.push( [
			'recordEvent',
			'wpcom_wordads_noad',
			{"theme":"pub\/morden","blog_id":177426086,"post_id":2078,"reason_blog_unsafe":1,"reason_post_null":1}
		] );
	}
</script>	<div id="actionbar" style="display: none;"
			class="actnbr-pub-morden actnbr-has-customize actnbr-has-edit">
		<ul>
								<li class="actnbr-btn actnbr-customize">
						<a href="https://importdotexport.wordpress.com/wp-admin/customize.php?url=https%3A%2F%2Fimportdotexport.wordpress.com%2F2024%2F01%2F11%2Fcoder%2F">
							<svg class="gridicon gridicons-customize" height="20" width="20" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><g><path d="M2 6c0-1.505.78-3.08 2-4 0 .845.69 2 2 2 1.657 0 3 1.343 3 3 0 .386-.08.752-.212 1.09.74.594 1.476 1.19 2.19 1.81L8.9 11.98c-.62-.716-1.214-1.454-1.807-2.192C6.753 9.92 6.387 10 6 10c-2.21 0-4-1.79-4-4zm12.152 6.848l1.34-1.34c.607.304 1.283.492 2.008.492 2.485 0 4.5-2.015 4.5-4.5 0-.725-.188-1.4-.493-2.007L18 9l-2-2 3.507-3.507C18.9 3.188 18.225 3 17.5 3 15.015 3 13 5.015 13 7.5c0 .725.188 1.4.493 2.007L3 20l2 2 6.848-6.848c1.885 1.928 3.874 3.753 5.977 5.45l1.425 1.148 1.5-1.5-1.15-1.425c-1.695-2.103-3.52-4.092-5.448-5.977z"/></g></svg>							<span>Customize</span>
						</a>
					</li>
									<li class="actnbr-btn actnbr-edit">
						<a href="https://wordpress.com/post/importdotexport.wordpress.com/2078">
							<svg class="gridicon gridicons-pencil" height="20" width="20" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><g><path d="M13 6l5 5-9.507 9.507c-.686-.686-.69-1.794-.012-2.485l-.002-.003c-.69.676-1.8.673-2.485-.013-.677-.677-.686-1.762-.036-2.455l-.008-.008c-.694.65-1.78.64-2.456-.036L13 6zm7.586-.414l-2.172-2.172c-.78-.78-2.047-.78-2.828 0L14 5l5 5 1.586-1.586c.78-.78.78-2.047 0-2.828zM3 18v3h3c0-1.657-1.343-3-3-3z"/></g></svg>							<span>Edit</span>
						</a>
					</li>
					<li class="actnbr-btn actnbr-stats">
						<a href="https://wordpress.com/stats/post/2078/importdotexport.wordpress.com">
							<svg class="gridicon gridicons-stats-alt" height="20" width="20" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><g><path d="M21 21H3v-2h18v2zM8 10H4v7h4v-7zm6-7h-4v14h4V3zm6 3h-4v11h4V6z"/></g></svg>							<span>Stats</span>
						</a>
					</li>
							<li class="actnbr-ellipsis actnbr-hidden">
				<svg class="gridicon gridicons-ellipsis" height="24" width="24" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><g><path d="M7 12c0 1.104-.896 2-2 2s-2-.896-2-2 .896-2 2-2 2 .896 2 2zm12-2c-1.104 0-2 .896-2 2s.896 2 2 2 2-.896 2-2-.896-2-2-2zm-7 0c-1.104 0-2 .896-2 2s.896 2 2 2 2-.896 2-2-.896-2-2-2z"/></g></svg>				<div class="actnbr-popover tip tip-top-left actnbr-more">
					<div class="tip-arrow"></div>
					<div class="tip-inner">
						<ul>
									<li class="actnbr-sitename">
			<a href="https://importdotexport.wordpress.com">
				<img alt='' src='https://importdotexport.files.wordpress.com/2020/05/apple-logo.jpg?w=50' srcset='https://importdotexport.files.wordpress.com/2020/05/apple-logo.jpg?w=50 1x, https://importdotexport.files.wordpress.com/2020/05/apple-logo.jpg?w=75 1.5x, https://importdotexport.files.wordpress.com/2020/05/apple-logo.jpg?w=100 2x, https://importdotexport.files.wordpress.com/2020/05/apple-logo.jpg?w=150 3x, https://importdotexport.files.wordpress.com/2020/05/apple-logo.jpg?w=200 4x' class='avatar avatar-50' height='50' width='50' />				phytosanitary products by Start Export			</a>
		</li>
								<li class="actnbr-folded-customize">
								<a href="https://importdotexport.wordpress.com/wp-admin/customize.php?url=https%3A%2F%2Fimportdotexport.wordpress.com%2F2024%2F01%2F11%2Fcoder%2F">
									<svg class="gridicon gridicons-customize" height="20" width="20" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><g><path d="M2 6c0-1.505.78-3.08 2-4 0 .845.69 2 2 2 1.657 0 3 1.343 3 3 0 .386-.08.752-.212 1.09.74.594 1.476 1.19 2.19 1.81L8.9 11.98c-.62-.716-1.214-1.454-1.807-2.192C6.753 9.92 6.387 10 6 10c-2.21 0-4-1.79-4-4zm12.152 6.848l1.34-1.34c.607.304 1.283.492 2.008.492 2.485 0 4.5-2.015 4.5-4.5 0-.725-.188-1.4-.493-2.007L18 9l-2-2 3.507-3.507C18.9 3.188 18.225 3 17.5 3 15.015 3 13 5.015 13 7.5c0 .725.188 1.4.493 2.007L3 20l2 2 6.848-6.848c1.885 1.928 3.874 3.753 5.977 5.45l1.425 1.148 1.5-1.5-1.15-1.425c-1.695-2.103-3.52-4.092-5.448-5.977z"/></g></svg>									<span>Customize</span>
								</a>
							</li>
																<li class="actnbr-folded-follow">
												<a class="actnbr-action actnbr-actn-follow  no-display" href="">
			<svg class="gridicon" height="20" width="20" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path clip-rule="evenodd" d="m4 4.5h12v6.5h1.5v-6.5-1.5h-1.5-12-1.5v1.5 10.5c0 1.1046.89543 2 2 2h7v-1.5h-7c-.27614 0-.5-.2239-.5-.5zm10.5 2h-9v1.5h9zm-5 3h-4v1.5h4zm3.5 1.5h-1v1h1zm-1-1.5h-1.5v1.5 1 1.5h1.5 1 1.5v-1.5-1-1.5h-1.5zm-2.5 2.5h-4v1.5h4zm6.5 1.25h1.5v2.25h2.25v1.5h-2.25v2.25h-1.5v-2.25h-2.25v-1.5h2.25z"  fill-rule="evenodd"></path></svg>
			<span>Subscribe</span>
		</a>
		<a class="actnbr-action actnbr-actn-following " href="">
			<svg class="gridicon" height="20" width="20" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path fill-rule="evenodd" clip-rule="evenodd" d="M16 4.5H4V15C4 15.2761 4.22386 15.5 4.5 15.5H11.5V17H4.5C3.39543 17 2.5 16.1046 2.5 15V4.5V3H4H16H17.5V4.5V12.5H16V4.5ZM5.5 6.5H14.5V8H5.5V6.5ZM5.5 9.5H9.5V11H5.5V9.5ZM12 11H13V12H12V11ZM10.5 9.5H12H13H14.5V11V12V13.5H13H12H10.5V12V11V9.5ZM5.5 12H9.5V13.5H5.5V12Z" fill="#008A20"></path><path class="following-icon-tick" d="M13.5 16L15.5 18L19 14.5" stroke="#008A20" stroke-width="1.5"></path></svg>
			<span>Subscribed</span>
		</a>
										</li>
																	<li class="actnbr-theme">
										<a href="https://wordpress.com/theme/morden/">Get theme: Morden</a>
									</li>
																	<li class="actnbr-shortlink"><a href="https://wp.me/sc0sD4-coder">Copy shortlink</a></li>
																	<li class="actnbr-reader">
										<a href="https://wordpress.com/read/blogs/177426086/posts/2078">
											View post in Reader										</a>
									</li>
																	<li class="actnbr-follows">
										<a href="https://wordpress.com/following/manage?s=importdotexport.wordpress.com">
											Manage subscriptions										</a>
									</li>
																		<li class="actnbr-fold"><a href="">Collapse this bar</a></li>
															</ul>
					</div>
				</div>
			</li>
		</ul>
	</div>
	
<script>
window.addEventListener( "load", function( event ) {
	var link = document.createElement( "link" );
	link.href = "https://s0.wp.com/wp-content/mu-plugins/actionbar/actionbar.css?v=20231122";
	link.type = "text/css";
	link.rel = "stylesheet";
	document.head.appendChild( link );

	var script = document.createElement( "script" );
	script.src = "https://s0.wp.com/wp-content/mu-plugins/actionbar/actionbar.js?v=20231122";
	script.defer = true;
	document.body.appendChild( script );
} );
</script>

	
	<script type="text/javascript">
		window.WPCOM_sharing_counts = {"https:\/\/importdotexport.wordpress.com\/2024\/01\/11\/coder\/":2078};
	</script>
							<script type="text/javascript">
				( function () {
					var currentScript = document.currentScript;

					// Helper function to load an external script.
					function loadScript( url, cb ) {
						var script = document.createElement( 'script' );
						var prev = currentScript || document.getElementsByTagName( 'script' )[ 0 ];
						script.setAttribute( 'async', true );
						script.setAttribute( 'src', url );
						prev.parentNode.insertBefore( script, prev );
						script.addEventListener( 'load', cb );
					}

					function init() {
						loadScript( 'https://platform.linkedin.com/in.js?async=true', function () {
							if ( typeof IN !== 'undefined' ) {
								IN.init();
							}
						} );
					}

					if ( document.readyState === 'loading' ) {
						document.addEventListener( 'DOMContentLoaded', init );
					} else {
						init();
					}

					document.body.addEventListener( 'is.post-load', function() {
						if ( typeof IN !== 'undefined' ) {
							IN.parse();
						}
					} );
				} )();
			</script>
						<script id="tumblr-js" type="text/javascript" src="https://assets.tumblr.com/share-button.js"></script>
						<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0],p=/^http:/.test(d.location)?'http':'https';if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=p+'://platform.twitter.com/widgets.js';fjs.parentNode.insertBefore(js,fjs);}}(document, 'script', 'twitter-wjs');</script>
								<script type="text/javascript">
				( function () {
					// Pinterest shared resources
					var s = document.createElement( 'script' );
					s.type = 'text/javascript';
					s.async = true;
					s.setAttribute( 'data-pin-hover', true );					s.src = window.location.protocol + '//assets.pinterest.com/js/pinit.js';
					var x = document.getElementsByTagName( 'script' )[ 0 ];
					x.parentNode.insertBefore(s, x);
					// if 'Pin it' button has 'counts' make container wider
					function init() {
						var shares = document.querySelectorAll( 'li.share-pinterest' );
						for ( var i = 0; i < shares.length; i++ ) {
							var share = shares[ i ];
							var countElement = share.querySelector( 'a span' );
							if (countElement) {
								var countComputedStyle = window.getComputedStyle(countElement);
								if ( countComputedStyle.display === 'block' ) {
									var countWidth = parseInt( countComputedStyle.width, 10 );
									share.style.marginRight = countWidth + 11 + 'px';
								}
							}
						}
					}

					if ( document.readyState !== 'complete' ) {
						document.addEventListener( 'load', init );
					} else {
						init();
					}
				} )();
			</script>
					<div id="fb-root"></div>
			<script>(function(d, s, id) { var js, fjs = d.getElementsByTagName(s)[0]; if (d.getElementById(id)) return; js = d.createElement(s); js.id = id; js.src = 'https://connect.facebook.net/fr_FR/sdk.js#xfbml=1&amp;appId=249643311490&version=v2.3'; fjs.parentNode.insertBefore(js, fjs); }(document, 'script', 'facebook-jssdk'));</script>
			<script>
			document.body.addEventListener( 'is.post-load', function() {
				if ( 'undefined' !== typeof FB ) {
					FB.XFBML.parse();
				}
			} );
			</script>
					<script>
		( function () {
			var currentScript = document.currentScript;

			// Don't use Pocket's default JS as it we need to force init new Pocket share buttons loaded via JS.
			function jetpack_sharing_pocket_init() {
				var script = document.createElement( 'script' );
				var prev = currentScript || document.getElementsByTagName( 'script' )[ 0 ];
				script.setAttribute( 'async', true );
				script.setAttribute( 'src', 'https://widgets.getpocket.com/v1/j/btn.js?v=1' );
				prev.parentNode.insertBefore( script, prev );
			}

			if ( document.readyState === 'loading' ) {
				document.addEventListener( 'DOMContentLoaded', jetpack_sharing_pocket_init );
			} else {
				jetpack_sharing_pocket_init();
			}
			document.body.addEventListener( 'is.post-load', jetpack_sharing_pocket_init );
		} )();
		</script>
			<script type="text/javascript" id="comment-like-js-extra">
/* <![CDATA[ */
var comment_like_text = {"loading":"chargement\u2026","swipeUrl":"https:\/\/s0.wp.com\/wp-content\/mu-plugins\/comment-likes\/js\/lib\/swipe.js?ver=20131008"};
/* ]]> */
</script>
<script type="text/javascript" id="wordads-preview-js-extra">
/* <![CDATA[ */
var wordads_preview = {"ajaxurl":"https:\/\/importdotexport.wordpress.com\/wp-admin\/admin-ajax.php","blog_id":"177426086","user":"startexpor","nonce":"3a26dce39d"};
/* ]]> */
</script>
<script type="text/javascript" id="sharing-js-js-extra">
/* <![CDATA[ */
var sharing_js_options = {"lang":"en","counts":"1","is_stats_active":"1"};
/* ]]> */
</script>
<script type="text/javascript" id="verbum-settings-js-before">
/* <![CDATA[ */
window.VerbumComments = {"Log in or provide your name and email to leave a reply.":"Connectez-vous ou indiquez votre nom et votre adresse e-mail pour laisser une r\u00e9ponse.","Receive web and mobile notifications for posts on this site.":"Recevez les notifications Web et mobiles relatives aux articles publi\u00e9s sur ce site.","Name":"Nom","Email (address never made public)":"Adresse e-mail (adresse strictement confidentielle)","Website (optional)":"Site Web (facultatif)","Leave a reply. (log in optional)":"Laissez une r\u00e9ponse. (connexion facultative)","Log in to leave a reply.":"Connectez-vous pour laisser une r\u00e9ponse.","Logged in via %s":"Connect\u00e9(e) via %s","Log out":"D\u00e9connexion","Email":"E-mail","(Address never made public)":"(adresse strictement confidentielle)","Instantly":"Instantan\u00e9ment","Daily":"Quotidien","Reply":"R\u00e9ponse","WordPress":"WordPress","Weekly":"Hebdomadaire","Notify me of new posts":"M\u2019informer des nouveaux articles","Email me new posts":"M\u2019informer des nouveaux articles par e-mail ","Email me new comments":"M\u2019envoyer de nouveaux commentaires par e-mail","Cancel":"Annuler","Write a comment...":"\u00c9crire un commentaire...","Website":"Site web","Optional":"Facultatif","We'll keep you in the loop!":"Nous vous tiendrons au courant\u00a0!","Loading your comment...":"Chargement de votre commentaire\u2026","Never miss a beat!":"Ne manquez rien\u00a0!","Interested in getting blog post updates? Simply click the button below to stay in the loop!":"Vous souhaitez \u00eatre au courant de la publication de nouveaux articles sur le blog\u00a0? Cliquez tout simplement sur le bouton ci-dessous pour rester au fait\u00a0!","Enter your email address":"Entrez votre adresse e-mail","Subscribe":"Souscrire","Comment sent successfully":"Commentaire envoy\u00e9 avec succ\u00e8s","Save my name, email, and website in this browser for the next time I comment.":"Enregistrer mon nom, mon e-mail et mon site Web dans le navigateur pour mon prochain commentaire.","siteId":177426086,"postId":2078,"mustLogIn":false,"requireNameEmail":true,"commentRegistration":false,"connectURL":"https:\/\/importdotexport.wordpress.com\/public.api\/connect\/?action=request","logoutURL":"https:\/\/importdotexport.wordpress.com\/wp-login.php?action=logout&_wpnonce=87f9614ae8","homeURL":"https:\/\/importdotexport.wordpress.com\/","subscribeToBlog":true,"subscribeToComment":true,"isJetpackCommentsLoggedIn":false,"jetpackUsername":"","jetpackUserId":0,"jetpackSignature":"","jetpackAvatar":"https:\/\/0.gravatar.com\/avatar\/?s=96&amp;d=identicon&amp;r=G","enableBlocks":false,"enableSubscriptionModal":false,"currentLocale":"fr","isJetpackComments":false,"allowedBlocks":["core\/paragraph","core\/list","core\/code","core\/list-item","core\/quote","core\/image","core\/embed","core\/quote","core\/code"],"embedNonce":"f32e5d3324","verbumBundleUrl":"https:\/\/s0.wp.com\/wp-content\/mu-plugins\/verbum\/dist\/index.js"}
/* ]]> */
</script>
<script crossorigin='anonymous' type='text/javascript' src='https://s0.wp.com/_static/??-eJx9UdtygyAQ/aEidpJp+tLpp3RW2OoiF8tCHP++aGLsZKxvsOey54AcB6GCT+iTdFkMNrfkWY6kW0wsMRc09ITCwigTusFCwqd5ZfhF7vtY6gv7J2PGDry2GFcyeWWzLqBh2YUrRlrEwnDlyO+xQBdANBD/EnZ2PngFV8GJTfe/puxvspPAPLfWkwdHStgAGo9kxd7NoW81zdNgr8RKiDjYaa9IY0O7fUOIGjQLZedki8E6GiJeCY/efnsHB5xKQYgiRVA9H4l6YodJnKpafpXgj8F3XMj6QGswDcX+fpec/c2iyWS15A4iluh6Wo7k23v9T/fxeqnP76dL/VabX0zC9Qw='></script>
<script type="text/javascript" id="sharing-js-js-after">
/* <![CDATA[ */
var windowOpen;
			( function () {
				function matches( el, sel ) {
					return !! (
						el.matches && el.matches( sel ) ||
						el.msMatchesSelector && el.msMatchesSelector( sel )
					);
				}

				document.body.addEventListener( 'click', function ( event ) {
					if ( ! event.target ) {
						return;
					}

					var el;
					if ( matches( event.target, 'a.share-telegram' ) ) {
						el = event.target;
					} else if ( event.target.parentNode && matches( event.target.parentNode, 'a.share-telegram' ) ) {
						el = event.target.parentNode;
					}

					if ( el ) {
						event.preventDefault();

						// If there's another sharing window open, close it.
						if ( typeof windowOpen !== 'undefined' ) {
							windowOpen.close();
						}
						windowOpen = window.open( el.getAttribute( 'href' ), 'wpcomtelegram', 'menubar=1,resizable=1,width=450,height=450' );
						return false;
					}
				} );
			} )();
var windowOpen;
			( function () {
				function matches( el, sel ) {
					return !! (
						el.matches && el.matches( sel ) ||
						el.msMatchesSelector && el.msMatchesSelector( sel )
					);
				}

				document.body.addEventListener( 'click', function ( event ) {
					if ( ! event.target ) {
						return;
					}

					var el;
					if ( matches( event.target, 'a.share-facebook' ) ) {
						el = event.target;
					} else if ( event.target.parentNode && matches( event.target.parentNode, 'a.share-facebook' ) ) {
						el = event.target.parentNode;
					}

					if ( el ) {
						event.preventDefault();

						// If there's another sharing window open, close it.
						if ( typeof windowOpen !== 'undefined' ) {
							windowOpen.close();
						}
						windowOpen = window.open( el.getAttribute( 'href' ), 'wpcomfacebook', 'menubar=1,resizable=1,width=600,height=400' );
						return false;
					}
				} );
			} )();
/* ]]> */
</script>
	<script>
	/(trident|msie)/i.test(navigator.userAgent)&&document.getElementById&&window.addEventListener&&window.addEventListener("hashchange",function(){var t,e=location.hash.substring(1);/^[A-z0-9_-]+$/.test(e)&&(t=document.getElementById(e))&&(/^(?:a|select|input|button|textarea)$/i.test(t.tagName)||(t.tabIndex=-1),t.focus())},!1);
	</script>
	
	<script type="text/javascript">
		(function () {
			var wpcom_reblog = {
				source: 'toolbar',

				toggle_reblog_box_flair: function (obj_id, post_id) {

					// Go to site selector. This will redirect to their blog if they only have one.
					const postEndpoint = `https://wordpress.com/post`;

					// Ideally we would use the permalink here, but fortunately this will be replaced with the 
					// post permalink in the editor.
					const originalURL = `${ document.location.href }?page_id=${ post_id }`; 
					
					const url =
						postEndpoint +
						'?url=' +
						encodeURIComponent( originalURL ) +
						'&is_post_share=true' +
						'&v=5';

					const redirect = function () {
						if (
							! window.open( url, '_blank' )
						) {
							location.href = url;
						}
					};

					if ( /Firefox/.test( navigator.userAgent ) ) {
						setTimeout( redirect, 0 );
					} else {
						redirect();
					}
				},
			};

			window.wpcom_reblog = wpcom_reblog;
		})();
	</script>
<script type="text/javascript">
// <![CDATA[
(function() {
try{
  if ( window.external &&'msIsSiteMode' in window.external) {
    if (window.external.msIsSiteMode()) {
      var jl = document.createElement('script');
      jl.type='text/javascript';
      jl.async=true;
      jl.src='/wp-content/plugins/ie-sitemode/custom-jumplist.php';
      var s = document.getElementsByTagName('script')[0];
      s.parentNode.insertBefore(jl, s);
    }
  }
}catch(e){}
})();
// ]]>
</script>	<iframe src='https://widgets.wp.com/likes/master.html?ver=20240111#ver=20240111&amp;lang=fr&amp;lang_ver=1704902759&amp;origin=https://importdotexport.wordpress.com&amp;n=1' scrolling='no' id='likes-master' name='likes-master' style='display:none;'></iframe>
	<div id='likes-other-gravatars' class='wpl-new-layout' role="dialog" aria-hidden="true" tabindex="-1">
		<div class="likes-text">
			<span>%d</span>		</div>
		<ul class="wpl-avatars sd-like-gravatars"></ul>
	</div>

		<script src="//stats.wp.com/w.js?66" defer></script> <script type="text/javascript">
_tkq = window._tkq || [];
_stq = window._stq || [];
_tkq.push(['identifyUser', 186149436, 'startexpor']);
_tkq.push(['storeContext', {'blog_id':'177426086','blog_tz':'0','user_lang':'en','blog_lang':'fr'}]);
_stq.push(['view', {'blog':'177426086','v':'wpcom','tz':'0','user':'1','user_id':'186149436','post':'2078','subd':'importdotexport'}]);
_stq.push(['extra', {'crypt':'UE5XaGUuOTlwaD85flAmcm1mcmZsaDhkV11YdWFnNncxc1tjZG9XVXhRUWsuSltdVUZYUVZqSU9FXXg2aDdLTnBkTmhhd2g5WGttVzdqSCx5WVlDXW9CdS9ES3xfS1JHSUlMbkdxbGRmZW8sZy9COHlLX3IsMiwsfjdOVklDP0grLj8xcVVfWzFvZml2K3ZqLl9fcE18djhsbC5ZVDNyX1hKNWVbRHwlV29JSWM9aEhWdUF+NEFlUnJUUU5fLmtJLHE3eGhmXXdtNXlic0k2ZktwTTRbOHBYZkZDNGk/QW9dVkg9Sy1UMGZSUlFJbFVkLXJYflpSJU9OY0hMMnFQdEEmZWtvMF89dWQmK2Fhd2g/VXJ+MHBTa2lJW3YyLzRbcjUwYXJrVllpSWRmP2FZaW9nbXRxWCs1ZEMyNCxwMkRQaDNbbnBWMA=='}]);
</script>
<noscript><img src="https://pixel.wp.com/b.gif?v=noscript" style="height:1px;width:1px;overflow:hidden;position:absolute;bottom:1px;" alt="" /></noscript>
<script defer id="bilmur" data-customproperties="{&quot;enq_jquery&quot;:&quot;1&quot;,&quot;logged_in&quot;:&quot;1&quot;,&quot;wptheme&quot;:&quot;pub\/morden&quot;,&quot;wptheme_is_block&quot;:&quot;0&quot;}" data-provider="wordpress.com" data-service="simple"  src="/wp-content/js/bilmur.min.js?i=11&m=202402"></script><div id="marketingbar" class="marketing-bar noskim  "><div class="marketing-bar-text">Supprimer cette bannière de site avec un plan payant</div><a class="marketing-bar-button" href="https://wordpress.com/plans/importdotexport.wordpress.com/?ref=marketing_bar&#038;utm_source=marketing-bar">Supprimer la bannière</a><a class="marketing-bar-link" tabindex="-1" aria-label="Créer un nouveau site sur WordPress.com" href="https://wordpress.com/plans/importdotexport.wordpress.com/?ref=marketing_bar&#038;utm_source=marketing-bar"></a></div>		<script type="text/javascript">
			window._tkq = window._tkq || [];
			document.querySelectorAll( '#marketingbar > a' ).forEach( link => {
				link.addEventListener( 'click', ( e ) => {
					window._tkq.push( [ 'recordEvent', 'wpcom_marketing_bar_cta_click', {"is_current_user_blog_owner":true} ] );
				} );
			});
		</script><script>
if ( 'object' === typeof wpcom_mobile_user_agent_info ) {

	wpcom_mobile_user_agent_info.init();
	var mobileStatsQueryString = "";
	
	if( false !== wpcom_mobile_user_agent_info.matchedPlatformName )
		mobileStatsQueryString += "&x_" + 'mobile_platforms' + '=' + wpcom_mobile_user_agent_info.matchedPlatformName;
	
	if( false !== wpcom_mobile_user_agent_info.matchedUserAgentName )
		mobileStatsQueryString += "&x_" + 'mobile_devices' + '=' + wpcom_mobile_user_agent_info.matchedUserAgentName;
	
	if( wpcom_mobile_user_agent_info.isIPad() )
		mobileStatsQueryString += "&x_" + 'ipad_views' + '=' + 'views';

	if( "" != mobileStatsQueryString ) {
		new Image().src = document.location.protocol + '//pixel.wp.com/g.gif?v=wpcom-no-pv' + mobileStatsQueryString + '&baba=' + Math.random();
	}
	
}
</script>
<script>
(function() {
	'use strict';

	const fetches = {};
	const promises = {};
	const urls = {
		'verbum': 'https://s0.wp.com/wp-content/mu-plugins/verbum/dist/index.js?m=1704973945i&ver=1704973945'
	};
	const loaders = {
		'verbum': () => {
			fetchExternalScript('verbum');
			promises['verbum'] = promises['verbum'] || loadWPScript('verbum');
			return promises['verbum'];
		},
		
	};
	const scriptExtras = {
		
	};

	window.WP_Enqueue_Dynamic_Script = {
		loadScript: (handle) => {
			if (!loaders[handle]) {
				console.error('WP_Enqueue_Dynamic_Script: unregistered script `' + handle + '`.');
			}
			return loaders[handle]();
		}
	};

	function fetchExternalScript(handle) {
		if (!urls[handle]) {
			return Promise.resolve();
		}

		fetches[handle] = fetches[handle] || fetch(urls[handle], { mode: 'no-cors' });
		return fetches[handle];
	}

	function runExtraScript(handle, type, index) {
		const id = 'wp-enqueue-dynamic-script:' + handle + ':' + type + ':' + (index + 1);
		const template = document.getElementById(id);
		if (!template) {
			return Promise.reject();
		}

		const script = document.createElement( 'script' );
		script.innerHTML = template.innerHTML;
		document.body.appendChild( script );
		return Promise.resolve();
	}

	function loadExternalScript(handle) {
		if (!urls[handle]) {
			return Promise.resolve();
		}

		return fetches[handle].then(() => {
			return new Promise((resolve, reject) => {
				const script = document.createElement('script');
				script.onload = () => resolve();
				script.onerror = (e) => reject(e);
				script.src = urls[handle];
				document.body.appendChild(script);
			});
		});
	}

	function loadExtra(handle, pos) {
		const count = (scriptExtras[handle] && scriptExtras[handle][pos]) || 0;
		let promise = Promise.resolve();

		for (let i = 0; i < count; i++) {
			promise = promise.then(() => runExtraScript(handle, pos, i));
		}

		return promise;
	}

	function loadWPScript(handle) {
		return loadExtra(handle, 'before')
			.then(() => loadExternalScript(handle))
			.then(() => loadExtra(handle, 'after'));
	}
} )();
</script>

</body>
</html>

