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

- In user-facing download lists, include the combined 24:06 kinematics,
  graphs, relative/rotational motion and ballistics film again: the user
  restored it on 2026-10-27 and intends to record their narration anew.
  Use kinematika_po_pdf_1080p60.mp4 and kinematika_po_pdf_ozvuchka.txt.
  Keep omitting the 11:00, synthetic voice29:18 and user's voice27:55 variants
  unless requested again. Preserve all actual files and archives.


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


- The direct-current theory film lives in direct_current_lesson: all 14 PDF pages,
  16 chapters, 50 beats, 100 narration parts, 2918 seconds (48:38). Keep pure black,
  silent 1080p60; deliver TXT and DOCX. Source ../setup_env.sh, run prepare_lesson.py,
  export_docx.py (system Python/python-docx), render_current.py --preview --jobs 3,
  make_contacts.py, render_current.py --jobs 3, verify_delivery.py, package_sources.py.
  Reading windows estimate 125 wpm; adapt static holds after the user's recording.
  Source conditions/corrections live in SOURCE_NOTES.md and materials/audit_*.md.
  Preserve electron/I/E directions, q charge versus Q heat, R external versus r internal.
  Ideal V is parallel/infinite R and ideal A series/zero R. Rheostat: left terminal to slider.
  Show T>Tc: R>0 before superconducting transition and T<Tc: R=0 after, for some materials.
  Keep r>0 at short circuit; finish derivations, both I(t) plots and the full energy loop.
  Na+ and Cl- have separate motion lanes; the steady ammeter does not reset. Hole handoff
  must fill the old vacancy and create a new one, with fixed atomic sites. Diode anode/cathode
  stay fixed when polarity changes; zero/infinite R are ideal only. Frame alignment may
  append 1–5 already pure black frames only when SPS/PPS match and all original packet
  hashes/timestamps are preserved; otherwise fall back to full black tail re-encoding.
  Require current layout/sync audits, visual review and full decode before publication.


- The magnetism/flux theory film lives in magnetism_lesson: all 22 PDF pages,
  19 chapters, 60 beats, 120 narration parts, 3517 seconds (58:37). Keep pure black,
  silent 1080p60, deliver TXT and DOCX. Source ../setup_env.sh, run prepare_lesson.py,
  export_docx.py with python-docx, render_magnetic.py --preview --jobs 3,
  make_contacts.py, render_magnetic.py --jobs 3, verify_delivery.py, package_sources.py.
  Reading windows estimate 125 wpm; adapt static holds to the user's recording.
  Read SOURCE_NOTES.md and materials/audit_*.md for source corrections. N=ROSE,
  S=CYAN; lines close N to S outside and S to N inside. Compass aligns with local
  resultant B; field vectors share a scale when used to infer the compass angle.
  Dot is +z toward the viewer, cross is -z away. Verify I cross B and q(v cross B).
  Magnetic Lorentz magnitude uses |q|. Ampere wire rotates rigidly at fixed length.
  Flux angle is between B and normal n; rotate constant-area frames by their angle,
  not endpoint blending. Induced B is along +/-n, not always +/-external B.
  State the view for clockwise currents. Arrows for induced current fade when the
  external flux stops changing in ordinary resistive loops. Faraday sign and
  absolute-value formulas are distinct. Psi=N Phi0 is linkage; Psi_self=L I.
  Do not count N twice. Signed self-EMF is -L Iprime and eps+eps_self=I Rsum.
  Current begins growing immediately after switching, without a finite dead time;
  winding resistance remains at steady current. Energy is L I squared / 2.
  Require current layout/sync audits, all rendered states reviewed, and full decode
  before publication; preserve all earlier films and files.


