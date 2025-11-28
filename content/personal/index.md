---
title: Personal hub
summary: Academic-first landing page with a dedicated space for research notes, LaTeX-friendly writing, and a side-channel for music, art, and reading lists.
date: 2024-06-01
type: page
math: true
---

## Academic front porch

Welcome—this page keeps the academic side up front: recent research threads, problem notes, and a LaTeX-ready writing corner for future articles. Use the quick link below to hop to the interests section when you want a change of pace.

- **Research snapshots**
  - Discrete math + algorithms: exploring amortized analysis for self-adjusting data structures and batching heuristics for sequence alignment.
  - Machine learning + systems: reproducibility checklists for small-batch RL and lightweight profilers for CUDA kernels.
  - Collaborative work: mentoring underclassmen on proof techniques and writing-friendly pipelines.
- **Past project shelf**
  - Undergraduate research notebooks with **KaTeX**-rendered derivations—start a new note by creating a Markdown file under `content/` and setting `math: true` in the front matter, then write math as `$\nabla f(x)$` or
    $$
    \int_{0}^{1} x^{k}(1-x)^{n-k}\,dx = \frac{k!\,(n-k)!}{(n+1)!}
    $$
  - Mini write-ups that mimic ar5iv: draft in Markdown + LaTeX, commit, and let the static site render the math.

[Skip to interests ↓](#interests)

---

## Structured writing & upkeep

- **Templates**: copy any post in `content/blog/` to start a new article; keep `math: true` for LaTeX and add a `summary` to control previews.
- **Citation-friendly**: use fenced code blocks for BibTeX snippets and add a short “Context” paragraph per project so visitors see the scholarly framing first.
- **Maintenance**: update playlists or reading lists in this page’s Markdown—no extra configs required.

---

## Interest wing {#interests}

When you need to pivot away from proofs and code, here’s the creative side. Music auto-starts (respecting browser rules) and cycles through a short playlist.

<div class="audio-card">
  <div>
    <p><strong>Now playing:</strong> <span id="now-playing">Loading…</span></p>
    <audio id="interest-player" controls autoplay preload="metadata"></audio>
    <p class="audio-note">Autoplay may require a click on some browsers; once started, the playlist loops.</p>
  </div>
</div>

### Playlist
- "Passing Time" — Kevin MacLeod (Pixabay)
- "After the Rain" — Keys of Moon (Pixabay)
- "Nightfall" — Amaksi (Pixabay)

### Art & writing
- **Visual experiments**: shader sketches, collage, and photo studies; pair each drop with a one-line technical note (toolchain, resolution, or pipeline quirk).
- **Creative writing**: keep a running log of prompts, vignettes, or poems; tag them for mood so readers can filter later.
- **Reading / radical theory**: short reactions to current books or essays; include 2–3 pull-quotes and a “how it changes my practice” note.

<script>
  const playlist = [
    { title: 'Passing Time — Kevin MacLeod', src: 'https://cdn.pixabay.com/download/audio/2022/10/20/audio_36bb1f3a5d.mp3?filename=passing-time-121130.mp3' },
    { title: 'After the Rain — Keys of Moon', src: 'https://cdn.pixabay.com/download/audio/2021/09/01/audio_94be6c19c4.mp3?filename=after-the-rain-5756.mp3' },
    { title: 'Nightfall — Amaksi', src: 'https://cdn.pixabay.com/download/audio/2024/01/17/audio_bf7e366f70.mp3?filename=nightfall-178454.mp3' }
  ];

  const player = document.getElementById('interest-player');
  const label = document.getElementById('now-playing');
  let index = 0;

  function loadTrack(i) {
    const track = playlist[i % playlist.length];
    player.src = track.src;
    label.textContent = track.title;
  }

  player.addEventListener('ended', () => {
    index = (index + 1) % playlist.length;
    loadTrack(index);
    player.play().catch(() => {});
  });

  window.addEventListener('load', () => {
    loadTrack(index);
    player.play().catch(() => {});
  });
</script>

<style>
.audio-card {
  padding: 1.5rem;
  border: 1px solid var(--color-border, #d9d9d9);
  border-radius: 12px;
  background: linear-gradient(135deg, rgba(238, 246, 255, 0.9), rgba(246, 242, 255, 0.9));
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  margin-bottom: 1rem;
}
.audio-note {
  font-size: 0.9rem;
  color: #5a5a5a;
  margin-top: 0.4rem;
}
</style>
