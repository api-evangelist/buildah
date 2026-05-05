---
title: "Buildah version 1.41.0 Release Announcement"
url: "https://buildah.io/releases/2025/07/21/Buildah-version-v1.41.0.html"
date: "2025-07-21T00:00:00+00:00"
author: "tsweeney"
feed_url: "https://buildah.io/feed.xml"
---
<p><img alt="buildah logo" src="https://buildah.io/images/buildah.png" /></p>

<h1 id="buildah-version-1410-release-announcement">Buildah version 1.41.0 Release Announcement</h1>

<p>We’re pleased to announce the release of <a href="https://github.com/containers/buildah">Buildah</a> <a href="https://github.com/containers/buildah/releases/tag/v1.41.0">version 1.41.0</a>, which is now available from GitHub for any Linux distro.  We are shipping this release on Fedora 41 and Fedora 42.  Buildah will also be shipped on CentOS, OpenSUSE, and Ubuntu soon. In addition, container images will be available at https://quay.io/repository/buildah/stable and https://quay.io/repository/containers/buildah.</p>

<p>The Buildah project has continued to grow over the past several weeks, welcoming several new contributors to the mix.  This release features notable changes: 
<!--readmore --></p>
<ul>
  <li>A number of changes have been made to allow for “reproducible builds”, which, in specific scenarios, should reduce the pull time of images.</li>
  <li>The <code class="language-plaintext highlighter-rouge">--inherit-annotations</code>, <code class="language-plaintext highlighter-rouge">--source-date-epoch</code>, <code class="language-plaintext highlighter-rouge">--rewrite-timestamp</code>, and <code class="language-plaintext highlighter-rouge">--unsetannotation</code> commands have been added to the <code class="language-plaintext highlighter-rouge">build</code> command.  See the <code class="language-plaintext highlighter-rouge">build</code> man page for more details.</li>
  <li>The <code class="language-plaintext highlighter-rouge">--link</code> option on the <code class="language-plaintext highlighter-rouge">COPY</code> and <code class="language-plaintext highlighter-rouge">ADD</code> commands in a Containerfile now fully supports layered build caching.</li>
</ul>

<p>This release comprises changes made for v1.41.0 and will be included in Podman v5.6.</p>

<h2 id="release-changes">Release Changes</h2>
<h3 id="changes-for-v1410">Changes for v1.41.0</h3>
<ul>
  <li>Filter image only when necessary, which reduces overhead when creating images by <a href="https://github.com/hanwen-flow">@hanwen-flow</a> in <a href="https://github.com/containers/buildah/pull/6141">#6141</a></li>
  <li>Support label_users in buildah from containers.conf by <a href="https://github.com/rhatdan">@rhatdan</a> in <a href="https://github.com/containers/buildah/pull/6161">#6161</a></li>
  <li>Fix typo in comment by <a href="https://github.com/brawer">@brawer</a> in <a href="https://github.com/containers/buildah/pull/6167">#6167</a></li>
  <li>Refactor NewImageSource to add a manifest type abstraction by <a href="https://github.com/aaronlehmann">@aaronlehmann</a> in <a href="https://github.com/containers/buildah/pull/5743">#5743</a>
   *When using –layers buildah will select most recent layer in case of conflict by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/6171">#6171</a></li>
  <li>The <code class="language-plaintext highlighter-rouge">buildah build</code>’s “–output” option can now be specified multiple times by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6177">#6177</a></li>
  <li>The <code class="language-plaintext highlighter-rouge">buildah add</code> command now offers a “–timestamp” option by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6178">#6178</a></li>
  <li>Fixed the link to the Maintainers file by <a href="https://github.com/JayKayy">@JayKayy</a> in <a href="https://github.com/containers/buildah/pull/6187">#6187</a></li>
  <li>The <code class="language-plaintext highlighter-rouge">buildah build --add-host</code> option now automatically resolves host-gateway from a string by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/6188">#6188</a></li>
  <li>When the <code class="language-plaintext highlighter-rouge">--platform</code> option is not invoked, Buildah now uses the default platform.  When the <code class="language-plaintext highlighter-rouge">--platform</code> option is used, the platform information from the base image is now used  by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6190">#6190</a></li>
  <li>Ensure extendedGlob returns paths in lexical order to achieve a reproducible build by <a href="https://github.com/Honny1">@Honny1</a> in <a href="https://github.com/containers/buildah/pull/6169">#6169</a></li>
  <li>The <code class="language-plaintext highlighter-rouge">buildah commit</code> command now recognizes <code class="language-plaintext highlighter-rouge">--source-date-epoch</code> and <code class="language-plaintext highlighter-rouge">--rewrite-timestamp</code> options, which affect the dates recorded in the new image’s configuration and the timestamps on the contents of the new layer by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6189">#6189</a></li>
  <li>The <code class="language-plaintext highlighter-rouge">buildah build</code> command now recognizes the <code class="language-plaintext highlighter-rouge">--source-date-epoch</code> and <code class="language-plaintext highlighter-rouge">--rewrite-timestamp</code> options, which affect the dates recorded in the new image’s configuration and the timestamps on the contents of the new layers and content generated in response to the <code class="language-plaintext highlighter-rouge">--output</code> flag by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6208">#6208</a></li>
  <li>Added support for the ‘–unsetannotation’ option, which allows users to prevent inheriting a specific annotation from base image in the build and config commands by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/6195">#6195</a></li>
  <li>The <code class="language-plaintext highlighter-rouge">buildah build</code>  sets a fixed hostname for RUN instructions when invoked with the <code class="language-plaintext highlighter-rouge">--timestamp</code> or <code class="language-plaintext highlighter-rouge">--source-date-epoch</code> options.
