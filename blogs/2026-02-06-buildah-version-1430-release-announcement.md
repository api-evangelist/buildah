---
title: "Buildah version 1.43.0 Release Announcement"
url: "https://buildah.io/releases/2026/02/06/Buildah-version-v1.43.0.html"
date: "2026-02-06T00:00:00+00:00"
author: "tsweeney"
feed_url: "https://buildah.io/feed.xml"
---
<p><img alt="buildah logo" src="https://buildah.io/images/buildah.png" /></p>

<h1 id="buildah-version-1430-release-announcement">Buildah version 1.43.0 Release Announcement</h1>

<p>We’re pleased to announce the release of <a href="https://github.com/containers/buildah">Buildah</a> <a href="https://github.com/containers/buildah/releases/tag/v1.43.0">version 1.43.0</a>, which is now available from GitHub for any Linux distro. We are shipping this release on Fedora 42 and Fedora 43. Buildah will also be shipped on CentOS, OpenSUSE, and Ubuntu soon. In addition, container images will be available at https://quay.io/repository/buildah/stable and https://quay.io/repository/containers/buildah.</p>

<p>The Buildah project has continued to grow over the past several weeks, welcoming several new contributors to the mix. This release features one notable change: 
<!--readmore --></p>
<ul>
  <li>Fixes for several runc CVEs and follow-on regressions.</li>
</ul>

<p>This release comprises changes made for v1.43.0 and will be included in Podman v5.8.</p>

<h2 id="release-changes">Release Changes</h2>
<h3 id="changes-for-v1430">Changes for v1.43.0</h3>
<ul>
  <li>[release-1.42] Bump runc to v1.3.4 to fix CVE-2025-31133, CVE-2025-52565, and CVE-2025-52881 and regression fixes to runc by <a href="https://github.com/TomSweeneyRedHat">@TomSweeneyRedHat</a> in <a href="https://github.com/containers/buildah/pull/6560">#6560</a></li>
  <li>[release-1.42] Run: don’t try to encode SystemContext with json by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6565">#6565</a></li>
  <li>
    <p>[release-1.42] chroot.bats(chroot with overlay root): ensure we can overlay by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6566">#6566</a></p>
  </li>
  <li>Vendored:
    <ul>
      <li>Vendor in github.com/opencontainers/runc v1.3.4</li>
    </ul>
  </li>
  <li>Tests</li>
  <li>[release-1.42] tests: use cached images instead of fedoraproject.org by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6667">#6667</a>
    <ul>
      <li>[release-1.42] test: do not untar archive into fs when checking file names by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6668">#6668</a></li>
    </ul>
  </li>
  <li>Changes to the build infrastructure
    <ul>
      <li>[release-1.42] fix(build): make –tag oci-archive:xxx.tar work with simple images by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6669">#6669</a> #6669</li>
    </ul>
  </li>
</ul>

<h3 id="full-changelog-httpsgithubcomcontainersbuildahcomparev1422v1430"><strong>Full Changelog</strong>: https://github.com/containers/buildah/compare/v1.42.2…v1.43.0</h3>

<h2 id="try-it-out">Try it Out.</h2>

<p>If you haven’t yet, <a href="https://github.com/containers/buildah/blob/master/install.md">install Buildah</a> from one of the Linux repos or GitHub and give it a spin. We’re betting you’ll find it’s an easy and quick way to build containers in your environment without a daemon being involved!</p>

<p>For those of you who contributed to this release, thank you very much for your contributions! If you haven’t joined our community yet, don’t wait any longer! Come join us on GitHub, where Open Source communities live.</p>

<h2 id="buildah--simplicity">Buildah == Simplicity</h2>
