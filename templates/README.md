# ProteinGym README Templates

This directory contains generic README templates for ProteinGym repositories. These templates can be adapted and customized for specific repositories within the ProteinGym organization.

## Available Templates

### 1. Organization Profile (`/profile/README.md`)
- **Purpose**: Main README displayed on the ProteinGym GitHub organization page
- **Location**: Already in place at `/profile/README.md`
- **Usage**: This is automatically displayed when visiting https://github.com/ProteinGym
- **Customization**: Update links, add new repositories, or modify content as the organization grows

### 2. ProteinGym-base Template (`README_ProteinGym_base.md`)
- **Purpose**: Template for the ProteinGym-base repository (core infrastructure)
- **Intended Use**: When creating the ProteinGym-base repository
- **Focus**: Data processing, evaluation framework, utility functions
- **Key Sections**:
  - Installation instructions
  - Core modules documentation
  - Data format standards
  - API examples
  - Contributing guidelines

### 3. ProteinGym-benchmark Template (`README_ProteinGym_benchmark.md`)
- **Purpose**: Template for the ProteinGym-benchmark repository (model implementations)
- **Intended Use**: When creating the ProteinGym-benchmark repository
- **Focus**: Model baselines, benchmarking workflows, scoring scripts
- **Key Sections**:
  - Available models and baselines
  - Benchmarking workflows
  - Model integration guide
  - Performance metrics
  - Submission process

## How to Use These Templates

### For New Repositories

1. **Create the new repository** on GitHub (e.g., ProteinGym-base or ProteinGym-benchmark)

2. **Copy the appropriate template**:
   ```bash
   # For ProteinGym-base
   cp templates/README_ProteinGym_base.md /path/to/ProteinGym-base/README.md
   
   # For ProteinGym-benchmark
   cp templates/README_ProteinGym_benchmark.md /path/to/ProteinGym-benchmark/README.md
   ```

3. **Customize the template**:
   - Update installation instructions with actual package names
   - Add real links to documentation, datasets, and resources
   - Modify examples to match actual API
   - Update dependency lists
   - Add actual repository structure
   - Include real version numbers and release information

4. **Fill in placeholders**:
   - Replace `[docs link to be added]` with actual documentation URLs
   - Update `[model list]` references with complete information
   - Add actual file paths and directory structures
   - Include real configuration examples

5. **Add repository-specific content**:
   - Specific features unique to your repository
   - Custom configuration options
   - Special installation requirements
   - Repository-specific examples

### For the Organization Profile

The organization profile README is already in place at `/profile/README.md`. To update it:

1. **Edit the file**:
   ```bash
   cd /home/runner/work/.github/.github
   # Edit profile/README.md with your changes
   ```

2. **Common updates**:
   - Add new repositories to the "Our Repositories" section
   - Update statistics (number of variants, assays, etc.)
   - Add new features or announcements
   - Update links and badges
   - Add community highlights or news

3. **Commit and push changes**:
   ```bash
   git add profile/README.md
   git commit -m "Update organization profile"
   git push
   ```

## Template Customization Guidelines

### Maintaining Consistency

- Keep the overall structure and tone consistent across all READMEs
- Use the same badge style and formatting
- Maintain similar section organization
- Follow the same code example style

### Required Sections

All templates should include:
- Overview/Description
- Installation instructions
- Quick start guide
- Documentation links
- Contributing guidelines
- Citation information
- License information
- Contact information

### Optional Sections

Add as needed:
- Detailed API documentation
- Advanced usage examples
- Troubleshooting guide
- Performance benchmarks
- Changelog
- Roadmap
- FAQ

### Styling Guidelines

- Use clear, concise language
- Include code examples where appropriate
- Use tables for structured information
- Add badges for quick status information
- Use emoji sparingly for visual organization
- Include diagrams or architecture images when helpful

## Updating Templates

When updating these templates:

1. **Test changes** with a sample repository first
2. **Get feedback** from the team
3. **Update all templates** to maintain consistency
4. **Document changes** in this README
5. **Communicate updates** to repository maintainers

## Links and References

### ProteinGym Resources
- Main Repository: https://github.com/OATML-Markslab/ProteinGym
- Website: https://www.proteingym.org/
- Documentation: [To be added]
- HuggingFace: https://huggingface.co/datasets/OATML-Markslab/ProteinGym_v1
- PyPI: https://pypi.org/project/proteingym/

### GitHub Documentation
- [About organization profiles](https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/customizing-your-organizations-profile)
- [Basic writing and formatting syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
- [Working with advanced formatting](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting)

## Questions or Suggestions

If you have questions about these templates or suggestions for improvements:
- Open an issue in this repository
- Contact the ProteinGym team
- Submit a pull request with proposed changes

---

**Last Updated**: October 2025
**Maintained By**: ProteinGym Team
