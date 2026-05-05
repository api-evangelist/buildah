---
title: "Buildah version 1.42.0 Release Announcement"
url: "https://buildah.io/releases/2025/10/22/Buildah-version-v1.42.0.html"
date: "2025-10-22T00:00:00+00:00"
author: "tsweeney"
feed_url: "https://buildah.io/feed.xml"
---
<p><img alt="buildah logo" src="https://buildah.io/images/buildah.png" /></p>

<h1 id="buildah-version-1420-release-announcement">Buildah version 1.42.0 Release Announcement</h1>

<p>We’re pleased to announce the release of <a href="https://github.com/containers/buildah">Buildah</a> <a href="https://github.com/containers/buildah/releases/tag/v1.42.0">version 1.42.0</a>, which is now available from GitHub for any Linux distro.  We are shipping this release on <a href="https://bodhi.fedoraproject.org/updates/FEDORA-2025-8a248ee4f4">Fedora 42</a>  and <a href="https://bodhi.fedoraproject.org/updates/FEDORA-2025-beb4c9a336">Fedora 43</a>.  Buildah will also be shipped on CentOS, OpenSUSE, and Ubuntu soon. In addition, container images will be available at https://quay.io/repository/buildah/stable and https://quay.io/repository/containers/buildah.</p>

<p>The Buildah project has continued to grow over the past several weeks, welcoming several new contributors to the mix.  This release features notable changes: 
<!--readmore --></p>
<ul>
  <li>The meaning of <code class="language-plaintext highlighter-rouge">--pull</code> now emulates Docker’s <code class="language-plaintext highlighter-rouge">--pull=always</code></li>
  <li>Destination locations for several commands that now end with a <code class="language-plaintext highlighter-rouge">/.</code> are treated as directories.</li>
  <li>The <code class="language-plaintext highlighter-rouge">--imagestore</code> option can now be used when configuring storage.</li>
  <li>The <code class="language-plaintext highlighter-rouge">--transient-store</code> option stores metadata about containers under the storage state directory.  See the buildah (1) man page for details.</li>
</ul>

<p>This release comprises changes made for v1.42.0 and will be included in Podman v5.7.</p>

