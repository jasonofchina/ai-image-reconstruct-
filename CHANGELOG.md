# Changelog
## [1.1.0] - 2026-08-14
### Removed
- Removed the 'Miniature Effect (Tilt-Shift)' feature module
- Deleted `examples/example_tiltshift.md`
- Removed all tilt-shift related logic, triggers, and adaptations
### Added
- New professional photography aesthetics: lighting reshaping, color grading, depth optimization, atmosphere enhancement
- New aspect ratio adjustment (3:4↔1:1, 16:9↔4:3, etc.)
- New camera angle adjustment (pitch/roll, sightline shift, camera pan)
- New mandatory confirmation mechanism for adjustments
- New pixel-level fidelity constraints
- New fidelity auto-downgrade and validation checkpoints
- New related test cases
### Changed
- Repository renamed to `ai-image-reconstruct`
- Skill name updated to 'AI Image Intelligent Reconstruction (Professional Photography Edition)'
- Simplified processing flow with a new adjustment confirmation stage
- Output summary now includes adjustment and fidelity status
### Fixed
- Fixed multi-mode instruction parsing issues
- Fixed style-induced text/logo distortion
- Fixed improper perspective after angle adjustments
## [1.0.0] - 2026-08-13
### Added
- Initial release
- Supported reconstruct and tilt-shift modes (tilt-shift removed in v1.1.0)
- Dual compliance checks
- Full test cases
