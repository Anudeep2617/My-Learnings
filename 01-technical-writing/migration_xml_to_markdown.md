# XML to Markdown Migration Guide

## 1. Overview

This guide explains how to migrate technical documentation from XML-based source files to Markdown while preserving the content structure, formatting, links, images, and meaning of the original documents.

XML is commonly used in structured authoring environments where elements and attributes define document structure and metadata. Markdown uses a simpler, readable syntax for headings, lists, links, images, tables, and code blocks.

Although both formats can represent technical information, they do not support exactly the same features. Therefore, a successful migration requires more than replacing XML tags with Markdown syntax. It also requires content analysis, mapping rules, link validation, rendering checks, and review by the documentation team.

This guide uses illustrative XML and Markdown examples. Actual conversion rules depend on the XML vocabulary, authoring tool, Markdown flavor, and publishing platform.

## 2. Objectives

The migration aims to:

- Preserve the original meaning and technical accuracy of the content.
- Maintain the heading hierarchy and document organization.
- Convert XML elements into appropriate Markdown structures.
- Preserve hyperlinks, images, tables, code samples, and cross-references.
- Identify XML-specific features that require manual conversion.
- Minimize broken links, missing content, and rendering differences.
- Establish a repeatable process for future documentation updates.

## 3. Scope

### 3.1 Included Content

The migration covers the following content types:

- Titles and section headings
- Paragraphs and inline formatting
- Ordered and unordered lists
- Tables
- Hyperlinks and cross-references
- Images and captions
- Code samples and command-line examples
- Notes, warnings, and important information
- File attachments and related resources

### 3.2 Items Requiring Special Review

Some XML-based documentation systems support features that standard Markdown does not provide directly:

- Conditional content and audience-specific filtering
- Reusable content and variables
- Topic references and automatically generated links
- Metadata and indexing attributes
- Complex tables and specialized elements
- Custom formatting and publishing-specific behavior

These features must be mapped to the target platform's capabilities or handled through an approved alternative.

## 4. Pre-Migration Assessment

Before converting the files, review the source documentation and identify the structures and dependencies that must be preserved.

### 4.1 Inventory the Source Files

Create an inventory of the XML files and their related assets.

Record the following information:

| Item | Purpose |
|---|---|
| Source filename | Identifies the original XML file. |
| Document title | Identifies the topic or guide. |
| XML vocabulary | Identifies the structure and element rules used by the source. |
| Referenced assets | Lists images, attachments, and other supporting files. |
| Cross-references | Identifies links to other topics or sections. |
| Special features | Identifies variables, conditional content, and custom elements. |
| Target filename | Defines the corresponding Markdown destination. |

### 4.2 Identify the XML Structure

Inspect the source file to understand how its elements represent document content.

For example, a structured XML document might use elements such as `<title>`, `<section>`, `<p>`, `<ul>`, `<li>`, `<codeblock>`, and `<xref>`.

Do not assume that every XML vocabulary uses the same element names. A DITA topic, DocBook document, and custom XML schema may represent equivalent content differently.

### 4.3 Establish Migration Rules

Create a mapping table before processing the full document set.

| XML element or feature | Markdown equivalent | Migration consideration |
|---|---|---|
| Document title | `# Title` | Use one top-level heading for the document title. |
| Section title | `## Heading` | Preserve the original hierarchy. |
| Subsection title | `### Heading` | Avoid skipping heading levels unnecessarily. |
| Paragraph | Plain text | Preserve meaning, punctuation, and paragraph breaks. |
| Bold formatting | `**text**` | Check the target renderer's supported syntax. |
| Italic formatting | `*text*` | Preserve emphasis. |
| Unordered list | `- Item` | Preserve list nesting and item order. |
| Ordered list | `1. Item` | Preserve sequence and nesting. |
| Inline code | `` `code` `` | Preserve commands, filenames, parameters, and identifiers. |
| Code block | Fenced code block | Specify a language where appropriate. |
| Hyperlink | `[Link text](path-or-url)` | Verify the destination and preserve meaningful link text. |
| Image | `![Alt text](path)` | Preserve the asset and meaningful alternative text. |
| Simple table | Markdown table | Check alignment and renderer support. |
| Note or warning | Platform-supported callout or blockquote | Preserve the severity and meaning of the original notice. |
| Cross-reference | Markdown link | Resolve the destination topic or heading. |
| Variable or conditional content | Platform-specific mechanism or manual rewrite | Preserve the intended audience and publishing behavior. |

This mapping table becomes the team's reference for consistent conversion.

## 5. Conversion Examples

### 5.1 Convert Headings

**XML source**

```xml
<section>
  <title>Configure the Application</title>
  <section>
    <title>Database Settings</title>
    <p>Configure the database connection before starting the application.</p>
  </section>
</section>
```