<h2 id="release-changes">Release Changes</h2>
<h3 id="changes-for-v1420">Changes for v1.42.0</h3>
<ul>
  <li>Restore the meaning of <code class="language-plaintext highlighter-rouge">--pull</code> (without argument), similar to the docker behavior: now defaults to <code class="language-plaintext highlighter-rouge">--pull=always</code> by <a href="https://github.com/Romain-Geissler-1A">@Romain-Geissler-1A</a> in <a href="https://github.com/containers/buildah/pull/6300">#6300</a></li>
  <li>Exclude pulled up parent directories at commit-time by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6296">#6296</a></li>
  <li>Only suppress “noted” items when not squashing by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6302">#6302</a></li>
  <li>History should note unset-label, timestamp, and rewrite-timestamp by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6315">#6315</a></li>
  <li>–mount=type=bind now does ignores modtime when looking for cache candidates by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/6311">#6311</a></li>
  <li>Destination locations specified for <code class="language-plaintext highlighter-rouge">buildah add</code> and <code class="language-plaintext highlighter-rouge">buildah copy</code>, and in ADD and COPY instructions for <code class="language-plaintext highlighter-rouge">buildah build</code>, that end with “/.” are now always expected to be directories by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6310">#6310</a></li>
  <li>Run: reap stray processes by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6307">#6307</a></li>
  <li>imagebuildah.StageExecutor.Execute: commit more “no instructions” cases by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6314">#6314</a></li>
  <li>Rework how we decide what to filter out of layer diffs by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6332">#6332</a></li>
  <li>Mount image fails with imagestores by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6340">#6340</a></li>
  <li>Losen the dependency on go-connections/tlsconfig by <a href="https://github.com/mtrmac">@mtrmac</a> in <a href="https://github.com/containers/buildah/pull/6328">#6328</a></li>
  <li>The global <code class="language-plaintext highlighter-rouge">--imagestore</code> flag can now be used when configuring storage by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6341">#6341</a></li>
  <li>The global <code class="language-plaintext highlighter-rouge">--transient-store</code> flag is now recognized by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6346">#6346</a></li>
  <li>FROM instructions which reference images using both a tag and a digest no longer trigger errors in <code class="language-plaintext highlighter-rouge">buildah build</code> with <code class="language-plaintext highlighter-rouge">--all-platforms</code>: the tag portion of the reference will be ignored by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6353">#6353</a></li>
  <li>The chroot isolation handler should now correctly use $PATH to find the binary to run when RUN instructions express the command to run in exec form, and which do not do so using an absolute path by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6378">#6378</a></li>
  <li>Parent directories created for mounts used by <code class="language-plaintext highlighter-rouge">buildah run</code> or by RUN instructions in <code class="language-plaintext highlighter-rouge">buildah build</code> will be world-readable again by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6381">#6381</a></li>
  <li>commit: always return the config digest as the image ID by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6426">#6426</a></li>
  <li>copier: ignore user.overlay.* xattrs by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6429">#6429</a></li>
  <li>Include the Sequoia crypto backend, and run integration tests with it by <a href="https://github.com/mtrmac">@mtrmac</a> in <a href="https://github.com/containers/buildah/pull/6390">#6390</a></li>
  <li>
    <p>build,add: add support for corporate proxies by <a href="https://github.com/userid0x0">@userid0x0</a> in <a href="https://github.com/containers/buildah/pull/6274">#6274</a></p>
  </li>
  <li>Documentation:
    <ul>
      <li>Adding mohanboddu as community manager to MAINTAINERS.md by <a href="https://github.com/mohanboddu">@mohanboddu</a> in <a href="https://github.com/containers/buildah/pull/6339">#6339</a></li>
    </ul>
  </li>
  <li>Vendored (Note, storage, image and common move to go.podman.io during this release):
    <ul>
      <li>Vendor github.com/containers/common to v0.64.1</li>
      <li>Vendor github.com/containers/luksy digest to 2cf5bc9</li>
      <li>Vendor github.com/containers/image/v5 to v5.36.1</li>
      <li>Vendor github.com/containers/storage to v1.59.1</li>
      <li>Vendor github.com/cyphar/filepath-securejoin to v0.4.1</li>
      <li>Vendor github.com/docker/docker to v28.5.1+incompatible</li>
      <li>Vendor github.com/docker/go-connections to v0.6.0</li>
      <li>Vendor github.com/fsouza/go-dockerclient to v1.12.2</li>
      <li>Vendor github.com/moby/buildkit to v0.25.1</li>
      <li>Vendor github.com/opencontainers/cgroups to v0.0.5</li>
      <li>Vendor github.com/opencontainers/runc to v1.3.2</li>
      <li>Vendor github.com/openshift/imagebuilder to v1.2.19</li>
      <li>Vendor github.com/seccomp/libseccomp-golang to v0.11.1</li>
      <li>Vendor github.com/stretchr/testify to v1.11.1</li>
      <li>Vendor github.com/spf13/cobra to v1.10.1</li>
      <li>Vendor github.com/spf13/pflag to v1.0.10</li>
      <li>Vendor github.com/ulikunitz/xz to v0.5.15</li>
      <li>Vendor go.etcd.io/bbolt to v1.4.3</li>
      <li>Vendor go.podman.io/common to v0.66.0</li>
      <li>Vendor go.podman.io/image/v5 to v5.38.0</li>
      <li>Vendor go.podman.io/storage to v1.61.0</li>
      <li>Vendor golang.org/x/crypto to v0.43.0</li>
      <li>Vendor golang.org/x/sys to v0.37.0</li>
      <li>Vendor golang.org/x/term to v0.34.0</li>
    </ul>
  </li>
  <li>Tests:
    <ul>
      <li>CI: make runc tests non-blocking by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6286">#6286</a></li>
      <li>Make some test files different from each other by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6405">#6405</a></li>
    </ul>
  </li>
  <li>Changes to the build infrastructure:
    <ul>
      <li>Switch common, storage and image to monorepo. by <a href="https://github.com/jankaluza">@jankaluza</a> in <a href="https://github.com/containers/buildah/pull/6356">#6356</a></li>
      <li>Update to Go 1.24 by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6380">#6380</a></li>
      <li>.cirrus.yml: Test Vendoring bump golang by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/6386">#6386</a></li>
    </ul>
  </li>
</ul>

<p>New Contributors:</p>
<ul>
  <li><a href="https://github.com/Romain-Geissler-1A">@Romain-Geissler-1A</a> first contribution in <a href="https://github.com/containers/buildah/pull/6300">#6300</a></li>
  <li><a href="https://github.com/mohanboddu">@mohanboddu</a> made their first contribution in <a href="https://github.com/containers/buildah/pull/6274">#6339</a></li>
  <li><a href="https://github.com/jankaluza">@jankaluza</a> made their first contribution in <a href="https://github.com/containers/buildah/pull/6274">#6356</a></li>
  <li><a href="https://github.com/userid0x0">@userid0x0</a> made their first contribution in <a href="https://github.com/containers/buildah/pull/6274">#6274</a></li>
</ul>

<h2 id="try-it-out">Try it Out.</h2>

<p>If you haven’t yet, <a href="https://github.com/containers/buildah/blob/master/install.md">install Buildah</a> from one of the Linux repos or GitHub and give it a spin. We’re betting you’ll find it’s an easy and quick way to build containers in your environment without a daemon being involved!</p>

<p>For those of you who contributed to this release, thank you very much for your contributions! If you haven’t joined our community yet, don’t wait any longer! Come join us on GitHub, where Open Source communities live.</p>

<h2 id="buildah--simplicity">Buildah == Simplicity</h2>
