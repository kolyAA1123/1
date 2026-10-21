# Video production preferences

- Use a pure black background (#000000) for new and revised videos.
- Deliver videos without AI narration or other audio by default. The user records
  the voice themselves. Never run speech synthesis unless explicitly requested.
- For every video, provide an original Russian narration text separately, with
  timestamps matching the visual sequences. Publish the text beside the video
  when updating the user's selected repository.
- Build each new video from the user's supplied files and instructions. Preserve
  mathematical/physical correctness and readable, uncluttered frames.
- Keep labels for forces, axes, states and formulas apart. Check actual rendered
  frames and text bounding boxes; moving labels must also remain readable.
- Use the existing checkout. Do not create a Git worktree unless requested.
- Published source is also kept in the corresponding *_sources.zip archive.
  In a fresh checkout, extract the needed archive if its project folder or setup
  files are absent; preserve any existing local edits.
- Follow available setup instructions. If setup_env.sh and render_all.py are
  present, source the environment from this folder and run the renderer there.
  Keep reusable source and instructions alongside the produced artifacts.
- The four-PDF film lives in pdf_lesson. Source setup_env.sh from this folder,
  then run `python render_pdf.py --jobs 3` inside pdf_lesson. Its plan.json and
  narration.json define 20 chapters and 1446 seconds. render_all.py produces
  the separate, older 11-minute film.
- The dynamics/statics/hydrostatics film lives in mechanics_lesson. After sourcing
  setup_env.sh, run `python render_mechanics.py --jobs 3` from that directory.
  Its plan.json defines 22 chapters and 1680 seconds. Do not add numerical
  examples or topics beyond the three supplied PDFs. verify_delivery.py checks
  the complete assembled film before package_sources.py prepares delivery files.
- The conservation/work/oscillations/waves film lives in energy_waves_lesson.
  Source setup_env.sh, then run `python render_energy_waves.py --jobs 3` there.
  Its plan.json defines 23 chapters and 1926 seconds. Use only the two supplied
  PDFs; all cycles and derivations must finish before transitions. The sound
  section must also remain completely silent. verify_delivery.py checks the
  assembled film, and package_sources.py prepares the three delivery files.
- The available isoprocesses/humidity sections live in mkt_isoprocesses_lesson.
  Source setup_env.sh, then run the renderer there with
  `python render_isoprocesses.py --preview --jobs 3 --no-assemble` first,
  and `python render_isoprocesses.py --jobs 3` for the final film.
  Its plan.json defines 13 chapters and 1176 seconds, based on the two available
  PDFs. The uploaded MKT PDF exceeded the 32 MiB transfer limit and is pending;
  do not claim it is covered or invent its contents. Preview rendering records
  text layout checks; verify_delivery.py requires complete, current reports
  without overlaps before package_sources.py prepares the delivery files.

- The user explicitly requested a voiced remake of the FIRST 11-minute kinematics
  film and selected the first calm female sample, Mari. This is an exception to
  the default silent workflow. The new project is kinematika_voice_lesson;
  preserve all older films. Run install_voice.sh there, then use the isolated
  ../.venv-speech/bin/python generate_voice.py. Source ../setup_env.sh and run
  render_lecture.py --preview --jobs 3 --no-assemble, then render_lecture.py
  --jobs 3, verify_delivery.py and package_sources.py. Its current measured plan
  has 12 chapters, 120 speech parts and 1758 seconds. Speech timing determines
  the visual plan; never time-compress speech to fit the old film. Do not claim
  the synthetic voice is a human recording. Keep voice weights, WAV files and
  cache directories out of Git and source archives.

- The user supplied a recording for the first kinematics film after asking to
  cut and synchronize their own narration. The provided-recording variant lives
  in kinematika_human_lesson and is separate from the Mari version. It has 120
  recorded parts and 1675 seconds (27:55). Do not synthesize or rewrite words.
  process_recording.py prepares a mono48k levelled WAV and16k guide; cuts.json
  preserves reviewed acoustic boundaries; prepare_human.py trims end pauses
  using the original guide, then derives the measured voice plan/frame map.
  retime_video.py changes only static speech holds and preserves every other
  source frame in order at60fps. Run assemble.py, verify_delivery.py, then
  package_sources.py. Keep original MP3, WAVs and ASR model weights out of Git.
  The five needs_listening notes in recording_review.json are uncertain ASR
  outputs, not verified listening. The user clarified that they read the
  supplied script correctly and that mistakes originated in our text. Review
  our source script before attributing any mistake to the narrator.

- The corrected THEORY-first dynamics/statics/hydrostatics narration lives in
  mechanics_theory_revision. Its authoritative output is narration_theory.json
  (22 chapters,110 passages). Run export_text.py there/from the repo to produce
  the TXT and DOCX and refresh the canonical dynamics narration filename.
  The previous mechanics_lesson narration is a visual-timing reference only;
  do not overwrite the revised text with its old generator. Times are scene
  anchors, not measured slots for the expanded theory. Preserve natural reading
  pace and adapt visuals after receiving a recording. Use definitions, physical
  meaning, conditions and complete explanations; proofread the script itself.


- The theory-first thermal equilibrium/thermodynamics/Carnot film lives in
  thermodynamics_lesson. It covers all 17 pages of the three supplied PDFs.
  Keep it silent on pure black; deliver separate TXT and DOCX for the user's
  voice. Source setup_env.sh, run prepare_lesson.py, then render_thermal.py
  --preview --jobs 3 --no-assemble and make_contacts.py. Inspect every beat's
  theory/action/result frames and require zero text collisions, then run
  render_thermal.py --jobs 3, verify_delivery.py and package_sources.py.
  Its reviewed plan has 14 chapters, 52 beats, 104 passages and 2626 seconds.
  The two narration windows surround a completed action; durations estimate
  natural reading at 125 wpm, not measured recorded speech. Adapt holds after
  a recording. Export Word with export_docx.py (python-docx; optional pinned
  requirements-export.txt). Preserve the source corrections in SOURCE_NOTES.md:
  correct c/C units and calorimeter temperature differences, no "isolated"
  system at Q!=0, constant-p work, ideal-gas model conditions, positive Qn/Qc
  magnitudes for engine efficiency and Kelvin/identical-reservoir/reversible
  conditions for Carnot. The ball must fully submerge before temperatures
  change; subsequent colour animation must keep its final position. The
  heating curve keeps all five segments and Carnot returns exactly to state 1.

- In user-facing download lists, omit the four kinematics variants (11:00,
  24:06, synthetic voice29:18, user's voice27:55) unless requested again.
  The user removed them from the list; preserve the actual files and archives.


- The source-based electrostatics/capacitors theory film lives in
  electrostatics_lesson: 20 PDF pages, 17 chapters, 57 beats, 114 narration passages,
  2855 seconds (47:35). Keep it silent on pure black and deliver TXT plus DOCX.
  Source setup_env.sh, run prepare_lesson.py, then render_electric.py --preview
  --jobs 3 --no-assemble, make_contacts.py, render_electric.py --jobs 3,
  verify_delivery.py and package_sources.py. Export Word with export_docx.py and requirements-export.txt.
  Read source corrections in SOURCE_NOTES.md. Distinguish Q from q0 and work
  of the field from minus the potential-energy change. Scope sphere formulas
  to a conducting sphere; preserve E's surface jump and phi's continuity.
  Keep the capacitor's one-plate charge distinct from total charge, fixed-q
  distinct from fixed-U, and neutral internal nodes in series. Never move
  charge through the ideal dielectric. In 14.3 the probe traverses the full gap.
  Vector lengths in compensation diagrams share one scale. Formula changes
  use sequential FadeOut/FadeIn, not glyph morphing. Sync reports are separate
  for preview/final so later previews cannot overwrite the final clock.
  Narration windows estimate 125 wpm, not a measured recording; adapt holds
  after receiving the user's voice. Preserve all previous films and files.
