# T27 OS 0.3.0 - native People reference UX

Reviewable source distribution of the owner-authorized native People chat, video call, and Connection screens. Product logic is authored in `.t27`. This repository is independent of canonical upstream landing: it does not bypass its write gates or claim an upstream merge.

The six final source files are in `specs/t27os/`. `evidence/candidate13/manifest.json` pins their SHA-256 hashes and separate production/QA executable hashes. Upstream and inherited integrated implementation retain their original authorship and license; see `UPSTREAM-LICENSE`, `UPSTREAM-NOTICE`, and `reconstruction/PROVENANCE.json`. The scoped derivative was prepared for Dmitrii Fedorov (`dmitrii-f-t27`) using Codex.

## Reconstruct the complete build inputs

Use a clean clone of https://github.com/Trinity-S-AI-DNA/t27 at commit `1df5fbebf7a3d2f02d6a51e07854b78af902ae39`. Do not apply these patches to an occupied or dirty checkout.

```text
git apply --index /absolute/path/to/reconstruction/INTEGRATED-BASE.patch
git write-tree
# Must equal a00c379e0f5d57c3999c2dbd87cbea4d50221dea.
git apply --index /absolute/path/to/reconstruction/SOURCE-UX.patch
```

The first overlay preserves the previously integrated build inputs; it is not part of the six-path People change, and its protected-path eligibility is not implied. Its exact resulting tree was independently reconstructed from public upstream before this distribution. The second patch changes only the six supplied final People-related sources. Verify their hashes against the manifest before building. Keep inherited protected keys changes separate for owner review when proposing canonical landing.

On macOS with Xcode and a compatible native `t27b`, build through the existing recipe:

```text
DEVELOPER_DIR=/Applications/Xcode.app/Contents/Developer \
SDKROOT=/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX27.2.sdk \
make t27os T27OS_T27B=/absolute/path/to/t27b T27OS_BUILD=8580 T27OS_OUT=target/people-release
```

The measured compiler SHA-256 is `99ce538a63d2f551655863dcd42fef0eb83174e4f958aabd21b261f976a91777`. The output is a complete ordinary `T27OS.app`, version 0.3.0/build8580, with its resources and existing helpers. Development signing is machine-specific; no signing keys or credentials are distributed. The portable production artifact hash is in `evidence/candidate13/production-artifact.json`; QA uses a separate bundle identity and isolated homes.

## Verified scope and limits

Final source is candidate13, independently reviewed PASS. Candidate11 screenshots/evidence retain their original candidate identity in `evidence/candidate11/`; their geometry is unchanged. Candidate13 adds actual physical unseen-READ lifecycle and closed/open in-call chat checks, fresh symmetric READ and genuine duplex/reverse media with End. Do not relabel candidate11 screenshots as candidate13 captures. See `RULES.md` for reproduced defects and check-first requirements.

Two physical Macs on the same LAN: fresh three-message bidirectional READ; real duplex microphone and camera, remote rendering and own preview; mute/unmute, camera off/on while audio remains active; chat during a call; reverse-origin microphone call; End stops capture. Fresh saved Mesh endpoints under Auto preference also exchanged bidirectional READ. No WAN result is claimed.

Eight safe full-window screenshots show chat, authenticated Direct/Mesh Connection, and a clearly labeled synthetic source2 call on both Macs. Cameras and microphones were off during screenshots; real-camera verification used counters only. No identifiable camera images, raw peer cards or private transcripts are included.

Focused activation/READ-retry probe from11: 5 tests /90 runtime assertions. Final13 UI21/131 runtime plus2 compile-time; bridge8/42. Full direct chat_host module testing has inherited lowering blockers reproduced against the baseline and is not reported green. The initial missing READ cause was not established; reconnect activation/retry ordering was fixed and targeted tests cover the verified defect.

Ordinary shell selection, Queen panel and Keys navigation were exercised in isolated QA. Live Orca web/provider effects were suppressed by QA and are not claimed. iOS was not rebuilt or released. Existing histories use peer-only filenames: keep an ordinary profile bound to its stable Keychain identity and use a new isolated home for each ephemeral RAM identity. No history migration or at-rest encryption is claimed.

Canonical landing follows maintainer registry-first guidance in upstream #14166. Existing #14154 covers editors host classification; missing Mesh classification needs its own reviewed prerequisite. This source distribution does not change those policies.
