# Video production preferences

- Use a pure black background (#000000) for new and revised videos.
- Deliver videos without AI narration or other audio by default. The user records
  the voice themselves. Never run speech synthesis unless explicitly requested.
- For every video, provide an original Russian narration text separately, with
  timestamps matching the visual sequences. Publish the text beside the video
  when updating the user's selected repository.
- Build each new video from the user's supplied files and instructions. Preserve
  mathematical/physical correctness and readable, uncluttered frames.
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
