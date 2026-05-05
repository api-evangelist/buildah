---
title: "Buildah version 1.39.0 Release Announcement"
url: "https://buildah.io/releases/2025/02/03/Buildah-version-v1.39.0.html"
date: "2025-02-03T00:00:00+00:00"
author: "tsweeney"
feed_url: "https://buildah.io/feed.xml"
---
<p><img alt="buildah logo" src="https://buildah.io/images/buildah.png" /></p>

<h1 id="buildah-version-1390-release-announcement">Buildah version 1.39.0 Release Announcement</h1>

<p>We’re pleased to announce the release of <a href="https://github.com/containers/buildah">Buildah</a> <a href="https://github.com/containers/buildah/releases/tag/v1.39.0">version 1.39.0</a>, which is now available from GitHub for any Linux distro.  We are shipping this release on Fedora 40 and Fedora 41.  Buildah will also be shipped on CentOS, OpenSUSE, and Ubuntu soon. In addition, container images will be available at https://quay.io/repository/buildah/stable and https://quay.io/repository/containers/buildah.</p>

<p>The Buildah project has continued to grow over the past several weeks, welcoming several new contributors to the mix.  This release features notable changes: 
<!--readmore --></p>
<ul>
  <li>An <code class="language-plaintext highlighter-rouge">--artifact-annotation</code> option has been added to the <code class="language-plaintext highlighter-rouge">manifest add</code> command to allow for annotation of the artifact manifest.</li>
  <li>Cache now works when additional build context is used as the source of –mount.</li>
  <li>The <code class="language-plaintext highlighter-rouge">build</code> command has two new options, –security-opt mask and unmask.</li>
  <li>The <code class="language-plaintext highlighter-rouge">buildah build</code> RUN instructions and <code class="language-plaintext highlighter-rouge">buildah run</code> command can now refer to images with the <code class="language-plaintext highlighter-rouge">from</code> argument when using the <code class="language-plaintext highlighter-rouge">--mount=type=cache</code> option.</li>
</ul>

<p>This release comprises changes made for v1.39.0 and will be included in Podman v5.4.</p>