When building or committing images with the <code class="language-plaintext highlighter-rouge">--timestamp</code> or <code class="language-plaintext highlighter-rouge">--source-date-epoch</code> options, the hostname, domain name, and name-of-container-which-was-committed will be set to fixed values by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6211">#6211</a>
   *The <code class="language-plaintext highlighter-rouge">buildah build</code> and <code class="language-plaintext highlighter-rouge">buildah commit</code> commands no longer sets/updates the <code class="language-plaintext highlighter-rouge">io.buildah.version</code> label by default when either the <code class="language-plaintext highlighter-rouge">--timestamp</code> or <code class="language-plaintext highlighter-rouge">--source-date-epoch</code> options are used by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6214">#6214</a></li>
  <li>Support zstd compression is now working in image commit by <a href="https://github.com/aaronlehmann">@aaronlehmann</a> in <a href="https://github.com/containers/buildah/pull/5452">#5452</a></li>
  <li>Added support for the <code class="language-plaintext highlighter-rouge">--inherit-annotations</code> command to the <code class="language-plaintext highlighter-rouge">build</code> command which allows users to specify if they want to inherit annotations from base image or not by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/6198">#6198</a></li>
  <li>The <code class="language-plaintext highlighter-rouge">buildah build</code> command no longer leave traces of mount targets used for RUN instructions in built images by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6233">#6233</a></li>
  <li>Images committed in OCI formats now default to including an “org.opencontainers.image.created” annotation by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6239">#6239</a></li>
  <li>The BUILDTAG btrfs_noversion flag has been removed as it is no longer effective by <a href="https://github.com/rahilarious">@rahilarious</a> in <a href="https://github.com/containers/buildah/pull/6267">#6267</a></li>
  <li>The <code class="language-plaintext highlighter-rouge">--link</code> option on the <code class="language-plaintext highlighter-rouge">COPY</code> and <code class="language-plaintext highlighter-rouge">ADD</code> commands in a Containerfile now fully support layered build caching by <a href="https://github.com/2004joshua">@2004joshua</a> in <a href="https://github.com/containers/buildah/pull/6240">#6240</a></li>
  <li>
    <p>The <code class="language-plaintext highlighter-rouge">build</code> command now makes sure that platform is considered correctly before using the potential image as cache candidate by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/6269">#6269</a></p>
  </li>
  <li>Documentation:
    <ul>
      <li>[CI:DOCS] update a couple of lists in the build man page by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6175">#6175</a></li>
      <li>[CI:DOCS] Add CNCF roadmap, touchup other CNCF files by <a href="https://github.com/TomSweeneyRedHat">@TomSweeneyRedHat</a> in <a href="https://github.com/containers/buildah/pull/6124">#6124</a></li>
      <li>[CI:DOCS] README.md: add openssf passing badge by <a href="https://github.com/lsm5">@lsm5</a> in <a href="https://github.com/containers/buildah/pull/6181">#6181</a></li>
      <li>docs: add –setopt “*.countme=false” to dnf examples by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6215">#6215</a></li>
      <li>Update Neil Smith’s GitHub username in MAINTAINERS.md by <a href="https://github.com/actionmancan">@actionmancan</a> in <a href="https://github.com/containers/buildah/pull/6248">#6248</a></li>
    </ul>
  </li>
  <li>Vendored:
    <ul>
      <li>Vendor in containers/automation_images to v20250422</li>
      <li>Vendor in github.com/containers/common to v0.63.0</li>
      <li>Vendor in github.com/containers/luksy digest to bc60f96</li>
      <li>Vendor in github.com/containers/image/v5 to v5.36.0</li>
      <li>Vendor in github.com/containers/storage to v1.59.0</li>
      <li>Vendor in github.com/docker/docker to v28.3.2+incompatible</li>
      <li>Vendor in github.com/fsouza/go-dockerclient to v1.12.1</li>
      <li>Vendor in github.com/go-viper/mapstructure/v2 to v2.3.0</li>
      <li>Vendor in github.com/moby/buildkit to v0.23.2</li>
      <li>Vendor in github.com/openshift/imagebuilder to v1.2.16</li>
      <li>Vendor in github.com/opencontainers/cgroups to v0.0.3</li>
      <li>Vendor in github.com/opencontainers/runc to v1.3.0</li>
      <li>Vendor in github.com/seccomp/libseccomp-golang to v0.11.0</li>
      <li>Vendor in go.etcd.io/bbolt to v1.4.2</li>
      <li>Vendor in golang.org/x/crypto to v0.40.0</li>
      <li>Vendor in golang.org/x/sync to v0.16.0</li>
      <li>Vendor in golang.org/x/term to v0.33.0</li>
    </ul>
  </li>
  <li>Tests
    <ul>
      <li>test/serve: fix a descriptor leak, add preliminary directory support by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6146">#6146</a></li>
      <li>commit-with-extra-files test: use $TEST_SCRATCH_DIR by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6231">#6231</a></li>
      <li>Add conditional release-checking system test by <a href="https://github.com/cevich">@cevich</a> in <a href="https://github.com/containers/buildah/pull/6243">#6243</a></li>
      <li>Update “bud with –cpu-shares” test, and rename it by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6271">#6271</a></li>
      <li>buildah: move passwd command to tests by <a href="https://github.com/flouthoc">@flouthoc</a> in <a href="https://github.com/containers/buildah/pull/6264">#6264</a></li>
    </ul>
  </li>
  <li>Changes to the build infrastructure
    <ul>
      <li>[skip-ci] Packit: Ignore ELN and CentOS Stream jobs by <a href="https://github.com/lsm5">@lsm5</a> in <a href="https://github.com/containers/buildah/pull/6172">#6172</a></li>
      <li>[skip-ci] Packit: set fedora-all after F40 EOL by <a href="https://github.com/lsm5">@lsm5</a> in <a href="https://github.com/containers/buildah/pull/6170">#6170</a></li>
      <li>Use Fedora 42 instead of 41 in that one conformance test by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6174">#6174</a></li>
      <li>[skip-ci] Packit: Disable osh_diff_scan by <a href="https://github.com/lsm5">@lsm5</a> in <a href="https://github.com/containers/buildah/pull/6164">#6164</a></li>
      <li>remove static nix build by <a href="https://github.com/Luap99">@Luap99</a> in <a href="https://github.com/containers/buildah/pull/6191">#6191</a></li>
      <li>Don’t BuildRequires: ostree-devel by <a href="https://github.com/mtrmac">@mtrmac</a> in <a href="https://github.com/containers/buildah/pull/6192">#6192</a></li>
      <li>dynamically link sqlite by <a href="https://github.com/Luap99">@Luap99</a> in <a href="https://github.com/containers/buildah/pull/6216">#6216</a></li>
      <li>CI: give the rootless test user some supplemental groups by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6227">#6227</a></li>
      <li>conformance: use mirrored frontend and base images by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6232">#6232</a></li>
      <li>CI: ensure rootless groups aren’t duplicates by <a href="https://github.com/nalind">@nalind</a> in <a href="https://github.com/containers/buildah/pull/6228">#6228</a></li>
      <li>Adjust a bud and run test as runc does not support keep-groups by <a href="https://github.com/ricardobranco777">@ricardobranco777</a> in <a href="https://github.com/containers/buildah/pull/6226">#6226</a></li>
    </ul>
  </li>
