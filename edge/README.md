# Consolonia edge (stop-gap)

This fork exists only to publish upstream Consolonia with fixes that are proposed but not yet
released. It is not a maintained fork. The fixes live on branches of
[JohnCampionJr/Consolonia](https://github.com/JohnCampionJr/Consolonia), each the head of an
upstream pull request, listed in [`branches.txt`](branches.txt). This `edge` branch is upstream
plus those branches merged, with any conflict between them resolved once; `main` stays a plain
mirror of upstream.

The [Edge workflow](../.github/workflows/edge.yml) runs on every push to `edge` and by hand. It
merges upstream `main` and each fix's latest tip, packs, and pushes to the private feed
`https://f.feedz.io/jcamp/packages/nuget/index.json`.

**Packages:** `Confetty.<package>` (`Confetty.Consolonia`, `Confetty.Consolonia.Core`, …), versioned
`<next upstream build>-edge.<run>`. Only the package id changes — assemblies, namespaces and types
are upstream's — so switching between official and edge is a change of `PackageReference` id and
nothing else.

**Retiring it:** drop each line from `branches.txt` once its fix ships upstream; when the list is
empty, switch consumers back to `Consolonia` and delete this fork.
