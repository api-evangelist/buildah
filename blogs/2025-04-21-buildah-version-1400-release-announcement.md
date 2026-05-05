---
title: "Buildah version 1.40.0 Release Announcement"
url: "https://buildah.io/releases/2025/04/21/Buildah-version-v1.40.0.html"
date: "2025-04-21T00:00:00+00:00"
author: "tsweeney"
feed_url: "https://buildah.io/feed.xml"
---
<p><img alt="buildah logo" src="https://buildah.io/images/buildah.png" /></p>

<h1 id="buildah-version-1400-release-announcement">Buildah version 1.40.0 Release Announcement</h1>

<p>We’re pleased to announce the release of <a href="https://github.com/containers/buildah">Buildah</a> <a href="https://github.com/containers/buildah/releases/tag/v1.40.0">version 1.40.0</a>, which is now available from GitHub for any Linux distro.  We are shipping this release on Fedora 41 and Fedora 42.  Buildah will also be shipped on CentOS, OpenSUSE, and Ubuntu soon. In addition, container images will be available at https://quay.io/repository/buildah/stable and https://quay.io/repository/containers/buildah.</p>

<p>The Buildah project has continued to grow over the past several weeks, welcoming several new contributors to the mix.  This release features notable changes: 
<!--readmore --></p>
<ul>
  <li>The <code class="language-plaintext highlighter-rouge">--inherit-labels</code> option has been added to inherit labels from the base image, or not.</li>
  <li>Add a <code class="language-plaintext highlighter-rouge">--parents</code> option for the <code class="language-plaintext highlighter-rouge">COPY</code> command to preserve leading directories in the paths of items being copied, relative to either the top of the build context, or to the “pivot point”.</li>
  <li>The <code class="language-plaintext highlighter-rouge">--timestamp option</code>, if set, is now passed through to a destination of <code class="language-plaintext highlighter-rouge">--tag=oci-archive</code> and is applied to the timestamp of entries in the tar archive</li>
</ul>

<p>This release comprises changes made for v1.40.0 and will be included in Podman v5.5.</p>

