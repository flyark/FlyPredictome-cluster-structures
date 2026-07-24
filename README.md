# FlyPredictome cluster structures

Single-best-model AlphaFold3 bundles for FlyPredictome-network sub(sub)-cluster higher-order complexes,
served for GitHub Pages and consumed by the network viewer.

- **152 complexes** (`<job>.zip`), 3-9-mer, drawn from every AF3 campaign (v18/v20/v21/v22/v25/v26/c*/s_c/d_ …),
  one best complex per network leaf plus curated variants (e.g. CCT with/without Misato).
- **Quality control**: every bundle passed a steric-clash gate — max inter-chain heavy-atom clash < 15% of a
  chain's residues, so paralog same-site double-occupancy assemblies are excluded. 101 CONFIRMED + 49 PARTIAL
  AF3 assembly verdicts + 2 curated (CCT).
- Each `<job>.zip` = highest-iLIS AF3 model (`_model_N.cif`) + PAE (`_full_data_N.json`, `contact_probs` dropped)
  + summary + job_request. PAE retained so LIVIA recomputes iLIS/cLIR in-browser.
- `cluster_available.json` = manifest: `{ job, url, members, n, verdict, best_model, has_PAE, iLIS, lcc }`.
  The viewer matches each bundle to its sub(sub)-cluster **by gene set** at runtime (job numbers predate the
  live clustering). The `url` field points at the hosting repo, so bundles can be split across repo 1/2 if the
  set outgrows the ~1 GB Pages limit.

Served with CORS `*` → LIVIA (`universal.html?data=<url>&name=`) fetches bundles directly, no proxy.