- The LC oscillations/transmission/transformer film lives in lc_oscillations_lesson:
  all 8 PDF pages, 9 chapters, 29 beats, 58 narration parts, 2389 words, 1641 seconds
  (27:21). Silent pure-black 1080p60; deliver TXT/DOCX. Source ../setup_env.sh,
  run prepare_lesson.py, export_docx.py (python-docx), render_lc.py --preview
  --jobs 3, make_contacts.py, render_lc.py --jobs 3, verify_delivery.py and
  package_sources.py. README gives the uv dependency/export ordering.
  Reading windows estimate 125 wpm; adapt static holds after the user's recording.
  See SOURCE_NOTES.md and materials/audit_*.md. q is the fixed initially positive
  LEFT plate charge; +I through the TOP coil points LEFT, so I=qprime and the
  first actual discharge points right with I<0. Full cycle must return to qmax,I0.
  Never move charge through dielectric; zero current has no actual arrow.
  q/qmax=cos(wt), I/Imax=-sin(wt); energies cos-squared/sin-squared stay >=0
  with period T/2, unlike charge/current T. U=-L Iprime is the signed balance
  with those conventions. Complete the derivation w=1/sqrt(LC),T=2pi sqrt(LC).
  Sum of energies equals each separate maximum, not the sum of maxima.
  Damping transfers field energy to heat; end of observation is not finite-time
  disappearance. Generator completes its turn at constant physical area.
  AC P=UI uses RMS values and an active load; line losses I-squared r compare
  at fixed P,r. U is the line-input terminal voltage, not unconditional source EMF.
  Transformer windings are electrically separate and share one varying per-turn
  flux. Use signed Faraday or correct magnitudes; count N once. Ideal U2/U1=N2/N1,
  same frequency. Require current layout/sync audits, visual review, full decode
  and verified download links before publication. Preserve earlier films/files.


- The optics/lenses theory film lives in optics_lesson: all 26 pages of two PDFs,
  17 chapters, 57 beats, 114 narration parts, 4627 words, 3188 seconds (53:08).
  Keep silent pure-black 1080p60; deliver TXT and DOCX. Source ../setup_env.sh,
  run prepare_lesson.py, export_docx.py (python-docx), render_optics.py --preview
  --jobs 3, make_contacts.py, render_optics.py --jobs 3, verify_delivery.py and
  package_sources.py. README gives uv dependency/export order. Reading windows
  estimate 125 wpm; adapt holds after the user's recording. Preserve older films.
  Source conditions/corrections: SOURCE_NOTES.md and materials/audit_*.md.
  All angles are measured from normals. TIR requires n1>n2 and alpha>critical;
  equality is grazing refraction. Plate outer media match; displacement is normal
  to parallel rays. Use glass index, not the source typo water. Normal dispersion:
  violet nearer normal than red. Geometric/paraxial thin lens model, same ambient
  medium on both sides; power D=1/F with F in metres. All real rays are solid with
  arrows along energy; backward extensions dashed. Reverse every actual arrow.
  optical_math.py and optical_geometry.py provide exact signed intersections and
  label placement; include BOTH in render/audit freshness dependencies. Real object
  d>0, real image f>0, virtual f<0; converging F>0/diverging F<0. H,h are positive
  sizes; Gamma=H/h=abs(f)/d and orientation is separate. A is the base, B the tip.
  At d=F outgoing rays are parallel; no finite image. Do not animate d across the
  pole. Verify all five converging and two diverging cases. Correct h/f to h/F
  in source similarity derivation. The pupil is an aperture, not the lens; cornea
  and crystalline lens refract. Eye correction rays end at the retina; any
  behind-retina geometry is dashed only. Do not add accommodation theory absent
  from the PDF. Require all rendered states reviewed, current layout/sync reports,
  full decode and verified download links before publication.


- The wave-optics theory film lives in wave_optics_lesson: all 9 PDF pages,
  9 chapters, 29 beats, 58 narration parts, 2302 words, 1598 seconds (26:38).
  Keep silent pure-black 1080p60; deliver TXT/DOCX. Source ../setup_env.sh,
  run prepare_lesson.py, export_docx.py (python-docx), render_wave.py --preview
  --jobs 3, make_contacts.py, render_wave.py --jobs 3, verify_delivery.py and
  package_sources.py. README gives dependency/export order. Reading windows
  estimate 125 wpm; adapt holds after the user's recording. Preserve old films.
  Source conditions: SOURCE_NOTES.md and materials/audit_wave_*.md. Natural
  light is not one coherently rotating E vector; polarization is transverse.
  Simple path extrema assume initially in-phase sources and a common medium;
  zero cancellation requires equal amplitudes. DeltaL=L2-L1 with S1 above S2;
  phase_pair uses a propagation lag, not an advance. Far-field DeltaL is
  approximately d sin(phi); far field alone does not imply a small angle.
  A grating period contains transparent and opaque parts; L spans N complete
  cells. Odd half-wavelength is not a universal multislit minimum. Finite
  forward-screen orders require abs(k)*lambda<d, strictly; kmax=ceil(d/lambda)-1.
  x approximately k*lambda*ell/d requires small angles. In the film section d
  becomes thickness. Use one reflection phase inversion for n_air<n_film>n_water;
  the half-wave term is phase, not energy loss. DeltaLeff approximately
  2*n*d+lambda0/2 requires nearly normal incidence. The given first reflected
  maximum is 760/(4*1.6)=118.75 nm approximately 119 nm, without claiming that
  all other colours disappear. Include wave_math.py in render/audit freshness.
  Require every rendered state reviewed, current layout/sync reports, complete
  actions, full decode and verified download links before publication.


