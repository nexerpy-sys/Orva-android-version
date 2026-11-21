# ORVA Android — Gemini project handoff

**Handoff date:** 21 November 2026  
**Purpose:** Continue engineering from the exact latest verified Android source checkpoint.  
**Incoming engineer:** Gemini in Google AI Studio.

## 1. Start here — authoritative source

Use this full source archive as the project baseline:

`ORVA_FRONTEND_CHECKPOINT_20261121T154905Z.zip`

- Source directory inside archive: `orva_frontend_work/`
- Git branch: `master`
- Exact HEAD: `059571a70b433b56d183c9aea99d704936a6f634`
- Commit: `Integrate approved A/B/C showcase typography`
- Git tree: `bac568cc25ab340104e1c705e2df50db9ee539ac`
- Working tree at checkpoint: clean
- Archive SHA-256: `60eb62a870c832793a6c9e201f24187c98641798411d80ea981d1cfc417a7d11`

This is the latest completed frontend topic checkpoint from 21 November 2026. It supersedes the earlier same-day archives and the earlier source states described in historical handover notes. Do not start from the 14:44/14:45 archives, an earlier commit, or a reconstructed copy of Kotlin source.

The ZIP contains the complete Android project source, tests, Gradle configuration/catalogue, resources, local `.git` history, design/continuity documents, font assets and licence notices. Preserve the complete project root. If the receiving environment requires an extracted project rather than a ZIP, extract `orva_frontend_work/` and open that directory as the project root; do not upload only `app/`.

## 2. What ORVA is

ORVA is the front-end showcase of Rindle Works, a studio building websites and custom apps. The Home and About Us experiences are meant to demonstrate crafted interface work, not a generic AI-generated dashboard or a template. The current Android target package is `com.rindleworks.orva`.

The archive is an Android source project, not a release APK. It must be built and validated in a real Android toolchain before anyone describes it as build-verified or release-ready.

## 3. Non-negotiable user decisions

### Agentic Build

- The existing Agentic Build is a defining feature and the user explicitly likes it. Improve it; never remove it or replace it with a generic loading animation, video, or cosmetic cursor effect.
- Preserve the existing 16-agent roster, shared frame clock/controller and scheduler architecture, dependency-aware construction, HUD, reduced-motion behaviour, haptics, pause/resume and manual-scroll/touch takeover.
- The Home regions are H1–H6; About Us regions are S01–S09. H2 includes the ORVA wordmark lantern sweep.
- Telemetry must describe actual controller/scheduler state. Do not invent fake progress, agent work or metrics.

### A/B/C identities are all approved together

They are dynamic regional design identities, not a user-facing theme picker. The initial experience starts in A; safe regions can be reverse-built and rebuilt through the existing morph sequence into B and C. Preserve content, stable region/task IDs, interaction state, navigation and the user's reading/scroll position. Pause morph work safely around active interaction and resume without discarding completed or partial work.

- **A — The Measured Press:** Archivo (display), Newsreader (reading), Space Mono (utility).
- **B — The Field Specimen:** Bricolage Grotesque (display), Source Serif 4 (reading), Martian Mono (utility).
- **C — The Museum Index:** Gloock (display), Schibsted Grotesk (reading), IBM Plex Mono (utility).
- Bengali uses Noto Sans Bengali. Bengali tracking/letter-spacing is zero.

The integrated source is authoritative for the approved palette, scale, layout grammar and motion. Do not re-propose fonts, recolour the system, introduce banned families, or convert A/B/C into a manual toggle. In particular, do not bring back Space Grotesk, Instrument Serif or Plus Jakarta Sans. Do not introduce Inter, Roboto, Open Sans, Lato, Montserrat, Poppins, DM Sans, Playfair Display, Arial, Helvetica or system-default font stacks.

### Scope boundaries

- Preserve the current Home H1–H6 and About S01–S09 content/structure as the basis for refinement; do not rewrite the product from scratch.
- Preserve business functionality and operational billing, inventory, tax, stock, returns and financial-domain rules. Do not alter domain logic or backend contracts as a side effect of front-end or font work.
- Do not add dependencies, runtime font downloads, remote font/CDN requirements or new files without a concrete need and an explanation.
- Keep the app's current ORVA branding, approved type and colours. Do not offer replacement brand directions.

## 4. What is already implemented in this checkpoint

- The A/B/C theme-aware typography resolver is integrated into Home, About, navigation and shared showcase components.
- The nine approved TTF files are bundled; six variable font resources use real supported axes on API 26+.
- Eight static font fallback instances are bundled for API 24–25. Static faces remain static; no fictional variable axes are fabricated.
- The existing IBM Plex Mono and Noto Sans Bengali resources are retained.
- Ten SIL Open Font License notices are included under `third_party/font_licenses/` and referenced in `THIRD_PARTY_NOTICES.md`.
- Old Space Grotesk, Instrument Serif and Plus Jakarta Sans resource mappings/files were removed from the active source.
- Theme-aware font roles are used through Home H1–H6 and About S01–S09. Bengali resolves to Noto Sans Bengali with zero tracking.
- Font axis values are applied at each region's active/terminal theme profile. **Per-frame optical/width-axis interpolation is not implemented and must not be claimed.** Existing Agentic reveal/morph behaviour is separate and remains in place.

