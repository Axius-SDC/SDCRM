# Versioning Strategy

This document describes the versioning strategy for SDCRM and the SDC4 ecosystem.

## Table of Contents

- [Semantic Versioning for Reference Models](#semantic-versioning-for-reference-models)
- [Version Number Format](#version-number-format)
- [What Changes Which Version](#what-changes-which-version)
- [Ecosystem Version Alignment](#ecosystem-version-alignment)
- [Release Process](#release-process)
- [Version Migration](#version-migration)

---

## Semantic Versioning for Reference Models

SDCRM follows [Semantic Versioning 2.0.0](https://semver.org/), adapted for reference model specifications.

**Key Principle**: The **MAJOR version** represents the **SDC generation**, not just breaking changes.

```
MAJOR.MINOR.PATCH
  │     │     └── Non-breaking fixes and clarifications
  │     └────────── Backward-compatible additions
  └──────────────────── SDC generation (breaking changes → new SDC)
```

### Current Version

**SDC4**: `4.0.0` (October 20, 2025)

---

## Version Number Format

### MAJOR Version (SDC Generation)

**Format**: `X.0.0` (e.g., `4.0.0` → `5.0.0`)

**Triggers**:
- Breaking changes to reference model structure
- Removed or renamed core types
- Changed required attributes
- Incompatible structural modifications
- **Creates a new SDC generation** (SDC4 → SDC5)

**Examples**:
```
4.0.0 → 5.0.0: Removed XdAnyType, restructured inheritance
4.0.0 → 5.0.0: Changed namespace URI
4.0.0 → 5.0.0: Made previously optional attributes required
```

**Impact**:
- Existing data models may not validate
- Tools need updates (SDCStudio, validators)
- Migration guide required
- Major announcement needed

**Process**:
1. RFC with detailed proposal
2. Community discussion (minimum 1 month)
3. Implementation plan
4. Beta testing period
5. Migration tools created
6. Official release

**Note**: New MAJOR versions are **rare** (years between releases). SDC4 should remain stable for extended period.

---

### MINOR Version (Backward-Compatible Additions)

**Format**: `X.Y.0` (e.g., `4.0.0` → `4.1.0`)

**Triggers**:
- New optional types added
- New optional attributes
- Enhanced annotations and metadata
- Additional convenience types
- New examples and guides
- **Still SDC4** - no breaking changes

**Examples**:
```
4.0.0 → 4.1.0: Added XdRatioType (new optional type)
4.0.0 → 4.1.0: Added 'confidence' attribute to XdQuantity (optional)
4.0.0 → 4.1.0: Enhanced OWL ontology with additional relationships
```

**Impact**:
- Existing models continue to validate
- New features available but not required
- Tools can optionally support new features
- Documentation updated
- Announcement in changelog

**Process**:
1. Proposal via GitHub issue
2. Community feedback (1-2 weeks)
3. Implementation with tests
4. Documentation update
5. Release with changelog

**Timeline**: Several MINOR releases per year possible.

---

### PATCH Version (Non-Breaking Fixes)

**Format**: `X.Y.Z` (e.g., `4.0.0` → `4.0.1`)

**Triggers**:
- Documentation clarifications
- Schema comment improvements
- Bug fixes that don't change structure
- Typo corrections
- Example fixes
- **Still SDC4** - no functional changes

**Examples**:
```
4.0.0 → 4.0.1: Fixed typo in schema annotation
4.0.0 → 4.0.1: Clarified conformance requirement in spec
4.0.0 → 4.0.1: Updated example to better demonstrate pattern
```

**Impact**:
- No functional changes
- Documentation improved
- No tool updates needed
- Existing models unaffected

**Process**:
1. Fix identified
2. Quick PR review
3. Merge and release
4. Update changelog

**Timeline**: PATCH releases as needed (monthly if active development).

---

## What Changes Which Version

| Change Type | Version Impact | Examples |
|-------------|----------------|----------|
| Remove type | MAJOR | Delete `XdStringType` |
| Remove attribute | MAJOR | Delete `label` attribute |
| Make attribute required | MAJOR | Change optional to required |
| Change element structure | MAJOR | Modify hierarchy |
| Change namespace URI | MAJOR | New namespace |
| Rename type | MAJOR | `XdString` → `XdText` |
| Add new optional type | MINOR | Add `XdRatioType` |
| Add new optional attribute | MINOR | Add `confidence` |
| Enhance ontology | MINOR | More OWL relationships |
| Add examples | MINOR | New use cases |
| Fix documentation | PATCH | Clarify ambiguity |
| Fix schema comment | PATCH | Improve annotation |
| Fix typo | PATCH | Spelling correction |

---

## Ecosystem Version Alignment

### Shared MAJOR Version

All projects in the SDC ecosystem share the **same MAJOR version**:

| Project | Current Version | Purpose |
|---------|-----------------|---------|
| **SDCRM** | 4.0.0 | Reference model and schemas |
| **SDCStudio** | 4.0.0 | Web application for model generation |
| **Obsidian Template** | 4.0.0 | Markdown template for dataset descriptions |

**Why?**
- Clear compatibility signaling
- Users know what works together
- Ecosystem-wide coordination
- Simplified documentation

### Independent MINOR/PATCH Versions

Each project manages its own MINOR and PATCH versions independently:

**Example Timeline**:
```
2025-10-20: SDC4 ecosystem launches
- SDCRM: 4.0.0
- SDCStudio: 4.0.0
- Obsidian Template: 4.0.0

2025-11-15: SDCStudio adds new UI features
- SDCRM: 4.0.0 (unchanged)
- SDCStudio: 4.1.0 (new features)
- Obsidian Template: 4.0.0 (unchanged)

2025-12-01: SDCRM adds new optional types
- SDCRM: 4.1.0 (new types)
- SDCStudio: 4.1.0 (unchanged, still compatible)
- Obsidian Template: 4.0.0 (unchanged)

2026-01-15: All projects update for new SDCRM types
- SDCRM: 4.1.0 (unchanged)
- SDCStudio: 4.2.0 (supports new types)
- Obsidian Template: 4.1.0 (includes new types)
```

### Compatibility Matrix

| SDCRM | SDCStudio | Obsidian Template | Compatible? |
|-------|-----------|-------------------|-------------|
| 4.0.x | 4.0.x+ | 4.0.x+ | ✅ Yes |
| 4.1.x | 4.0.x+ | 4.0.x+ | ✅ Yes (new types optional) |
| 4.1.x | 4.2.x | 4.1.x | ✅ Yes (full feature support) |
| 5.0.x | 4.x.x | 4.x.x | ❌ No (breaking changes) |

---

## Release Process

### For MAJOR Releases (SDC5, SDC6, etc.)

1. **RFC Phase** (1-3 months)
   - Detailed proposal published
   - Community discussion and feedback
   - Consensus building

2. **Alpha Phase** (1-2 months)
   - Early implementation
   - Internal testing
   - Breaking changes allowed

3. **Beta Phase** (1-2 months)
   - Feature complete
   - Public testing
   - Bug fixes only (no new features)
   - Migration tools developed

4. **Release Candidate** (1 month)
   - Production-ready candidate
   - Final testing and validation
   - Documentation complete

5. **Release**
   - Official announcement
   - Migration guide published
   - Tools updated
   - Training materials available

### For MINOR Releases

1. **Proposal** - GitHub issue with description
2. **Discussion** - 1-2 week feedback period
3. **Implementation** - Schema changes + documentation
4. **Review** - Maintainer approval
5. **Release** - Changelog update, Git tag, announcement

### For PATCH Releases

1. **Fix identified** - Bug or documentation issue
2. **Quick PR** - Immediate fix proposed
3. **Review** - Fast-track approval
4. **Release** - Git tag, changelog update

---

## Version Migration

### From SDC4 to SDC4.1 (MINOR)

**No migration needed** - Backward compatible

Actions:
- Read changelog for new features
- Optionally use new types/attributes
- Update documentation if desired
- Existing models work unchanged

### From SDC4 to SDC5 (MAJOR)

**Migration required** - Breaking changes

Actions:
1. Read migration guide
2. Review breaking changes
3. Update models to new structure
4. Validate against new schema
5. Test with updated tools
6. Deploy when ready

**Tools Provided**:
- Automated migration scripts
- Validation checklist
- Before/after examples
- Tool compatibility matrix

---

## Git Tagging Strategy

### Tag Format

```
v4.0.0      # Release
v4.0.1      # Patch
v4.1.0      # Minor
v5.0.0      # Major (new SDC generation)

v4.1.0-rc.1 # Release candidate
v4.1.0-beta.1 # Beta
v4.1.0-alpha.1 # Alpha
```

### Branches

- `main` - Stable releases (4.0.0, 4.1.0, etc.)
- `develop` - Next MINOR version development
- `sdc5` - Next MAJOR version (when applicable)
- `hotfix/*` - Emergency fixes for current release

---

## Deprecation Policy

### MINOR Version Deprecations

Features can be **marked deprecated** in MINOR versions:

```
4.1.0: Feature X deprecated (warning added)
4.2.0: Feature X still works (warning remains)
4.3.0: Feature X still works (final warning)
5.0.0: Feature X removed (MAJOR version)
```

**Minimum deprecation period**: 3 MINOR versions or 1 year, whichever is longer.

### Deprecation Notices

Deprecated features marked in:
- Schema comments
- Specification documentation
- Changelog (Deprecated section)
- Runtime warnings (if applicable in tools)

---

## Version Support

| Version | Status | Support Level |
|---------|--------|---------------|
| 4.0.x | Current | Full support (features + security) |
| 3.x.x | Legacy | No support |

**Support duration**: Current MAJOR version supported until next MAJOR release + 6 months.

---

## FAQ

**Q: Can I use SDCStudio 4.1.0 with SDCRM 4.0.0?**
A: Yes! MINOR versions are backward compatible.

**Q: What happens to my models when SDC5 is released?**
A: Your SDC4 models continue to work. You migrate when ready.

**Q: How often are new MAJOR versions released?**
A: Rarely. SDC4 is designed for long-term stability (years).

**Q: Can I request new types in a MINOR version?**
A: Yes! Propose via GitHub issue. If optional and backward-compatible, it's a MINOR change.

**Q: What if I find a security issue?**
A: Report privately via security policy. Security fixes released as PATCH versions.

---

## References

- [Semantic Versioning 2.0.0](https://semver.org/)
- [Keep a Changelog](https://keepachangelog.com/)
- [GitHub Release Flow](https://docs.github.com/en/repositories/releasing-projects-on-github)

---

**Version stability is a core SDC principle. Breaking changes are rare and carefully managed.**
