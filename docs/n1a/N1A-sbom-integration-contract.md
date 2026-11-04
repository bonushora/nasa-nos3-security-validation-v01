# N1-A — SBOM Integration Contract

## Objective

Define future association of NOS3, cFS, and F´ SBOMs without reading, importing, or modifying independent workspaces. This is a proposed contract; N1-A observed no external SBOM.

## Mandatory principles

1. Each external SBOM is independently immutable and identified by authorized location, byte length, media type, and exact-byte SHA-256.
2. Declare format/version: SPDX JSON (preferably compatible 2.3+) or CycloneDX JSON (compatible 1.5+).
3. Subject identity includes repository, full commit, informational branch, and tree OID where available.
4. SBOM subject commits must match the NOS3 gitlink manifest; mismatches fail closed.
5. Generation/conversion/merge/validation records exact tool version, executable/image digest, and parameters.
6. SBOM does not replace build provenance, artifact hashes, or configuration.
7. Signatures/attestations supplement but do not replace preserved-byte hashes.

## Minimum external envelope

```json
{
  "artifact_id": "external-sbom:<framework>:<sha256>",
  "framework": "cFS|Fprime",
  "source_repository": "https://...",
  "source_commit": "<40-hex>",
  "source_tree": "<40-hex-or-UNAVAILABLE>",
  "format": "SPDX|CycloneDX",
  "spec_version": "<version>",
  "media_type": "application/json",
  "byte_length": 0,
  "sha256": "<64-hex>",
  "generator": [{"name": "<tool>", "version": "<exact>", "digest": "<sha256>"}],
  "signature_or_attestation": "<reference-or-NOT_APPLICABLE-with-justification>",
  "captured_at": "<RFC3339>",
  "authority": "<mission/approval reference>"
}
```

The zero byte length is a schema placeholder, never valid evidence.

## cFS and F´ binding

cFS is distributed across cFE, OSAL, PSP, tools, and apps. Its external manifest must enumerate covered commits, compare each with the corresponding NOS3 gitlink, expose omissions/additions, preserve SPDX/CycloneDX dependency relations, and resolve identity by repository+commit+hash rather than labels.

The `fsw/fprime/fprime-nos3` gitlink identifies an integration/deployment, not automatically the F´ framework version. An F´ SBOM must bind deployment and framework commits, resolution mechanism, incorporated NOS3 components, and baseline gitlinks. Otherwise it remains `PARTIAL`.

## Future aggregate and gates

The aggregate references immutable NOS3/cFS/F´ SBOMs, the 47-entry manifest, tool/config/image/binary provenance, a source-to-package-to-artifact table, experiment identity, and witness events without rewriting external artifacts.

S1–S8 require authorized bytes/hash, valid supported JSON, matching subject identity, recorded tools/parameters, validated relations, explicit cFS/F´ deltas, immutable references, and a verifiable provenance/experiment/witness link. Any failure keeps `SBOM_INTEGRATION=NOT_READY`.
