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