</ul>

<h3 id="new-contributors">New Contributors</h3>
<ul>
  <li><a href="https://github.com/hanwen-flow">@hanwen-flow</a> made their first contribution in <a href="https://github.com/containers/buildah/pull/6141">#6141</a></li>
  <li><a href="https://github.com/brawer">@brawer</a> made their first contribution in <a href="https://github.com/containers/buildah/pull/6167">#6167</a></li>
  <li><a href="https://github.com/JayKayy">@JayKayy</a> made theirfirst contribution in <a href="https://github.com/containers/buildah/pull/6187">#6187</a></li>
  <li><a href="https://github.com/ricardobranco777">@ricardobranco777</a> made their first contribution in <a href="https://github.com/containers/buildah/pull/6226">#6226</a></li>
  <li><a href="https://github.com/actionmancan">@actionmancan</a> made their first contribution in <a href="https://github.com/containers/buildah/pull/6248">#6248</a></li>
  <li><a href="https://github.com/pstoeckle">@pstoeckle</a> made their first contribution in <a href="https://github.com/containers/buildah/pull/6252">#6252</a></li>
  <li><a href="https://github.com/2004joshua">@2004joshua</a> made their first contribution in <a href="https://github.com/containers/buildah/pull/6240">#6240</a></li>
</ul>

<h2 id="try-it-out">Try it Out.</h2>

<p>If you haven’t yet, <a href="https://github.com/containers/buildah/blob/master/install.md">install Buildah</a> from one of the Linux repos or GitHub and give it a spin. We’re betting you’ll find it’s an easy and quick way to build containers in your environment without a daemon being involved!</p>

<p>For those of you who contributed to this release, thank you very much for your contributions! If you haven’t joined our community yet, don’t wait any longer! Come join us on GitHub, where Open Source communities live.</p>

<h2 id="buildah--simplicity">Buildah == Simplicity</h2>