- The quantum/photoeffect/relativity/nuclear film lives in quantum_nuclear_lesson:
  all 27 pages of two PDFs, 17 chapters, 54 beats, 108 narration parts,
  4199 words, 2933 seconds (48:53). Keep silent pure-black 1080p60;
  deliver TXT/DOCX. Source ../setup_env.sh, run prepare_lesson.py,
  export_docx.py (python-docx), render_quantum.py --preview --jobs 3,
  make_contacts.py, render_quantum.py --jobs 3, verify_delivery.py and
  package_sources.py. Reading windows estimate 125 wpm; adapt holds after
  the user's recording. Preserve older films. SOURCE_NOTES.md and materials
  contain source corrections and independent physics/visual reviews.
  Large apertures do not prove particle behaviour; which-path measurement
  is physical interaction, not consciousness. Do not attribute that setup to
  de Broglie. Photon E=h*nu=hc/lambda and p=h/lambda use vacuum lambda/c;
  reflected photon delta-p=-2p, plate receives +2p for normal ideal reflection.
  Bohr levels are historical states, not continuous spatial paths; hydrogen
  En=-13.6/n^2 eV, zero is ionization, all six depicted transitions are alternatives.
  H2 is molecular, deuterium is an isotope. Spectra are qualitative, uncalibrated.
  Photoelectron initial speeds/directions vary; Kmax is an upper bound. Use
  U=Vanode-Vcathode, e>0 and positive Ustop with cutoff at signed U=-Ustop.
  Work function is escape from the material surface, not isolated-atom ionization.
  Kmax=me*vmax^2/2 requires nonrelativistic electrons; threshold Kmax=0 is
  not a guaranteed finite collected current. Intensity J differs from current I.
  Light-clock triangle uses c^2-v^2; one-way t1 is not proper time between
  distinct floor/ceiling points. E0=mc^2 uses vacuum c. Correct source's
  massless-muon error to rest-frame pi0->two opposite photons; do not add
  relativistic mass or length-contraction chapters absent from the PDF.
  Rutherford deflection is electrostatic; classical collapse is not annihilation.
  A/Z count nucleons/protons, electrons=Z only for neutral atoms. Lorentz:
  v right/B into screen gives alpha up, beta-minus down, gamma straight.
  Mass defect compares the whole bound nucleus to free nucleons, not changing
  each nucleon's invariant mass. Decay m(t) is remaining parent-isotope mass;
  activity falls while cumulative decays rise. U235+n fission is induced,
  not spontaneous decay. Fission paths are schematic with opposite fragment
  recoil; neutron losses prevent guaranteed tripling. Control rods absorb;
  graphite moderates. Include quantum_math.py in render/audit freshness.
  Require current layout/sync reports, every rendered state reviewed, complete
  actions, full decode and verified download links before publication.


- The NEW recording `1.mp3` for the combined four-PDF24:06 kinematics film
  lives in kinematika_pdf_human_lesson (distinct from old120cue firstfilm).
  Its measured voiced edit has20chapters,100cues,1872seconds31:12.
  Keep originalsilent24:06 and oldvoicevariants intact. No TTS; no voice speed
  or pitch change. build_edit.py derives exactPCMtracks and frame_map from
  cuts.json plus reviewed narration_anchors.json. retime_video.py changes only
  decoded-static sourceholds and initial singleframe pauses plus apexWait.
  All other sourceframes stay in native60fps order. Run assemble.py,
  verify_delivery.py (fullAVdecode, exactPCM, sourceholdpixelchecks), then
  package_delivery.py. ASR is not verified listening or narrator-error evidence.
  Tight01_05→02_01join82.83s is documented in output/alignment_review.json;
  preserve quiet edge handles. The second uploaded compressed mechanics MP3
  exceeded32MiB transfer limit and has NOT been processed; await smaller upload.