<h2 id="release-changes">Release Changes</h2>
<h3 id="changes-for-v1390">Changes for v1.39.0</h3>
<ul>
  <li>executor: allow to specify –no-pivot-root by <a href="https://github.com/giuseppe">@giuseppe</a> <a href="https://github.com/containers/buildah/pull/5838">#5838</a></li>
  <li>The <code class="language-plaintext highlighter-rouge">buildah manifest add</code> command now includes a <code class="language-plaintext highlighter-rouge">--artifact-annotation</code> flag which can be used to add an annotation to the artifact manifest which is generated and then added to the image index. by <a href="https://github.com/nalind">@nalind</a> <a href="https://github.com/containers/buildah/pull/5854">#5854</a></li>
  <li>The <code class="language-plaintext highlighter-rouge">buildah build</code> or <code class="language-plaintext highlighter-rouge">buildah run</code> with <code class="language-plaintext highlighter-rouge">--isolation chroot</code> will now default to using pivot_root() internally, unless the <code class="language-plaintext highlighter-rouge">--no-pivot</code> CLI flag is used. by <a href="https://github.com/nalind">@nalind</a> <a href="https://github.com/containers/buildah/pull/5874">#5874</a></li>
  <li>Cache now works when additional build context is used as the source of –mount by <a href="https://github.com/flouthoc">@flouthoc</a> <a href="https://github.com/containers/buildah/pull/5693">#5693</a></li>
  <li>Allow cache mounts to be stages and additional build contexts by <a href="https://github.com/nalind">@nalind</a> <a href="https://github.com/containers/buildah/pull/5897">#5897</a></li>
  <li>The <code class="language-plaintext highlighter-rouge">build</code> command has two new options, –security-opt mask and unmask.  Refer to the `build(1) man page for more information by <a href="https://github.com/rhatdan">@rhatdan</a> <a href="https://github.com/containers/buildah/pull/5883">#5883</a></li>
  <li>Add more checks to the –mount flag parsing logic by <a href="https://github.com/nalind">@nalind</a> <a href="https://github.com/containers/buildah/pull/5925">#5925</a></li>
  <li>Refactor: replace golang.org/x/exp with stdlib by <a href="https://github.com/Juneezee">@Juneezee</a> <a href="https://github.com/containers/buildah/pull/5937">#5937</a></li>
  <li>Changes were made to more thoroughly unmount images by <a href="https://github.com/nalind">@nalind</a> <a href="https://github.com/containers/buildah/pull/5924">#5924</a></li>
  <li>The <code class="language-plaintext highlighter-rouge">buildah build</code> RUN instructions and <code class="language-plaintext highlighter-rouge">buildah run</code> command can now refer to images with the <code class="language-plaintext highlighter-rouge">from</code> argument when using the <code class="language-plaintext highlighter-rouge">--mount=type=cache</code> option. by <a href="https://github.com/nalind">@nalind</a> <a href="https://github.com/containers/buildah/pull/5934">#5934</a></li>
  <li>The <code class="language-plaintext highlighter-rouge">build</code> and <code class="language-plaintext highlighter-rouge">run</code> commands now record hash or digest in the image history for sources used in <code class="language-plaintext highlighter-rouge">--mount</code>. by <a href="https://github.com/flouthoc">@flouthoc</a> <a href="https://github.com/containers/buildah/pull/5691">#5691</a></li>
</ul>

<h3 id="overall-miscellaneous-changes">Overall Miscellaneous Changes</h3>
<ul>
  <li>Documentation:
    <ul>
      <li>Fixed a broken doc link by <a href="https://github.com/cheesesashimi">@cheesesashimi</a> <a href="https://github.com/containers/buildah/pull/5936">#5936</a></li>
    </ul>
  </li>
  <li>Vendored:
    <ul>
      <li>Vendor in github.com/containers/common to v0.62.0</li>
      <li>Vendor in github.com/containers/image to v5.34.0</li>
      <li>Vendor in github.com/containers/luksy digest to a3a812d</li>
      <li>Vendor in github.com/containers/ocicrypt to v1.2.1</li>
      <li>Vendor in github.com/containers/storage to v1.57.1</li>
      <li>Vendor in github.com/cyphar/filepath-securejoin to v0.3.6</li>
      <li>Vendor in github.com/docker/docker to v27.5.1</li>
      <li>Vendor in github.com/moby/buildkit to v0.19.0</li>
      <li>Vendor in github.com/moby/sys/capability to v0.4.8</li>
      <li>Vendor in github.com/opencontainers/runc to v1.2.4</li>
      <li>Vendor in github.com/opencontainers/runtime-tools digest to f7e3563b0271</li>
      <li>Vendor in github.com/stretchr/testify to v1.10.0</li>
      <li>Vendor in github.com/vbatts/tar-split to v0.11.7.</li>
      <li>Vendor in golang.org/x/crypto to v0.32.0</li>
      <li>Vendor in golang.org/x/exp digest to 7d7fa50e5329</li>
      <li>Vendor in golang.org/x/net to v0.34.0</li>
    </ul>
  </li>
  <li>Tests
    <ul>
      <li>Make _prefetch() parallel-safe by <a href="https://github.com/edsantiago">@edsantiago</a> <a href="https://github.com/containers/buildah/pull/5841">#5841</a></li>
      <li>Parallelize some bats tests by <a href="https://github.com/edsantiago">@edsantiago</a> <a href="https://github.com/containers/buildah/pull/5552">#5552</a></li>
      <li>copy-preserving-extended-attributes: use a different base image by <a href="https://github.com/nalind">@nalind</a> <a href="https://github.com/containers/buildah/pull/5901">#5901</a></li>
      <li>chroot mount flags integration test: copy binaries by <a href="https://github.com/nalind">@nalind</a> <a href="https://github.com/containers/buildah/pull/5926">#5926</a></li>
    </ul>
  </li>
  <li>Changes to the build infrastructure
    <ul>
      <li>CI VMs: bump again by <a href="https://github.com/edsantiago">@edsantiago</a> <a href="https://github.com/containers/buildah/pull/5833">#5833</a></li>
      <li>Finish updating to go 1.22 by <a href="https://github.com/nalind">@nalind</a> <a href="https://github.com/containers/buildah/pull/5835">#5835</a></li>
      <li>Makefile cleanups by <a href="https://github.com/kolyshkin">@kolyshkin</a> <a href="https://github.com/containers/buildah/pull/5832">#5832</a></li>
      <li>Makefile: list sources via find conditionally by <a href="https://github.com/danishprakash">@danishprakash</a> <a href="https://github.com/containers/buildah/pull/5807">#5807</a></li>
      <li>Packit: f39 and rhel cleanups by <a href="https://github.com/lsm5">@lsm5</a> <a href="https://github.com/containers/buildah/pull/5849">#5849</a></li>
      <li>CI: remove some inter-job dependencies, run cross-compile task with make -j, use /tmp for Go build cache by <a href="https://github.com/nalind">@nalind</a> <a href="https://github.com/containers/buildah/pull/5856">#5856</a></li>
      <li>New VM Images by <a href="https://github.com/Luap99">@Luap99</a> <a href="https://github.com/containers/buildah/pull/5900">#5900</a></li>
      <li>RPM: use default gobuild macro on RHEL by <a href="https://github.com/lsm5">@lsm5</a> <a href="https://github.com/containers/buildah/pull/5938">#5938</a></li>
      <li>CI, .cirrus: parallelize containerized integration by <a href="https://github.com/flouthoc">@flouthoc</a> <a href="https://github.com/containers/buildah/pull/5947">#5947</a></li>
    </ul>
  </li>
  <li>Plus a few minor fixes.</li>
</ul>

<h2 id="try-it-out">Try it Out.</h2>

<p>If you haven’t yet, <a href="https://github.com/containers/buildah/blob/master/install.md">install Buildah</a> from one of the Linux repos or GitHub and give it a spin. We’re betting you’ll find it’s an easy and quick way to build containers in your environment without a daemon being involved!</p>

<p>For those of you who contributed to this release, thank you very much for your contributions! If you haven’t joined our community yet, don’t wait any longer! Come join us on GitHub, where Open Source communities live.</p>

<h2 id="buildah--simplicity">Buildah == Simplicity</h2>
