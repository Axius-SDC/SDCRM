# Pull Request

## Description

**What does this PR do?**

## Type of Change

- [ ] Documentation fix/improvement
- [ ] New example
- [ ] Bug fix (non-breaking change that fixes an issue)
- [ ] New feature (non-breaking change that adds functionality)
- [ ] Breaking change (requires MAJOR version bump)
- [ ] Tool/validator addition

## Related Issues

**Closes #(issue number)**

**Related discussions**: (link if applicable)

## Changes Made

**Summary of changes**:

1.
2.
3.

## Testing

**How has this been tested?**

### For Schema Changes

- [ ] Schema validates against XSD spec: `xmllint --schema http://www.w3.org/2001/XMLSchema.xsd sdc4/schemas/sdc4.xsd`
- [ ] All examples validate: `xmllint --schema sdc4/schemas/sdc4.xsd --noout sdc4/examples/**/*.xml`
- [ ] Tested with SDCStudio (if applicable)

### For Examples

- [ ] Example validates against `sdc4.xsd`
- [ ] Example is well-commented
- [ ] Example demonstrates clear use case
- [ ] Added to examples README

### For Documentation

- [ ] Documentation matches `sdc4.xsd` (schema is source of truth)
- [ ] All links work
- [ ] Spelling and grammar checked
- [ ] Follows documentation style guide

### For Tools

- [ ] Tool works as expected
- [ ] Usage documentation provided
- [ ] Tested on target platforms

## Checklist

- [ ] I have read [CONTRIBUTING.md](../CONTRIBUTING.md)
- [ ] I have followed the coding/documentation style
- [ ] I have performed a self-review of my changes
- [ ] I have commented my code/examples where needed
- [ ] I have updated relevant documentation
- [ ] My changes generate no new warnings
- [ ] I have tested my changes
- [ ] All validations pass

## For Schema Changes (if applicable)

⚠️ **Schema changes require extra scrutiny**

- [ ] RFC opened and discussed (if breaking change)
- [ ] Community feedback addressed
- [ ] Migration path documented (if breaking)
- [ ] Version number updated appropriately
- [ ] CHANGELOG.md updated
- [ ] All related documentation updated
- [ ] All examples updated to validate

## Screenshots (if applicable)

**Add screenshots to help explain your changes**

## Additional Notes

**Any additional context or information for reviewers**:

---

## For Reviewers

**Areas that need special attention**:

**Questions for reviewers**:
