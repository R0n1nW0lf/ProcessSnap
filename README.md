# ProcessSnap

**ProcessSnap** is a lightweight Windows process-behavior recorder for defensive security and malware-analysis labs.

> **ProcessSnap records and preserves process-lifecycle evidence. The analyst decides what the evidence means.**

ProcessSnap is designed to make short-lived and easy-to-miss process activity easier to review after a controlled test. It records process activity continuously between analyst-controlled checkpoints so processes that appear and disappear quickly are still preserved for later analysis.

## Lab Demonstration

[See the benign lab demonstration](docs/lab-demonstration/README.md): follow BEGIN → MID → FINAL, review a 79.77 ms process, and compare the evidence with Procmon and Wireshark.

## Current Status

**Public alpha release repository**

This repository is intended for reviewed public release material. Active development is maintained separately so unfinished experiments, internal notes, and development-only material are not mixed into the public release.

Current target platform:

- Windows 10 / 11 x64
- Portable use
- Controlled lab or sandbox environments
- Defensive security and malware-analysis workflows

## Current Capabilities

- BEGIN / MID / FINAL checkpoint workflow
- Continuous process-lifecycle recording
- Preservation of terminated and short-lived processes
- PID / PPID and available process metadata
- Process start and termination timestamps
- Readable process durations
- Parent / child process relationships where available
- Named and dated case folders with run numbers
- Optional baseline filtering without deleting recorded evidence
- Text report export

## Workflow

```text
Launch ProcessSnap
        ↓
Allow Windows / sandbox to settle
        ↓
BEGIN — baseline + start continuous recording
        ↓
Execute or test the sample
        ↓
Record process-lifecycle activity
        ↓
MID — analyst checkpoint
(recording continues)
        ↓
Observe delayed or additional activity
        ↓
FINAL — final checkpoint + stop recording
        ↓
Review captured lifecycle evidence
```

The continuous recorder matters because a process may exist for only milliseconds or seconds and terminate before an analyst reaches a later checkpoint.

## What ProcessSnap Helps Surface

ProcessSnap is intended to help analysts review evidence such as:

- Processes created after the baseline
- Processes that terminated during the observation window
- Short-lived process activity
- Parent / child relationships
- Start and termination timing
- Process duration
- Activity that occurred between checkpoints

A recorded process is **not automatically malicious**. ProcessSnap preserves evidence for investigation; it does not make a malware verdict.

## What ProcessSnap Is Not

ProcessSnap is not intended to replace:

- **Process Monitor (Procmon)** for detailed Windows process, Registry, filesystem, and related activity
- **Regshot** for Registry snapshot comparison
- An EDR, antivirus product, sandbox, or automatic malware-verdict engine

ProcessSnap is intended to help narrow the process evidence that deserves deeper investigation.

## Downloads

Public release files will be published here as they are prepared.

When a release includes a SHA-256 checksum, verify the downloaded file against the checksum published for that **exact release version** before execution.

Windows example:

```powershell
Get-FileHash .\ProcessSnap.exe -Algorithm SHA256
```

A matching hash verifies file integrity against the published reference. It does not by itself prove that a program is safe.

## Safe Testing

Use ProcessSnap only in an appropriate controlled Windows lab or sandbox when working with unknown or potentially malicious software.

Do not treat a recorded process, command, file, or behavior as malicious solely because ProcessSnap observed it. Correlate the surrounding evidence and verify before reaching a conclusion.

## Project Direction

The current focus is reliable **process-lifecycle evidence capture**:

1. Continuous process recording
2. Analyst-controlled checkpoints
3. Preservation of short-lived processes
4. Parent / child relationships
5. Timing and duration
6. Clear review and comparison output

Broader correlation features may be considered later, but the current public release remains focused on process behavior.

## Feedback

For bugs or feature suggestions, use GitHub Issues and include only sanitized information.

Helpful details include:

- ProcessSnap version
- Windows version
- Expected behavior
- Actual behavior
- Error message, if any
- Sanitized screenshot or log, if appropriate

**Do not upload live malware samples, credentials, private case data, or sensitive system information to a public issue.**

## License

A public license has not been selected yet. Licensing information will be added separately when the project is ready for public source distribution.

---

**ProcessSnap** — preserve the process evidence first, then investigate what it means.