**Markdown output**

```markdown
## Configure the Application

### Database Settings

Configure the database connection before starting the application.
```

**Explanation**

The section hierarchy determines the Markdown heading levels. A migration must preserve the relationship between parent sections and subsections rather than assigning heading levels based only on the appearance of the source text.

Validate that the converted document has a logical heading hierarchy and that any links targeting headings still work.

### 5.2 Convert Lists

**XML source**

```xml
<ul>
  <li>Install the application server.</li>
  <li>Configure the database.</li>
  <li>Deploy the application.</li>
</ul>
```

**Markdown output**

```markdown
- Install the application server.
- Configure the database.
- Deploy the application.
```

**Explanation**

Use hyphens for unordered lists and numbered items for ordered lists. Preserve the original sequence, nested relationships, and any formatting within list items.

For nested lists, verify indentation in the target Markdown renderer. Different publishing tools may interpret indentation and mixed list structures differently.

### 5.3 Convert Tables

**XML source**

```xml
<table>
  <row>
    <entry>Parameter</entry>
    <entry>Description</entry>
  </row>
  <row>
    <entry>limit</entry>
    <entry>Maximum number of records to return.</entry>
  </row>
</table>
```

**Markdown output**

```markdown
| Parameter | Description |
|---|---|
| limit | Maximum number of records to return. |
```

**Explanation**

Simple tables can be converted directly. Complex tables may contain merged cells, nested lists, multiple paragraphs, or other structures that basic Markdown tables cannot represent reliably.

For complex tables:

1. Check whether the target platform supports extended table syntax.
2. Simplify the structure only if the information remains clear and accurate.
3. Split a complex table into smaller tables when appropriate.
4. Use a supported HTML or alternative format only if the publishing platform permits it.
5. Review the rendered result for missing content and readability.

### 5.4 Convert Hyperlinks and Cross-References

**XML source**

```xml
<p>
  For details, see
  <xref href="installation.xml">Installation Guide</xref>.
</p>
```

**Markdown output**

```markdown
For details, see [Installation Guide](installation.md).
```

**Explanation**

The Markdown link must point to the correct destination file or URL. Changing the source filename alone is not enough.

During migration:

1. Identify the original target of each cross-reference.
2. Determine the destination Markdown filename.
3. Update the link to the new location.
4. Check heading anchors if the link targets a specific section.
5. Test the link after publishing or rendering the Markdown.

Avoid using generic link text such as "click here" when a descriptive title is available.

### 5.5 Convert Images

**XML source**

```xml
<image href="images/configuration-screen.png">
  <alt>Application configuration screen</alt>
</image>
```

**Markdown output**

```markdown
![Application configuration screen](images/configuration-screen.png)
```

**Explanation**

Markdown uses the alternative text and the image path to display the image.

Preserve the original image assets unless a replacement is required. When changing the folder structure, update the relative paths in the Markdown files.

Verify the following:

- The image file exists in the repository.
- The filename and extension match the reference.
- The relative path is correct.
- Alternative text describes the image's purpose.
- The image renders correctly in the target platform.

### 5.6 Convert Code Samples

**XML source**

```xml
<codeblock>
curl -X GET https://api.example.com/v1/items
</codeblock>
```

**Markdown output**

````markdown
```bash
curl -X GET https://api.example.com/v1/items
```
````

**Explanation**

Use fenced code blocks for commands, source code, configuration examples, and JSON payloads. Add a language identifier where appropriate to support syntax highlighting.

Check that conversion has not changed quotation marks, indentation, escape characters, or special symbols. These changes can make a command or code example incorrect.

The endpoint above is illustrative and is not intended to represent a verified API.

### 5.7 Convert Notes and Warnings

**XML source**

```xml
<note>
  Back up the configuration before upgrading the application.
</note>
```

**Markdown output using a portable format**

```markdown
> **Note:** Back up the configuration before upgrading the application.
```

**Explanation**

A blockquote is a broadly supported option, but it may not preserve the original visual styling or semantic behavior of a specialized XML note.

If the target documentation platform supports dedicated note, warning, or danger callouts, use its documented syntax. Preserve the original message's importance and do not turn a warning into ordinary explanatory text.

## 6. Handle XML Features Without Direct Markdown Equivalents

### 6.1 Reusable Content

Some XML authoring systems support reusable snippets that are maintained once and included in multiple documents.

Markdown does not define one universal mechanism for reusable content.

Possible approaches include:

- Use the publishing platform's supported include mechanism.
- Store shared content in a controlled partial or snippet file.
- Use a build-time content-generation process.
- Duplicate content only when reuse is not required and the maintenance implications are understood.

Before selecting an approach, determine how shared content is updated, reviewed, and published.

### 6.2 Variables and Conditional Content