Verified source font metadata includes:
- Archivo: `wght` 100–900; `wdth` 62–125.
- Newsreader: `wght` 200–800; `opsz` 6–72.
- Bricolage Grotesque: `opsz` 12–96; `wght` 200–800; `wdth` 75–100.
- Source Serif 4: `wght` 200–900; `opsz` 8–60.
- Martian Mono: `wght` 100–800; supplied `wdth` is fixed at 112.5; do not animate width.
- Schibsted Grotesk: `wght` 400–900.
- Space Mono and Gloock are static.

## 5. Verification — exact boundary

The following checks passed at this checkpoint:

- Pure Kotlin suite: **93 passed, 0 failed** (`tools/run_pure_kotlin_tests.sh`). This is a pure JVM suite; it does not prove Android or Compose compilation.
- Font acquisition helper: `py_compile` passed; `--check-only` reported 9 TTF files and 8 new-family OFL notices.
- FontTools audit parsed all 19 local `.ttf` resources, checked six variable-font axis tables, eight static fallbacks and ten OFL notices.
- Source audit: 126 Home/About/navigation/shared showcase Text calls explicitly specify a font family; no active source references to the three removed legacy font families were found.
- `git diff --check` passed; the checkpoint repository was clean.
- Full source archive passed ZIP integrity verification and was restored in a separate directory; its Git HEAD and tree matched the manifest.

**Not run / not verified:**

- Android Gradle build or Android resource linking.
- Compose compiler, Robolectric or Compose UI tests.
- APK/AAB build, emulator launch, physical-device installation or screenshots.
- English/Bengali glyph shaping and tracking on real Android devices.
- Runtime font behaviour on API 24–25 and API 26+ devices.
- Layout and performance checks at 360dp, 390dp, 412dp and tablet widths.

The previous environment had no Gradle executable, no `gradlew` script / wrapper JAR, no Android SDK and no resolved dependency cache. `gradle/wrapper/gradle-wrapper.properties` exists, but that alone is not an executable wrapper. A standalone `kotlinc` scan timed out and is inconclusive; do not report it as a successful compile.

## 6. Recommended first actions for Gemini

1. Import/restore the exact archive and verify Git HEAD `059571a70b433b56d183c9aea99d704936a6f634` before editing.
2. Read `BUILD_REPORT.md`, `ASSET_MANIFEST.md`, `THIRD_PARTY_NOTICES.md`, `RECOVERY_AND_CONTINUITY.md`, and the full original handover records under `docs/ORVA_HANDOVER_2026-11-21/`.
3. Read the active implementation in `OrvaShowcaseTokens.kt`, Home/About screen files and the Agentic controller/scheduler before changing anything. Treat source code and this handoff's current checkpoint status as newer than older status paragraphs in historical documents.
4. Establish a reproducible Android build environment. Inspect the existing Android Gradle Plugin/Kotlin/Compose versions in `gradle/libs.versions.toml` and the Gradle build files before choosing or adding a wrapper. Do not upgrade dependencies or rewrite the project merely to make the first build green.
5. Run the full Android build and applicable unit/Compose/Robolectric tests. Record exact commands, toolchain versions, failures and results. Fix compile/resource/runtime failures while preserving the accepted design and Agentic architecture.
6. Validate Home/About on emulator/device in English and Bengali at the mobile widths and tablet width listed above; include reduced motion, touch takeover, scroll stability, accessibility, font rendering, haptics and performance.
7. Only after those checks, update `BUILD_REPORT.md` and continuity notes with evidence, then create one complete topic-level source checkpoint with checksum. Do not create meaningless files or micro-checkpoints.

## 7. Important document caveats

- The project contains a substantial original user handover under `docs/ORVA_HANDOVER_2026-11-21/`, including verbatim design direction, preservation requests, Home/About decisions and theme-morph confirmation. Keep these records intact.
- Some older sections in `RECOVERY_AND_CONTINUITY.md`, `06_NEXT_CHAT_CONTINUITY.md`, `09_CHECKPOINT_STATUS.txt` and `11_THEME_MORPH_ENGINE_STATUS_AND_PENDING.md` describe earlier milestones (for example, font migration as pending). Those statements are historical and were superseded by the latest source commit and the 21 November 15:49 UTC checkpoint manifest/test log. Do not mistake them for the latest status; do not delete the historical record.
- `BUILD_REPORT.md` references `RINDLE_WORKS_ORVA_FRONTEND_MASTER_DIRECTIVE.md`, but that exact file is not present in this archive. The user's detailed design direction is preserved in `docs/ORVA_HANDOVER_2026-11-21/03_USER_ORVA_DESIGN_DIRECTION_VERBATIM.txt`, and the Home/About decisions are preserved in `07_ORVA_HOME_ABOUT_DECISIONS_2026-11-21_v2.txt`.
- The root `README.md` contains generic AI Studio export/bootstrap instructions. It mentions a `GEMINI_API_KEY`; do not assume the Android app needs a runtime Gemini API key. Inspect actual source usage and Gradle configuration before introducing secrets or `.env` handling.
- The archive includes local Git history but no configured GitHub remote. No GitHub repository was created as part of this handoff.

## 8. Supplementary files

The companion support archive contains the checkpoint manifest, full pure-Kotlin/font verification log, recovery patch and checksum metadata. These are evidence/recovery aids; the complete source ZIP remains the primary project.

**Do not treat this handoff as permission to redesign ORVA, remove Agentic Build, alter approved identity decisions, or claim unrun Android verification. Continue from the exact source and report what is actually built and tested.**
