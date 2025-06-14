# AGENT Instructions for ArduPilot

## Project structure
- Vehicle firmware lives under `ArduCopter/`, `ArduPlane/`, `ArduSub/`, `Rover/` and `AntennaTracker/`.
- Shared code resides in `libraries/`.
- Utility scripts are under `Tools/`.
- External dependencies are kept in `modules/` and should not be modified directly.

## Building
- Run all build commands from the repository root using `./waf`.
- Configure for SITL with `./waf configure --board=sitl`.
- Build a vehicle with `./waf <vehicle>` (for example `./waf copter`).
- List available boards with `./waf list_boards`.
- Install prerequisites with `Tools/environment_install/install-prereqs-<OS>.sh`
  (for example `install-prereqs-ubuntu.sh -y`) to ensure dependencies such as
  `python3-pexpect` are present.
- Clean with `./waf clean` only when necessary.

## Testing
- Ensure submodules are up to date: `git submodule update --init --recursive`.
- Run `./waf check` to build and execute the relevant tests.
- Run `./waf check --alltests` to execute the entire test suite.

## Code Style
- Format C/C++ with AStyle via `Tools/scripts/run_astyle.py`.
  - Rules are defined in `Tools/CodeStyle/astylerc`.
- Python code uses Black (line length 120) and is checked with Flake8.
  - Install the hooks using `pre-commit install` and run `pre-commit run --all-files` before committing.
- Imports are sorted with isort using the Black profile.

## Documentation
- Doxygen and graphviz are required.
- Run `docs/build-libs.sh` once and then `docs/build-<project>.sh` (e.g. `docs/build-arducopter.sh`) to generate HTML docs in `docs/`.

## Pull Request Guidelines
- Title format: `[Fix|Feat] Short summary`.
- PR description must include:
  - **What changed**
  - **Testing done**
  - **Related issue(s)**