XML documentation may use variables or conditional attributes to generate different content for different product versions, audiences, or deployment environments.

During migration:

1. Identify every variable and conditional rule.
2. Determine which output variants are required.
3. Map each rule to the target platform's supported mechanism.
4. Confirm that the correct content appears in each published version.
5. Document any functionality that cannot be reproduced directly.

Do not remove conditional attributes without checking whether they control important product-specific instructions.

### 6.3 Metadata and Indexing

XML source files may contain metadata for document IDs, product versions, authors, keywords, or navigation.

Identify which metadata fields are required by the target platform. Convert them to supported front matter, repository metadata, or publishing configuration where appropriate.

Do not copy XML attributes into Markdown headings or body text unless they are intended for readers.

## 7. Migration Workflow

Use a repeatable workflow to reduce conversion errors.

### Step 1: Inventory

Identify the source XML files, linked topics, image assets, reusable content, and special markup.

### Step 2: Define Mapping Rules

Document the XML-to-Markdown mapping and agree on naming, heading, link, image, and callout conventions.

### Step 3: Convert a Representative Sample

Select documents containing a range of structures, such as headings, lists, tables, code samples, links, and images.

Convert these first to discover limitations before processing the entire documentation set.

### Step 4: Review and Refine

Compare the original XML with the converted Markdown. Correct mapping rules where content or structure has been lost.

### Step 5: Convert the Remaining Files

Apply the approved conversion rules. Use automated processing where appropriate, but flag unsupported or ambiguous structures for manual review.

### Step 6: Update Dependencies

Update internal links, image references, filenames, navigation, and references to reusable content.

### Step 7: Validate the Output

Run link checks and Markdown linting where available. Render the documents using the target publishing platform and inspect the output.

### Step 8: Perform Technical Review

Ask the relevant subject matter expert or document owner to verify technical accuracy, completeness, and product-specific behavior.

### Step 9: Publish and Archive

Publish the approved Markdown files. Retain the original XML files and migration records according to the team's version-control and retention practices.

## 8. Quality Assurance Checklist

### Content Integrity

- [ ] All source topics have been accounted for.
- [ ] No paragraphs, list items, or table entries are missing.
- [ ] Technical terms, identifiers, and commands are unchanged unless intentionally revised.
- [ ] Warnings, notes, and prerequisites retain their original meaning.

### Structure and Formatting

- [ ] Heading hierarchy is consistent.
- [ ] Lists retain their nesting and order.
- [ ] Tables render correctly.
- [ ] Code samples use appropriate fenced blocks.
- [ ] Images have descriptive alternative text.

### Links and Assets

- [ ] Internal links point to the correct Markdown files.
- [ ] Heading anchors resolve correctly.
- [ ] External URLs are valid.
- [ ] All referenced images and attachments are present.
- [ ] Relative paths work in the target repository structure.

### Publishing and Review

- [ ] Markdown linting or automated checks have passed, where configured.
- [ ] The target publishing system renders the documents correctly.
- [ ] Conditional and reusable content behaves as intended.
- [ ] Technical review is complete.
- [ ] The converted files have been reviewed and approved before publication.

## 9. Common Migration Problems

| Problem | Likely cause | Recommended action |
|---|---|---|
| Broken internal links | XML filenames or reference IDs were not mapped correctly | Create and validate a source-to-target link mapping. |
| Missing images | Asset paths changed during migration | Copy the assets and update relative paths. |
| Incorrect heading hierarchy | XML nesting was not preserved | Rebuild headings based on the source structure. |
| Tables render incorrectly | Source table contains unsupported structures | Simplify or convert the table using a supported alternative. |
| Conditional content disappears | XML filtering rules were discarded | Reimplement the required rules or generate the required variants. |
| Code examples fail | Special characters or formatting changed | Compare the original and converted code and test executable examples. |
| Duplicate content | Reusable XML content was expanded without a reuse strategy | Establish a supported approach for shared content. |

## 10. Migration Completion Criteria

Consider the migration complete when:

- All in-scope source documents have been converted or explicitly excluded with an approved reason.
- Content, structure, links, and assets have been checked.
- Unsupported XML-specific features have approved alternatives.
- Automated validation has passed or remaining issues have been documented.
- Technical and editorial reviews are complete.
- The Markdown files render correctly in the intended publishing environment.
- The team has documented the conversion rules for future maintenance.

## 11. Conclusion

Migrating XML documentation to Markdown requires both structural conversion and editorial quality assurance. A consistent mapping strategy, careful handling of XML-specific features, link and asset validation, and technical review help preserve the accuracy and usability of the documentation.

The migration should be treated as a controlled documentation project rather than a simple file-format conversion.

## 12. Revision History

| Version | Description |
|---|---|
| 1.0 | Initial version of the illustrative XML-to-Markdown migration guide. |
