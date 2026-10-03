# Branch protection

The forge is authoritative for jankurai-standard. GitHub is a publishing mirror
only: it receives `main` and release tags from the forge, runs no CI, and is not
a merge path. CI runs on the forge and our own hosts, and releases are built and
signed on our servers.

`main` moves only through reviewed forge pull requests. Merge after reviewing the
complete final diff and the actual forge CI results for its exact head, then
qualify resulting main before selecting it downstream. Force pushes and branch
deletion on `main` are not used.

This is a process record, not a substitute for review or a claim of independent
approval. The wider program's independent deployment approval remains a
separate acceptance requirement.

Release tags are immutable: verify the selected commit and evidence before
creating a release tag, then retain the tag and assets unchanged. See
[release process](release.md).

Changes to the accepted baseline and its provenance require the same complete
diff review and checks as other source changes. A badge documents its linked
audited revision; it is not a claim that every later commit has passed.
