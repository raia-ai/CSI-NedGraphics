# Master Prompt: GitBook Framework Generation for AI Agent Vector Stores

## Objective

Create a production-ready GitBook repository from documentation files that serves dual purposes:
1. **AI Agent Integration**: Optimized structure for nightly scraping and vector store ingestion
2. **Human Editing**: Accessible GitBook interface for content updates by non-technical users

## Core Requirements

### 1. Direct GitBook Import Ready
- Generate a ZIP file that can be **directly imported** into GitBook without modification
- Include only essential files: `README.md`, `SUMMARY.md`, `.gitbook.yaml`, and content files
- All content must be in markdown format with proper YAML frontmatter
- File structure must follow GitBook conventions

### 2. No Placeholders or Temporary Content
- **Zero placeholder documents** - only include actual content files provided
- **No "Coming Soon" sections** - if content doesn't exist, don't create the section
- **No implementation guides** - this is production content, not a framework guide
- Every file must contain substantial, complete content
- Treat all content as **permanent and final**

### 3. AI-Optimized Structure
- Organize by **semantic categories** (product families, functional areas, or topics)
- Use **consistent naming conventions**: lowercase-with-hyphens for files and folders
- Create **clear hierarchical navigation** in SUMMARY.md for AI context understanding
- Ensure **metadata-rich frontmatter** on every document for vector store enrichment

### 4. YAML Frontmatter Format
Every content file must start with properly formatted YAML frontmatter:

```yaml
---
title: "Document Title"
source: "original-file-name.pdf"
tags: ["Category1", "Category2", "Feature", "Module"]
version: "1.0"
last_updated: "YYYY-MM-DD"
short_description: "One-sentence summary for quick reference"
long_description: "Comprehensive 2-3 paragraph description of content, audience, and key topics"
---
```

**Critical**: The opening `---` delimiter is **mandatory** - without it, GitBook displays metadata as raw text instead of parsing it.

### 5. Human Editing Workflow
- Humans edit content directly in GitBook's web interface
- Nightly scraper extracts updated content and converts to JSON
- JSON file updates the AI agent's vector store
- **No technical knowledge required** for content updates

## Input Requirements

You will receive:
1. **AI Agent System Prompt** (optional) - Context about the agent's purpose and capabilities
2. **Vector Store Files** or **Documentation Files** - The actual content to organize
3. **Any existing taxonomy guidance** (optional) - Preferred categorization approach

## Output Deliverables

### Single ZIP File Containing:

```
[ProjectName]_GitBook/
├── README.md                    # Overview and navigation guide
├── SUMMARY.md                   # Complete table of contents
├── .gitbook.yaml               # GitBook configuration
├── category1/                  # Semantic category folders
│   ├── document1.md
│   ├── document2.md
│   └── ...
├── category2/
│   └── ...
└── categoryN/
    └── ...
```

### File Specifications

#### README.md
- Professional introduction to the knowledge base
- Brief description of each category/product family
- Usage guidance (2-3 paragraphs)
- **No bullet lists** - use flowing paragraphs
- **No implementation instructions** - this is end-user documentation

#### SUMMARY.md
- Hierarchical navigation structure
- Group by category/product family
- Descriptive titles (not just filenames)
- Maximum 2-3 levels of nesting
- Format:
```markdown
# Table of Contents

* [Project Name](README.md)

## Category Name

* [Document Title](category/document-file.md)
* [Another Document](category/another-file.md)

## Another Category

* [Document Title](another/document.md)
```

#### .gitbook.yaml
```yaml
root: ./

structure:
  readme: README.md
  summary: SUMMARY.md
```

#### Content Files
- All markdown files in category subdirectories
- Proper YAML frontmatter (with opening `---`)
- Original content preserved exactly
- Clean, descriptive filenames

## Processing Steps

### Step 1: Analyze Content
1. Read all provided documentation files
2. Identify natural semantic groupings (products, features, document types)
3. Count total files and assess completeness
4. Note any language variations (EN/DE/etc.)

### Step 2: Design Taxonomy
1. Create 5-15 top-level categories based on content analysis
2. Assign each document to exactly one category
3. Use business-friendly category names (not technical jargon)
4. Ensure balanced distribution (avoid categories with 1-2 files or 50+ files)

### Step 3: Fix Frontmatter
1. Check every file for YAML frontmatter
2. Add opening `---` if missing
3. Verify all required fields present
4. Ensure proper YAML syntax

### Step 4: Build Structure
1. Create category folders
2. Copy files with clean, descriptive names
3. Generate comprehensive README.md
4. Generate complete SUMMARY.md with all files
5. Create .gitbook.yaml

### Step 5: Validate & Package
1. Verify all files have proper frontmatter
2. Check all links in SUMMARY.md are valid
3. Ensure no placeholder content exists
4. Create ZIP archive
5. Test extraction to verify structure

## Quality Checklist

Before delivering, verify:

- [ ] ZIP extracts cleanly with proper structure
- [ ] All content files have opening `---` in frontmatter
- [ ] SUMMARY.md includes every content file
- [ ] No placeholder documents or "Coming Soon" sections
- [ ] README.md is professional and complete
- [ ] Category names are clear and business-friendly
- [ ] File names are descriptive and use lowercase-with-hyphens
- [ ] No implementation guides or technical setup docs included
- [ ] All content is substantial and complete
- [ ] Package size is reasonable (< 50MB for typical documentation)

## Common Pitfalls to Avoid

❌ **Don't create placeholder documents** - only include actual content
❌ **Don't add implementation guides** - focus on end-user documentation
❌ **Don't forget opening `---`** - frontmatter won't parse without it
❌ **Don't use technical category names** - use business-friendly terms
❌ **Don't create empty directories** - only create folders with content
❌ **Don't include scraper scripts** - this is content only
❌ **Don't add "Getting Started" sections** - unless content exists
❌ **Don't treat this as a template** - it's production-ready content

## Success Criteria

✅ ZIP file imports directly into GitBook without errors
✅ All metadata displays as "Quick Reference" tables
✅ Navigation is intuitive for both humans and AI
✅ Every document is substantial and complete
✅ Structure supports nightly scraping for vector store updates
✅ Non-technical users can edit content in GitBook
✅ AI agent can semantically search and retrieve information
✅ Content is organized by business value, not file structure

## Example Taxonomy Patterns

### Pattern 1: Product-Based (Software Suite)
```
- Overview
- Product A
- Product B
- Product C
- Cross-Product Features
- Tools & Utilities
```

### Pattern 2: Function-Based (Single Product)
```
- Getting Started
- Configuration
- User Guides
- Administration
- API Reference
- Troubleshooting
```

### Pattern 3: Audience-Based (Multi-Audience)
```
- Executive Overview
- End User Documentation
- Administrator Guides
- Developer Resources
- Technical Reference
```

### Pattern 4: Workflow-Based (Process-Oriented)
```
- Planning & Setup
- Daily Operations
- Reporting & Analytics
- Maintenance & Support
- Advanced Features
```

Choose the pattern that best matches the content and business context.

## Final Notes

This is a **production deployment**, not a framework or template. Every file must be complete, every section must have real content, and the entire package must be ready for immediate use by both AI agents and human editors. Treat this as a permanent knowledge base that will be maintained through GitBook's interface, not through file system changes.

The GitBook serves as the **single source of truth** - humans edit it, AI scrapes it, and both benefit from the structured, accessible format.

