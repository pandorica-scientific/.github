<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/pandorica-scientific/.github/main/profile/assets/lockup-dark.png">
  <img alt="Pandorica Scientific" src="https://raw.githubusercontent.com/pandorica-scientific/.github/main/profile/assets/lockup-light.png" width="460">
</picture>

<h3>Software for problems where the data has to be trusted.</h3>

<p>
  <a href="#active-projects"><b>Projects</b></a> &nbsp;·&nbsp;
  <a href="#upstream-scientific-work"><b>Upstream work</b></a> &nbsp;·&nbsp;
  <a href="#licensing"><b>Licensing</b></a> &nbsp;·&nbsp;
  <a href="#contact"><b>Contact</b></a>
</p>

</div>

<br>

## What this organization is

Pandorica Scientific is the home for the open-source work of
[Robert Kiewisz](https://github.com/RRobert92) — tools for electron
microscopy, and the software that grew out of the same habit of mind.

The projects here look unrelated at first glance: a serial-section tomogram
stitcher, a self-hosted household finance platform, a passive sensor logger.
The method behind them is the same one.

- **Read the raw signal, not a vendor's summary of it.** Microscope volumes,
  the bank's own statement files, the wristband's own radio broadcast.
- **Verify the result against something independent.** A geometric invariant,
  the statement's own closing balance, a reading from the official app.
- **Keep the data on hardware you control.** No cloud account is required to
  run any of it.
- **Say plainly what a tool cannot do.** Limitations belong in the README,
  not in the issue tracker after someone is bitten.

<br>

## Active projects

### 🔬 [pandorica](https://github.com/pandorica-scientific/pandorica) — analytical tools for electron microscopy

Stitches serial-section electron tomograms into one continuous volume,
automatically. Image data fixes each section's global pose — rotation, shift,
anisotropic stretch — and microtubule splines drive only the fine residual
warp, guarded so the deformation stays an orientation-preserving
diffeomorphism and cannot fold the volume back on itself. A global pose solve
replaces pairwise accumulation, so alignment error does not drift down the
stack. Ships with a [napari](https://napari.org) plugin for validating results
on real datasets and recording coarse-alignment ground truth by hand.

```bash
pip install pandorica
python -m pandorica.stitch.cli <input_dir>
```

`Python` · `PolyForm Noncommercial 1.0.0` · integrates with `tardis_em`

---

### 🏠 [continuum](https://github.com/pandorica-scientific/continuum) — your household's whole financial picture, on hardware you own

Most personal-finance software starts by asking which bank you use. Continuum
never does. It reads the export files your bank already gives you, works out
their structure from the files themselves, and checks what it extracted
against the statement's own balances before trusting a single row. From there
it connects the money to what belongs around it — the property, the mortgage
secured against it, the tenants, the portfolio, the payslips, the tax those
generate — for the household as a whole rather than one person at a time.
It never connects to your bank, and it runs on a machine you control.

```bash
docker compose up
```

`TypeScript` · `SvelteKit` · `Docker (amd64 · arm64)` · `PolyForm Noncommercial 1.0.0`

---

### 📟 [ble-vitals-monitor](https://github.com/pandorica-scientific/ble-vitals-monitor) — passive vitals monitor and logger

An unofficial, strictly receive-only monitor for a baby-vitals wristband. It
listens to the Bluetooth Low Energy advertisements the wristband already
broadcasts in the clear, decodes heart rate, blood-oxygen saturation and skin
temperature, and logs every reading to a microSD card as timestamped CSV — all
without ever connecting to, pairing with, or transmitting to the wristband or
its base station, so the official system keeps working untouched. Runs on an
inexpensive ESP32 "Cheap Yellow Display"; small Swift command-line tools cover
the same job on a Mac.

> **Not a medical device and not a safety monitor.** A hobby and educational
> project. Independent, and not affiliated with or endorsed by the
> manufacturer.

`C++` · `ESP32` · `Swift` · `PolyForm Noncommercial 1.0.0`

<br>

## Upstream scientific work

**TARDIS** — Transformer And Rapid Dimensionless Instance Segmentation — and
its companion packages were developed at the
[Simons Machine Learning Center](https://github.com/SMLC-NYSBC) at the New
York Structural Biology Center, and belong to that group. The copies in this
organization are forks kept for continued maintenance and contribution
upstream; they are not Pandorica Scientific projects, and the canonical
repositories remain under [SMLC-NYSBC](https://github.com/SMLC-NYSBC).

| Fork | Upstream | Purpose |
| --- | --- | --- |
| [TARDIS](https://github.com/pandorica-scientific/TARDIS) | [SMLC-NYSBC/TARDIS](https://github.com/SMLC-NYSBC/TARDIS) | Instance segmentation of microtubules, membranes and filaments in electron microscopy data · [docs](https://smlc-nysbc.github.io/TARDIS/) |
| [napari-tardis_em](https://github.com/pandorica-scientific/napari-tardis_em) | [SMLC-NYSBC/napari-tardis_em](https://github.com/SMLC-NYSBC/napari-tardis_em) | napari plugin front-end for TARDIS |
| [tardis_em_analysis](https://github.com/pandorica-scientific/tardis_em_analysis) | [SMLC-NYSBC/tardis_em_analysis](https://github.com/SMLC-NYSBC/tardis_em_analysis) | Shared analysis libraries used by both |

`pandorica` extends this line of work into serial-section reconstruction. When
`tardis_em` is installed alongside it, the stitcher is also exposed as the
`tardis_stitch` console script.

<br>

<details>
<summary><b>Archive</b> — earlier microscopy scripts, kept for reference</summary>

<br>

Small, unmaintained helper scripts from earlier electron-tomography work. They
still do what they say, but they are not developed further.

- [Assit_Automatic_Tomogram_Flattening_IMOD](https://github.com/pandorica-scientific/Assit_Automatic_Tomogram_Flattening_IMOD) — console interface for the IMOD automatic tomogram-flattening tool (2023, GPL-3.0)
- [etomo_Batch_SetUp](https://github.com/pandorica-scientific/etomo_Batch_SetUp) — eTomo batch settings for automatic reconstruction of roughly 300 nm plastic serial sections (2021, MIT)

</details>

<br>

## Licensing

The three active projects are released under the
[PolyForm Noncommercial License 1.0.0](https://polyformproject.org/licenses/noncommercial/1.0.0).
They are free to use for research, study, and teaching — by educational,
public-research, charitable, public-health, environmental and government
institutions, whatever their funding source. Commercial use needs a separate
licence; each repository explains how to ask for one.

The TARDIS forks stay under their upstream MIT licence. Archived scripts carry
the licence stated in their own repository.

Contributions are welcome and require a Developer Certificate of Origin
sign-off — see the `CONTRIBUTING.md` in each repository.

<br>

## Contact

Robert Kiewisz — [robert.kiewisz@gmail.com](mailto:robert.kiewisz@gmail.com) ·
Poland

<div align="center"><sub>Questions about a specific project belong in that project's issue tracker.</sub></div>
