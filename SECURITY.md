# Security Policy

## Reporting Security Vulnerabilities

The SkillOS project takes security seriously. If you discover a security vulnerability, please **do not** open a public GitHub issue. Instead, follow the responsible disclosure process below.

---

## Responsible Disclosure

### How to Report

1. **Email the maintainers** at: [security@skillos-project.org](mailto:security@skillos-project.org)
   - Include a clear description of the vulnerability
   - Provide steps to reproduce the issue
   - Include your contact information

2. **Use GitHub Private Security Advisory** (if available):
   - Go to the repository's Security tab
   - Click "Report a vulnerability"
   - Fill in the details privately

3. **Contact Core Maintainers** (if emails above don't work):
   - Open a private discussion in GitHub (if available)
   - Message maintainers directly with "SECURITY" in the subject

### What to Include

- **Vulnerability Type:** (e.g., code injection, data exposure, authentication bypass)
- **Component Affected:** (e.g., Skill Creator, validator, specific skill)
- **Severity Assessment:** (Critical/High/Medium/Low)
- **Description:** Clear explanation of the vulnerability
- **Steps to Reproduce:** Detailed instructions (if applicable)
- **Proof of Concept:** Code, screenshots, or examples (if safe to share)
- **Impact Analysis:** What could an attacker do with this vulnerability?
- **Suggested Fix:** Your ideas on how to patch it (optional)

---

## Security Best Practices for Contributors

### When Contributing Skills or Code

1. **Never commit secrets:**
   - API keys, tokens, credentials
   - Private configuration files
   - Sensitive test data
   - Use `.env.example` as a template instead

2. **Validate user input:**
   - Don't trust user-provided prompts
   - Sanitize inputs before processing
   - Validate skill configurations

3. **Follow principle of least privilege:**
   - Only request permissions you need
   - Document why each permission is required
   - Minimize data access

4. **Secure dependencies:**
   - Keep dependencies up-to-date
   - Review dependencies before adding
   - Use lock files (package-lock.json, etc.)
   - Check for known vulnerabilities

5. **Document security considerations:**
   - Add comments about security decisions
   - Explain why certain patterns are used
   - Document potential attack vectors

---

## Security in Skills

### Skill-Specific Guidelines

1. **Assumption Documentation**
   - Document security assumptions in the Ethical Constraint Layer
   - Consider data access patterns
   - Flag if a skill has higher security impact

2. **Boundary Recognition**
   - Route to security specialist if needed
   - Don't attempt security-critical operations outside expertise
   - Flag compliance or regulatory requirements

3. **Error Handling**
   - Don't expose sensitive information in error messages
   - Log security events appropriately
   - Handle failures gracefully

---

## Response Timeline

After receiving a security report:

- **24 hours:** Initial acknowledgment
- **3-5 days:** Security team begins investigation
- **7-14 days:** Potential patch or workaround provided
- **30 days:** Public disclosure (after patch release) OR timeline adjusted based on severity

---

## Severity Assessment

### Critical (Immediate Action Required)
- Remote code execution
- Authentication bypass
- Data exposure at scale
- System-wide compromise

**Response:** Immediate hotfix, security advisory, possible emergency release

### High (Urgent)
- Privilege escalation
- Data access without authorization
- Significant performance degradation
- Denial of service

**Response:** Patch within 1-2 weeks, security advisory

### Medium (Moderate)
- Information disclosure
- Local privilege escalation
- Usability issues with security implications

**Response:** Patch in regular release cycle

### Low (Minor)
- Security hardening
- Defense-in-depth improvements
- Documentation gaps
- Best practice violations

**Response:** Include in next regular release

---

## Security Updates

### Staying Informed

- **Watch releases:** Star and watch the repository
- **Security advisories:** GitHub notifications for known vulnerabilities
- **Mailing list:** (Planned) Subscribe for security announcements
- **Social media:** Follow @SkillOS for announcements

### Patching

- Security patches are released as soon as possible
- Always update to the latest version
- Don't use outdated or end-of-life versions
- Check the CHANGELOG for security notes

---

## Scope of SkillOS Security

### In Scope

- Skill Creator compiler functionality
- SDS validation logic
- GitHub Actions workflows
- Registry storage and integrity
- API endpoints (if any)
- Authentication and authorization (if implemented)

### Out of Scope

- Skills themselves (reported directly to skill maintainers)
- Third-party dependencies (report to upstream projects)
- User's local environment (outside SkillOS control)
- Infrastructure hosting (report to hosting provider)

---

## Attribution & Recognition

After a security issue is patched, we'd like to recognize the security researcher (unless they prefer anonymity):

- Credit in the security advisory
- Mention in CHANGELOG
- Optional: Social media recognition
- Optional: GitHub repository credit

---

## Questions?

If you have questions about security reporting or policies:
- Open a **non-public** discussion if GitHub supports it
- Email the maintainers marked "SECURITY INQUIRY"
- Do not discuss vulnerabilities in public issues

---

## Related Documents

- [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md) - Community guidelines
- [CONTRIBUTING.md](./CONTRIBUTING.md) - Contribution process
- [SKILL-DEFINITION-STANDARD.md](./SKILL-DEFINITION-STANDARD.md) - Security constraints in skills

---

**Last Updated:** 2026-07-12  
**Policy Version:** 1.0  
**Maintained By:** SkillOS Security Team