<h2 id="release-changes">Release Changes</h2>
<h3 id="changes-for-v1400">Changes for v1.40.0</h3>
<ul>
  <li>Bump Buildah to v1.39.0, c/storage v1.57.1, c/image v5.34.0, c/common v0.62.0 by <a href="https://github.com/TomSweeneyRedHat">@TomSweeneyRedHat</a> in <a href="https://github.com/containers/buildah/pull/5962">#5962</a>
    *The host directory used when a <code class="language-plaintext highlighter-rouge">buildah build</code> RUN instruction or <code class="language-plaintext highlighter-rouge">buildah run</code> uses the <code class="language-plaintext highlighter-rouge">--mount=type=cache</code> option is now chosen based not only on its “target” or “id” value, but also on the combination of “uid” and “gid” flag values specified, by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/5978">#5978</a></li>
  <li>Better support for the containers.conf container_name_as_hostname option by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/5943">#5943</a></li>
  <li>Better validation of manifest and expected digests by <a href="https://github.com/mtrmac">@mtrmac</a> in <a href="https://github.com/containers/buildah/pull/6014">#6014</a></li>
  <li>stage_executor: history now correctly includes the heredoc summary by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/6041">#6041</a></li>
  <li>Add <code class="language-plaintext highlighter-rouge">--parents</code> option for the <code class="language-plaintext highlighter-rouge">COPY</code> command to preserve leading directories in the paths of items being copied, relative to either the top of the build context, or to the “pivot point” by <a href="https://github.com/Honny1">@Honny1</a> in <a href="https://github.com/containers/buildah/pull/6008">#6008</a></li>
  <li>The  /proc/interrupts and /sys/devices/system/cpu/*/thermal_throttle are thermal paths are masked by default by <a href="https://github.com/giuseppe">@giuseppe</a> in <a href="https://github.com/containers/buildah/pull/6074">#6074</a></li>
  <li>Fix built-in args on ARM64 by <a href="https://github.com/Honny1">@Honny1</a> in <a href="https://github.com/containers/buildah/pull/6076">#6076</a></li>
  <li>The –timestamp option, if set, is now passed through to a destination of –tag=oci-archive: and is applied to the timestamp of entries in the tar archive by <a href="https://github.com/aeijdenberg">@aeijdenberg</a> in <a href="https://github.com/containers/buildah/pull/6023">#6023</a></li>
  <li>“chroot” isolation should no longer require the “–no-pivot” flag be specified in order to function on “image mode” systems. by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6088">#6088</a></li>
  <li>Fixed a bug to add: correctly resolve git tags and branches and report errors if no reference is found by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/6087">#6087</a></li>
  <li>Fixed a bug in processing Windows style paths by <a href="https://github.com/danegsta">@danegsta</a> in <a href="https://github.com/containers/buildah/pull/6083">#6083</a></li>
  <li>Return status 125 when a git operation fails instead of relaying the error code directly from git by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/6092">#6092</a></li>
  <li>The build process now resets the platform in systemcontext for every stage by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/5971">#5971</a></li>
  <li>Allow users to choose if they want to inherit labels from the base image by using –inherit-labels option  by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/6103">#6103</a></li>
  <li>Certain errors encountered when calling <code class="language-plaintext highlighter-rouge">mount()</code> while using “chroot” isolation will now use mount flag names in error diagnostic messages by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6129">#6129</a></li>
  <li>A bug was fixed to close files after a build properly by <a href="https://github.com/aeijdenberg">@aeijdenberg</a> in <a href="https://github.com/containers/buildah/pull/6047">#6047</a></li>
</ul>

<h3 id="overall-miscellaneous-changes">Overall Miscellaneous Changes</h3>
<ul>
  <li>Documentation:
    <ul>
      <li>Switch to the CNCF Code of Conduct by <a href="https://github.com/mheon">@mheon</a> in <a href="https://github.com/containers/buildah/pull/5982">#5982</a></li>
      <li>buildah-build.1.md: secret examples by <a href="https://github.com/hdub-tech">@hdub-tech</a> in <a href="https://github.com/containers/buildah/pull/5999">#5999</a></li>
      <li>Add a link to project governance and MAINTAINERS file by <a href="https://github.com/mheon">@mheon</a> in <a href="https://github.com/containers/buildah/pull/6108">#6108</a></li>
      <li>[CI:DOCS] Document rw/src for –mount in buildah-run(1) by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6127">#6127</a></li>
      <li>Update Buildah issue template to new version and support podman build by <a href="https://github.com/ninja-quokka">@ninja-quokka</a> in <a href="https://github.com/containers/buildah/pull/6099">#6099</a></li>
    </ul>
  </li>
  <li>Vendored:
    <ul>
      <li>Update to Go 1.23 for vendoring</li>
      <li>Vendor in containers/automation_images to v20250324</li>
      <li>Vendor in dependency golangci/golangci-lint to v2.1.0</li>
      <li>Vendor in github.com/containernetworking/cni to v1.3.0</li>
      <li>Vendor in github.com/containers/common to v0.62.2</li>
      <li>Vendor in github.com/containers/image/v5 to v5.34.2</li>
      <li>Vendor in github.com/containers/luksy digest to 40bd943</li>
      <li>Vendor in github.com/opencontainers/selinux to v1.12.0</li>
      <li>Vendor in github.com/containers/storage to v1.58.0</li>
      <li>Vendor in github.com/docker/docker to v28.1.0+incompatible</li>
      <li>Vendor in github.com/go-jose/go-jose/v4 to v4.0.5</li>
      <li>Vendor in github.com/moby/buildkit to v0.21.0</li>
      <li>Vendor in github.com/opencontainers/image-spec</li>
      <li>Vendor in github.com/opencontainers/runc to v1.2.6</li>
      <li>Vendor in github.com/opencontainers/runtime-spec to v1.2.1</li>
      <li>Vendor in github.com/opencontainers/runtime-tools digest to 260e151</li>
      <li>Vendor in github.com/openshift/imagebuilder digest to e87e4e1</li>
      <li>Vendor in github.com/spf13/cobra to v1.9.0</li>
      <li>Vendor in golang.org/x/crypto to v0.37.0</li>
      <li>Vendor in golang.org/x/net to v0.36.0 [security]</li>
      <li>Vendor in golang.org/x/sync to v0.11.0</li>
      <li>Vendor in golang.org/x/sys to v0.30.0</li>
      <li>Vendor in golang.org/x/term to v0.29.0</li>
      <li>Vendor in tags.cncf.io/container-device-interface to v1.0.1</li>
    </ul>
  </li>
  <li>Tests
    <ul>
      <li>tests/conformance/testdata/Dockerfile.add: update some URLs by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6012">#6012</a></li>
      <li>conformance: make TestCommit and TestConformance parallel by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/5995">#5995</a></li>
      <li>Fix Conformance tests on ARM64 by <a href="https://github.com/Honny1">@Honny1</a> in <a href="https://github.com/containers/buildah/pull/5990">#5990</a></li>
      <li>[skip-ci] TMT: system tests by <a href="https://github.com/lsm5">@lsm5</a> in <a href="https://github.com/containers/buildah/pull/5885">#5885</a></li>
    </ul>
  </li>
  <li>Changes to the build infrastructure
    <ul>
      <li>CI: parallize unit tests by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/5954">#5954</a></li>
      <li>Use tmpfs for integration tests by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/5959">#5959</a></li>
      <li>.cirrus: bump ci resources by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/5979">#5979</a></li>
      <li>cirrus: reduce task timeout by <a href="https://github.com/Luap99">@Luap99</a> in <a href="https://github.com/containers/buildah/pull/5994">#5994</a></li>
      <li>github: remove cirrus rerun action by <a href="https://github.com/Luap99">@Luap99</a> in <a href="https://github.com/containers/buildah/pull/6063">#6063</a></li>
      <li>github: check_cirrus_cron work around github bug by <a href="https://github.com/Luap99">@Luap99</a> in <a href="https://github.com/containers/buildah/pull/6120">#6120</a></li>
      <li>github: disable cron rerun action by <a href="https://github.com/Luap99">@Luap99</a> in <a href="https://github.com/containers/buildah/pull/6036">#6036</a></li>
      <li>cirrus: make Total Success wait for rootless integration by <a href="https://github.com/Luap99">@Luap99</a> in <a href="https://github.com/containers/buildah/pull/6130">#6130</a></li>
    </ul>
  </li>
  <li>Plus a few minor fixes.</li>
</ul>

<h2 id="try-it-out">Try it Out.</h2>

<p>If you haven’t yet, <a href="https://github.com/containers/buildah/blob/master/install.md">install Buildah</a> from one of the Linux repos or GitHub and give it a spin. We’re betting you’ll find it’s an easy and quick way to build containers in your environment without a daemon being involved!</p>

<p>For those of you who contributed to this release, thank you very much for your contributions! If you haven’t joined our community yet, don’t wait any longer! Come join us on GitHub, where Open Source communities live.</p>

<h2 id="buildah--simplicity">Buildah == Simplicity</h2>
