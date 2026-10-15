# MadCap Flare: Beginner-to-Advanced Technical Writer's Guide

**Purpose:** A practical learning guide for technical writers using
MadCap Flare Desktop, Git, structured authoring, and multi-format
publishing.

**Audience:** Beginner to advanced technical writers\
**Version note:** Menu names and capabilities can vary by Flare release,
project template, license, and whether you use Flare Desktop or Flare
Online. Treat the procedures below as a workflow guide and confirm exact
menu labels in the help for your installed version.

------------------------------------------------------------------------

## Table of contents

1.  [What MadCap Flare does](#1-what-madcap-flare-does)
2.  [Core concepts and terminology](#2-core-concepts-and-terminology)
3.  [Create a new Flare project](#3-create-a-new-flare-project)
4.  [Understand the project
    structure](#4-understand-the-project-structure)
5.  [Create and edit topics](#5-create-and-edit-topics)
6.  [Build and edit a table of
    contents](#6-build-and-edit-a-table-of-contents)
7.  [Create and use snippets](#7-create-and-use-snippets)
8.  [Create and use variables](#8-create-and-use-variables)
9.  [Images and other assets](#9-images-and-other-assets)
10. [Bulk import from Word and other
    sources](#10-bulk-import-from-word-and-other-sources)
11. [Styles, stylesheets, and page
    layouts](#11-styles-stylesheets-and-page-layouts)
12. [Conditions and single-sourcing](#12-conditions-and-single-sourcing)
13. [Links, cross-references, and
    navigation](#13-links-cross-references-and-navigation)
14. [Structured authoring and content
    architecture](#14-structured-authoring-and-content-architecture)
15. [Git: local repository, branches, commits, and pull
    requests](#15-git-local-repository-branches-commits-and-pull-requests)
16. [Build and publish HTML5, PDF, and other
    outputs](#16-build-and-publish-html5-pdf-and-other-outputs)
17. [CMS and team content
    management](#17-cms-and-team-content-management)
18. [Review, quality checks, and
    troubleshooting](#18-review-quality-checks-and-troubleshooting)
19. [Recommended end-to-end
    workflow](#19-recommended-end-to-end-workflow)
20. [Beginner-to-pro learning plan](#20-beginner-to-pro-learning-plan)
21. [Official learning resources](#21-official-learning-resources)

------------------------------------------------------------------------

## 1. What MadCap Flare does

MadCap Flare is a technical authoring and publishing tool. It lets a
documentation team maintain content in reusable components and publish
it to different outputs, such as responsive HTML5 help and PDF, from a
managed project.

Typical uses include:

-   Product user guides and online help.
-   Installation, configuration, and upgrade guides.
-   API and developer documentation.
-   Release notes and troubleshooting articles.
-   Print-ready manuals and PDFs.
-   Multiple versions or editions of documentation using shared content.

The key idea is **single-source publishing**: author content once where
practical, then reuse and assemble it for different audiences or
formats.

Flare is not simply a word processor. A Flare project includes topics,
images, stylesheets, snippets, variables, condition tags, tables of
contents (TOCs), targets, and other configuration files.

## 2. Core concepts and terminology

  
  |Term   |Meaning  | Example|
  |-------|--------|--------|
  |Project |The complete set of source content and publishing configuration |Identity product documentation |          

  Topic                   A standalone content    Configure SSO
                          file that explains one  
                          subject or task         

  TOC                     An outline/navigation   Installation \>
                          structure that          Configure the server
                          organizes topics        

  Snippet                 Reusable formatted      A common security note
                          content inserted into   
                          multiple topics         

  Variable                Reusable short text or  ProductName,
                          dynamic value           VersionNumber

  Stylesheet              Rules controlling the   Heading styles, tables,
                          appearance of content   notes

  Condition tag           A label used to include CloudOnly, OnPremOnly
                          or exclude content in a 
                          target                  

  Target                  A configuration for a   HTML5 Help, PDF User
                          particular output       Guide

  Skin                    The presentation and    HTML5 navigation design
                          navigation framework    
                          for supported online    
                          outputs                 

  Page layout             Print-page design such  PDF title page and
                          as headers, footers,    footer
                          and margins             

  Cross-reference         A link to another topic See Configure SSO
                          or bookmark within the  
                          project                 

  Repository              Version-controlled      Git repository
                          project history and     
                          collaboration area      

  Branch                  An independent line of  feature/add-sso-guide
                          work in Git             

  Pull request (PR)       A request to review and Merge documentation
                          merge branch changes    updates

  CMS/CCMS                A system for managing   Enterprise component
                          content, reuse,         content management
                          permissions, and        
                          workflows               
  -----------------------------------------------------------------------

A common Flare Desktop project uses a `Content` folder for topics and
resources, a `Project` folder for project configuration, and dedicated
folders for TOCs and targets. Folder names and the exact layout may vary
by template or team convention.

## 3. Create a new Flare project

### 3.1 Plan before creating the project

Decide:

1.  Product or feature name.
2.  Intended audience and user tasks.
3.  Outputs required: HTML5, PDF, Word, or others.
4.  Whether content needs multiple product versions, editions, or
    deployment models.
5.  Whether Git or another source control system will be used.
6.  Whether the team has an approved template, stylesheet, glossary, or
    folder convention.

### 3.2 Create the project

1.  Open MadCap Flare Desktop.
2.  Select the option to create a new project.
3.  Choose an appropriate project template, if your organization
    provides one.
4.  Enter a project name and choose a local folder.
5.  Select the required starting content and output options as prompted.
6.  Finish the wizard and open the project.
7.  Save the project and confirm it builds before making extensive
    changes.

**Best practice:** Use the company template when available. It may
already include approved styles, variables, page layouts, TOCs, skins,
and targets. Avoid rebuilding those assets without a reason.

### 3.3 Create a useful folder structure

A possible structure is:

``` text
ProductDocs/
├── Content/
│   ├── Home.htm
│   ├── Concepts/
│   ├── Tasks/
│   ├── Reference/
│   ├── Troubleshooting/
│   └── Resources/
│       ├── Images/
│       ├── Snippets/
│       ├── Stylesheets/
│       ├── PageLayouts/
│       └── Templates/
├── Project/
├── TOCs/
├── Targets/
└── Output/
```

This is an illustrative convention, not a mandatory Flare structure. Use
the folders created by Flare and align additional folders with your
team's standards. Do not move project files around in File Explorer
while Flare is open unless you understand the implications for links and
project configuration.

## 4. Understand the project structure

The Project Organizer and Content Explorer are central navigation areas
in Flare Desktop. Their exact labels and arrangement depend on the
version and workspace layout.

Common assets include:

-   **Topics:** `.htm` files containing the main authored content.
-   **Snippets:** commonly `.flsnp` files.
-   **Variable sets:** commonly `.flvar` files.
-   **TOCs:** commonly `.fltoc` files.
-   **Targets:** commonly `.fltar` files.
-   **Condition tag sets:** commonly `.flcts` files.
-   **Stylesheets:** `.css` files.
-   **Images:** PNG, JPG/JPEG, GIF, SVG, and other supported formats.
-   **Page layouts:** print-oriented layout files.
-   **Skins:** online-output presentation configuration.

Use Flare's file creation and management features where possible. The
project's internal links and references can be affected by moving or
renaming files outside the application.

## 5. Create and edit topics

### 5.1 What makes a good topic?

A topic should answer one primary user question or help the reader
complete one task. Avoid making one enormous topic contain an entire
manual.

Examples:

-   `About-role-management.htm`
-   `Create-a-role.htm`
-   `Configure-sso.htm`
-   `Troubleshoot-login-failures.htm`

Use a naming convention consistently. Prefer meaningful names and avoid
filenames such as `new-topic-2.htm` or `final-final.htm`.

### 5.2 Create a topic

1.  In the project's content area, select the folder where the topic
    belongs.
2.  Use the new-file/topic command or the project's equivalent
    context-menu command.
3.  Choose a topic template if prompted.
4.  Give the topic a descriptive filename.
5.  Open the topic in the editor.
6.  Add a clear title and write the content.
7.  Apply paragraph and character styles instead of manually formatting
    every element.
8.  Save the topic.

The topic title shown to users may be controlled by the heading in the
topic, the TOC entry, or output settings. Check the rendered result
rather than assuming the filename is the displayed title.

### 5.3 Recommended topic structure

A procedural topic might use this structure:

``` text
Title: Configure single sign-on

Purpose / short introduction

Prerequisites
- Required role or permission
- Required configuration

Procedure
1. Open the relevant settings page.
2. Enter the required values.
3. Save the configuration.

Verification
- Confirm the status is Enabled.

Troubleshooting or related links
```

A conceptual topic might explain what a feature does, how it works,
limitations, and related concepts. A reference topic might use tables
for fields, parameters, values, or error codes.

Do not force every topic into exactly the same structure. Choose the
structure that matches the reader's goal.

### 5.4 Edit a topic

1.  Locate the topic in the content explorer.
2.  Open it in the editor.
3.  Make the change in the appropriate section.
4.  Use heading styles in the correct hierarchy; do not select a heading
    style only because it looks larger.
5.  Add or update links and images.
6.  Save.
7.  Preview the topic in the relevant target.
8.  Check links, formatting, accessibility, and the actual workflow.

### 5.5 Source/code view

Flare topics are XML/XHTML-based. Advanced writers may inspect the
source to troubleshoot markup or perform controlled edits. Use source
view only when you understand the markup. Invalid tags or malformed
nesting can break rendering or builds. Keep a backup or Git commit
before broad source-level changes.

### 5.6 Review topic links and dependencies

Use Flare's link analysis tools, such as Link Viewer where available, to
inspect relationships between topics, images, stylesheets, snippets, and
other files. Before deleting a topic, search for references to it and
update any TOC entries or links.

## 6. Build and edit a table of contents

### 6.1 What a TOC does

For online output, a TOC commonly provides navigation or menu structure.
For print output, it acts as an outline that determines topic order; the
printed TOC page itself is usually generated through print TOC settings
or a TOC proxy, depending on the project configuration.

### 6.2 Create a TOC

1.  Locate the TOCs area in the Project Organizer.
2.  Create a new TOC or open the existing one.
3.  Add a book (a parent navigation item) or a topic entry.
4.  Link each entry to the appropriate topic or supported destination.
5.  Arrange entries into a logical hierarchy.
6.  Save the TOC.
7.  Open the target and associate the TOC with it.
8.  Build the target and verify the navigation.

### 6.3 Add topics to the TOC

Depending on the Flare version, you can drag topics from the content
explorer into the TOC editor, or create entries in the TOC editor and
select their linked files.

A typical hierarchy might be:

``` text
Getting Started
  Overview
  Prerequisites
  Sign In

Administration
  Manage Users
  Configure Roles
  Configure SSO

Troubleshooting
  Login Problems
  Common Error Messages
```

The labels in the TOC can be more reader-friendly than the source
filenames.

### 6.4 Edit and maintain a TOC

-   **Change order:** Move entries up or down or drag them into the
    correct position.
-   **Create hierarchy:** Nest topic entries under books.
-   **Rename a navigation label:** Change the TOC entry label without
    unnecessarily renaming the topic file.
-   **Change a linked topic:** Edit the entry's destination.
-   **Remove an entry:** Remove it from the TOC. This does not
    necessarily delete the source topic.
-   **Delete a topic:** Separately verify whether the topic is
    referenced elsewhere before deleting it.
-   **Validate:** Build and test all links and navigation in the output.

### 6.5 TOC best practices

-   Organize around user tasks and mental models, not the organization
    chart.
-   Use short, scannable labels.
-   Avoid too many levels of nesting.
-   Keep naming and capitalization consistent.
-   Check that important topics are reachable from the TOC or other
    appropriate navigation.
-   Maintain separate TOCs when audiences or outputs need different
    structures.

## 7. Create and use snippets

### 7.1 When to use a snippet

A snippet is reusable formatted content. It can contain text,
paragraphs, tables, images, and other supported content. Use it when the
same block needs to appear in multiple places and should be maintained
centrally.

Good examples:

-   A recurring security warning.
-   A standard prerequisite block.
-   A shared configuration note.
-   A repeated contact/support instruction.

Use a variable for a short text value such as a product name or version;
use a snippet for a larger formatted block.

### 7.2 Create a snippet

1.  In the content area, locate the appropriate snippets folder or
    create one according to the team convention.
2.  Create a new snippet file.
3.  Give it a descriptive name, such as `Security-Warning.flsnp`.
4.  Add the reusable content and apply the appropriate styles.
5.  Save the snippet.

Alternatively, some workflows allow you to select existing content and
convert it to a snippet. The exact command varies by Flare version.

### 7.3 Insert a snippet into a topic

1.  Open the destination topic.
2.  Place the cursor where the reusable content should appear.
3.  Use the snippet insertion command or drag the snippet into the
    topic, depending on the editor and version.
4.  Select the snippet.
5.  Save the topic.
6.  Preview the output to verify formatting and placement.

### 7.4 Edit a snippet

1.  Open the snippet file itself.
2.  Edit the shared content.
3.  Save the snippet.
4.  Preview affected topics or build the target.

Because topics reference the snippet, changes can affect every topic
that uses it. Before changing a shared warning or policy statement,
identify its usages and confirm the change is correct for all of them.

### 7.5 Snippet best practices

-   Keep each snippet focused on one reusable purpose.
-   Use descriptive filenames.
-   Do not turn every sentence into a snippet.
-   Avoid snippets that only make sense in one context unless their name
    and usage make that clear.
-   Be cautious with nested snippets because they can make content
    dependencies harder to trace.
-   Review all usages after changing shared content.
-   Use snippet conditions if a reusable block needs controlled
    variation, where supported.

## 8. Create and use variables

### 8.1 When to use variables

A variable is a reusable short text value or generated value maintained
in one place.

Examples:

-   Product name.
-   Company name.
-   Version number.
-   Release date.
-   Documentation URL.
-   Support email address.

Variables are particularly useful when a value changes across releases
or differs between product editions.

### 8.2 Create a variable

1.  Locate the Variables or variable-set area in the project.
2.  Open an existing variable set or create a new one.
3.  Add a variable with a clear name, such as `ProductName`.
4.  Enter its displayed value, such as `Example Identity Platform`.
5.  Save the variable set.

A variable set is commonly stored in a `.flvar` file. The precise
dialogs depend on the version.

### 8.3 Insert a variable

1.  Open the topic or snippet.
2.  Place the cursor where the value should appear.
3.  Use the Insert Variable command.
4.  Choose the relevant variable set and variable.
5.  Save and preview the topic.

Conceptually, the source refers to a variable while the generated output
displays its defined value.

### 8.4 Update and override variables

If the product name changes, update the central variable definition
rather than editing every topic manually. If different targets require
different values, use target-specific variable overrides when supported
and appropriate.

For example:

  Target               ProductName value
  -------------------- -----------------------------
  Standard edition     Example Platform
  Enterprise edition   Example Platform Enterprise

### 8.5 Variable best practices

-   Use variables for short, reusable values---not entire procedures.
-   Agree on a naming convention.
-   Avoid creating duplicate variables for the same concept.
-   Review target overrides during release updates.
-   Build all affected targets after changing a high-use variable.
-   Check grammar around variables. A variable replacement should read
    naturally in every sentence where it is used.

## 9. Images and other assets

### 9.1 Organize images

Create or use a central images folder, for example
`Content/Resources/Images/`. Use descriptive filenames such as
`user-management-page.png` rather than `image001.png`.

Recommended practices:

-   Use consistent image naming.
-   Keep original source screenshots where your team's process requires
    them.
-   Use PNG for most interface screenshots and suitable formats for
    diagrams or photographs.
-   Crop unnecessary areas and remove sensitive information.
-   Add meaningful alternative text where supported and appropriate.
-   Use readable image dimensions and avoid screenshots with tiny text.
-   Confirm licensing and confidentiality before importing external
    images.

### 9.2 Insert an image into a topic

1.  Capture or obtain the approved image.
2.  Save it into the project's images folder.
3.  Open the destination topic.
4.  Use the image insertion command or drag the image from the project
    explorer.
5.  Set alternative text, size, alignment, and any supported display
    options.
6.  Preview HTML5 and print outputs to ensure the image is legible.

### 9.3 Import approximately 100 images in bulk

Do not insert 100 images into a topic one at a time if the objective is
only to bring the files into the project. Import or copy them into the
project's image folder in bulk, then insert references to individual
images where required.

A safe workflow:

1.  Gather the images in a staging folder outside the active project.
2.  Remove duplicates and unrelated files.
3.  Rename files using a consistent convention.
4.  Check image formats, file sizes, and confidential content.
5.  Back up or commit the current project.
6.  Use Flare's import/add-files workflow if available, or copy the
    files into the intended project folder while following your team's
    source-control process.
7.  Refresh/reopen the project if necessary so the files appear in the
    project explorer.
8.  Insert the images into topics or snippets as needed.
9.  Check links and run a build to find missing assets.

**Important:** Copying files into a folder does not automatically place
them in the correct topics. Image files must be referenced from content,
and those references must resolve correctly in the output. Avoid
renaming imported images after they have been linked unless you update
and validate every reference.

### 9.4 Image migration checklist

-   [ ] Images are in the correct project folder.
-   [ ] Filenames are unique and meaningful.
-   [ ] No confidential data appears in screenshots.
-   [ ] Image references work in topics.
-   [ ] Alternative text is provided where needed.
-   [ ] Images are legible in HTML5 and PDF.
-   [ ] The project builds without missing-file errors.

## 10. Bulk import from Word and other sources

Flare provides import workflows for sources such as Microsoft Word and
other supported documentation formats. Available importers and options
depend on the installed version and source format.

### 10.1 Prepare a Word document before import

1.  Make a backup of the original Word file.
2.  Use Word heading styles consistently (Heading 1, Heading 2, etc.).
3.  Apply list styles to lists rather than typing bullet symbols
    manually.
4.  Use real tables instead of images of tables where possible.
5.  Add meaningful captions and alternative text to images when
    possible.
6.  Remove obsolete content, tracked changes, comments, and duplicate
    sections.
7.  Check hyperlinks and references.
8.  Decide whether the entire document should become one topic or
    whether headings should be split into separate topics.

Clean source formatting generally leads to a cleaner import.

### 10.2 Import a Word document

1.  Open the Flare project.
2.  Use the import workflow and select Microsoft Word or the appropriate
    source type.
3.  Browse to the source file.
4.  Choose the import options, including how headings map to topics and
    how styles are handled.
5.  Select the destination folder and any TOC-related options offered by
    the importer.
6.  Review the import preview/options carefully.
7.  Run the import.
8.  Open several imported topics and check headings, tables, lists,
    images, links, and formatting.
9.  Repair the content and build a test output.

Do not assume that a successful import means the result is
publication-ready. Imported formatting often needs cleanup and alignment
with the project stylesheet.

### 10.3 Import many Word files

If you have many Word files:

1.  Inventory the documents and group them by guide, audience, and
    subject.
2.  Decide the desired topic granularity and folder structure.
3.  Standardize the Word styles where practical.
4.  Use the importer's batch or multi-file options if available in your
    version.
5.  If batch import is not available for the exact source type, import
    files in manageable groups.
6.  Maintain a mapping list from original filenames to resulting Flare
    topics.
7.  Check whether a TOC was created and whether its order is correct.
8.  Compare imported topic counts and key headings against the source
    inventory.
9.  Run broken-link, image, and build checks.

### 10.4 Easy Sync and ongoing imports

Some Flare workflows support synchronizing imported source documents
with later changes. This can be useful when a Word file remains the
authoritative source, but it also requires a clear ownership decision.
Do not create a workflow where both the Word file and the Flare topics
are edited independently without a defined source of truth.

Before enabling ongoing synchronization, test how it handles edits made
directly in Flare, removed sections, images, and formatting. Maintain
backups and a review process.

### 10.5 Import decision checklist

Choose the import approach based on these questions:

-   Is the source still being edited in Word?
-   Is Flare becoming the authoritative source?
-   Do you need ongoing synchronization or a one-time migration?
-   Must headings become separate topics?
-   Are the source styles consistent?
-   Are images embedded in Word or stored as separate files?
-   Do you need to preserve a TOC or rebuild it?
-   How will you validate completeness after import?

## 11. Styles, stylesheets, and page layouts

### 11.1 Why styles matter

Stylesheets control the visual presentation of content. They help the
team maintain consistent headings, body text, notes, tables, links, and
lists across topics and outputs.

Use semantic styles such as Heading 1 and Heading 2. Avoid formatting
each heading manually with a different font size or color.

### 11.2 Apply a stylesheet

1.  Open the relevant topic or project settings.
2.  Check which stylesheet is associated with the topic or target.
3.  Apply the appropriate paragraph or character style.
4.  Preview the result in the target output.
5.  Update the stylesheet centrally if the same visual correction is
    needed across the project.

### 11.3 Common stylesheet areas

-   Body text and headings.
-   Ordered and unordered lists.
-   Tables and table headers.
-   Notes, warnings, and tips.
-   Hyperlinks and cross-references.
-   Images and captions.
-   Responsive media queries for different screen sizes.

### 11.4 PDF page layouts

Print output may require page layouts for page size, margins, headers,
footers, title pages, and other page elements. Configure the page layout
and print-specific settings, then review page breaks, widows/orphans,
tables, and image scaling in the generated PDF.

A stylesheet controls content styling; a page layout controls print-page
structure. They serve related but different purposes.

## 12. Conditions and single-sourcing

### 12.1 What conditions do

Condition tags allow you to include or exclude content for a particular
output or audience. They are useful when different products, deployment
models, roles, or editions share much of the same documentation.

Example condition tags:

-   `Cloud`
-   `OnPrem`
-   `Admin`
-   `EndUser`
-   `Enterprise`

Use a controlled set of condition tags and document their purpose.

### 12.2 Apply conditions

1.  Create or open the condition tag set.
2.  Define the condition tags used by the team.
3.  Select the content to condition.
4.  Apply the relevant condition tag.
5.  Open the target settings.
6.  Configure the target's conditional expression to include or exclude
    the intended content.
7.  Build the target and verify both included and excluded content.

Condition syntax and settings vary by version. Use the expression
builder or current Flare help rather than guessing the syntax.

### 12.3 Conditions versus variables versus snippets

  -----------------------------------------------------------------------
  Need                                Preferred mechanism
  ----------------------------------- -----------------------------------
  A product name or version number    Variable
  changes                             

  A reusable paragraph or warning     Snippet
  appears in many topics              

  A section should appear only in     Condition tag
  cloud documentation                 

  A section belongs in a different    TOC
  order or navigation hierarchy       

  The same topic needs different      Output-specific stylesheet/target
  presentation in HTML5 and PDF       settings, where appropriate
  -----------------------------------------------------------------------

Avoid excessive conditions. If a topic becomes full of complex
conditional blocks, separate topics or distinct targets may be easier to
maintain.

## 13. Links, cross-references, and navigation

### 13.1 Hyperlinks and cross-references

Use internal cross-references for links to topics or bookmarks inside
the project where appropriate. Use hyperlinks for external websites or
resources. Cross-references may be formatted differently in online and
print output, which makes them useful for multi-format documentation.

### 13.2 Link quality checks

-   Ensure the target exists.
-   Use descriptive link text such as "Configure single sign-on," not
    "click here."
-   Check external links before publishing.
-   Check that links work in each output.
-   Update links after topic renames or moves.
-   Use link analysis tools to find references before deleting content.

## 14. Structured authoring and content architecture

### 14.1 What structured authoring means

Structured authoring means organizing content according to defined
patterns and rules rather than treating a document as a free-form page.
Flare supports topic-based authoring and reusable structures; teams can
also establish templates and conventions for consistent content.

A topic-based approach separates a large guide into smaller,
independently maintainable topics and assembles them through TOCs and
targets.

### 14.2 Choose topic types based on user intent

Common patterns include:

-   **Concept:** Explain what something is and when to use it.
-   **Task/procedure:** Tell users how to complete a goal.
-   **Reference:** Describe fields, parameters, settings, status codes,
    or supported values.
-   **Troubleshooting:** Describe a symptom, likely causes, and
    resolution steps.
-   **Release note:** Summarize changes, limitations, and upgrade
    considerations.

A consistent topic template may include purpose, prerequisites, steps,
result, and related information. Use only the sections that help the
reader.

### 14.3 Separate content from presentation

-   Keep the topic focused on meaning and user tasks.
-   Use stylesheet rules for presentation.
-   Use snippets for reusable blocks.
-   Use variables for reusable short values.
-   Use conditions for controlled inclusion/exclusion.
-   Use TOCs to define navigation and print order.
-   Use targets for output-specific configuration.

This separation reduces duplicated content and makes updates safer.

### 14.4 Content modeling for advanced teams

Before building a large documentation set, define:

1.  Audiences and personas.
2.  User journeys and tasks.
3.  Topic types and templates.
4.  Naming and metadata conventions.
5.  Reuse rules and ownership.
6.  Versioning and product-variant strategy.
7.  Review and approval workflow.
8.  Publication destinations and maintenance responsibilities.

Use metadata and naming consistently so writers can locate content,
identify owners, and assess change impact.

## 15. Git: local repository, branches, commits, and pull requests

Git is a distributed version control system. GitHub hosts repositories
and provides pull requests for review and merging. Flare has
source-control integration in supported configurations; teams may use
Flare's integration or Git command-line tools. Coordinate with your team
before using both approaches on the same project.

### 15.1 Before connecting a Flare project to Git

-   Confirm whether the repository already exists.
-   Agree on the default branch, often `main`.
-   Confirm which files should be tracked and whether output folders
    should be excluded.
-   Make a backup.
-   Ensure team members know how to pull, commit, and resolve conflicts.
-   Avoid having two writers edit the same files concurrently without
    coordination.

### 15.2 Create a local repository for an existing project

If your project is not yet under version control, open Git Bash or a
terminal and navigate to the project folder:

``` bash
cd /path/to/ProductDocs
git init
git status
git add .
git commit -m "Initial commit of Flare project"
```

Before running `git add .`, inspect the project and establish an
appropriate `.gitignore` file. Do not commit generated output, temporary
files, credentials, or sensitive information unless the repository
policy explicitly requires them.

### 15.3 Connect the local repository to GitHub

Create an empty repository on GitHub, then add it as a remote:

``` bash
git branch -M main
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git push -u origin main
```

Replace the example URL with your repository URL. Follow your
organization's authentication policy; GitHub may require browser
authentication, a credential manager, or a token rather than an account
password.

If the GitHub repository already contains commits or files, do not
blindly push over it. First understand its history and follow the
correct clone/pull workflow.

### 15.4 Clone an existing repository

For an existing GitHub repository, the usual approach is to clone it:

``` bash
git clone https://github.com/USERNAME/REPOSITORY.git
cd REPOSITORY
git status
```

Open the project from the cloned local folder in Flare. Avoid making a
second unrelated repository inside the project folder.

### 15.5 Create a branch

``` bash
git switch -c feature/update-installation-guide
```

Use a descriptive branch name. Examples:

-   `docs/add-sso-guide`
-   `docs/update-api-reference`
-   `docs/fix-installation-steps`

### 15.6 Make and commit changes

1.  Open the project in Flare.
2.  Edit topics, snippets, variables, TOCs, or other files.
3.  Save the changes.
4.  Inspect the changed files:

``` bash
git status
git diff
```

5.  Stage the intended files:

``` bash
git add Content/Tasks/Configure-SSO.htm
```

6.  Commit:

``` bash
git commit -m "Update SSO configuration steps"
```

A good commit message says what changed and avoids vague messages such
as `updates` or `final changes`.

### 15.7 Push the branch

``` bash
git push -u origin feature/update-installation-guide
```

After the first upstream setup, later pushes usually need only:

``` bash
git push
```

### 15.8 Create a pull request

1.  Open the repository on GitHub.
2.  Choose the option to compare branches or create a pull request.
3.  Set the **base** branch to `main` (or your team's integration
    branch).
4.  Set the **compare/head** branch to your feature branch.
5.  Write a summary of the change and its purpose.
6.  Include testing performed, such as HTML5/PDF build checks.
7.  Add reviewers if required.
8.  Create the pull request.

### 15.9 Update an existing pull request

If reviewers request changes:

1.  Keep working on the same feature branch.
2.  Edit the Flare source files.
3.  Preview/build the output.
4.  Stage and commit the changes.
5.  Push the same branch.

``` bash
git add .
git commit -m "Address review comments on SSO guide"
git push
```

The existing pull request updates automatically when you push new
commits to its branch.

### 15.10 Bring the branch up to date with main

Follow your team's preferred merge or rebase policy. A straightforward
merge workflow is:

``` bash
git switch main
git pull origin main
git switch feature/update-installation-guide
git merge main
```

Resolve any conflicts, test the project, commit the resolution if Git
requires it, and push the branch.

Rebase is another option, but do not rebase a shared branch without
understanding the team's policy. Avoid force-pushing shared work unless
the team explicitly permits it.

### 15.11 Resolve conflicts safely

A conflict occurs when Git cannot automatically reconcile changes to the
same part of a file.

1.  Run `git status` to identify conflicted files.
2.  Open each file and inspect both versions.
3.  Keep the correct combined content; do not simply accept one side
    without review.
4.  Remove conflict markers if editing manually.
5.  Open the affected topic in Flare and check that the markup remains
    valid.
6.  Build the target.
7.  Stage the resolved files and commit the resolution.
8.  Push the branch and recheck the PR.

Flare source files may contain XML/XHTML markup. A textually resolved
conflict can still produce malformed content, so a build and rendered
review are essential.

### 15.12 Merge the pull request

After required approvals and checks pass:

1.  Review the final diff.
2.  Confirm the right base and compare branches.
3.  Confirm automated checks/builds have passed if configured.
4.  Select the merge option permitted by the repository.
5.  Confirm the merge.
6.  Delete the feature branch if your workflow allows it.
7.  Update your local `main`:

``` bash
git switch main
git pull origin main
```

If the repository requires squash merging or rebasing, follow that
policy instead of choosing a merge method independently.

### 15.13 Git practices for Flare teams

-   Commit source files, not unnecessary generated output.
-   Do not commit passwords, API keys, access tokens, or confidential
    user data.
-   Pull updates before starting work.
-   Use small, focused commits.
-   Avoid editing the same topic as another writer at the same time.
-   Treat binary assets and project configuration carefully.
-   Build the output after merging changes.
-   Keep a clear release/tagging policy for published documentation.

## 16. Build and publish HTML5, PDF, and other outputs

### 16.1 Understand targets

A target defines how a particular output is generated. Different targets
can use different TOCs, skins, conditions, variable overrides,
stylesheets, and publishing settings.

Common outputs include responsive HTML5, PDF, Word, and other formats
supported by the installed Flare version and license.

### 16.2 Create an HTML5 target

1.  Open the Targets area in the Project Organizer.
2.  Create a new target.
3.  Select HTML5 as the output type.
4.  Set a descriptive target name, such as `Product-Help-HTML5`.
5.  Select the correct TOC.
6.  Configure the skin/navigation settings.
7.  Set condition expressions and variable overrides if needed.
8.  Review search, branding, output folder, and other target settings.
9.  Save the target.
10. Build the target.
11. Open the generated output locally and test navigation, search,
    images, links, and responsive behavior.

The exact target editor options depend on the Flare release and selected
output type.

### 16.3 Create a PDF target

1.  Create a target and select PDF or the applicable print-based output
    type.
2.  Select the appropriate TOC/outline.
3.  Configure page layout, page size, margins, headers, footers, and
    numbering.
4.  Set print stylesheet and other print-specific options.
5.  Configure the printed TOC if required.
6.  Build the target.
7.  Review the PDF page by page.

Check for:

-   Incorrect page breaks.
-   Empty pages.
-   Clipped tables or images.
-   Inconsistent heading numbering.
-   Missing cross-reference text or page numbers.
-   Header/footer errors.
-   Unreadable code or API tables.
-   Font and symbol problems.

### 16.4 Build versus publish

**Build** generates the output files. **Publish** transfers or deploys
the output to a destination, if a publishing destination is configured.

For example, building HTML5 locally does not automatically make it
publicly available on the internet.

### 16.5 Deploy HTML5 output

Common deployment approaches include:

-   Uploading the generated output to a web server.
-   Deploying it through a controlled release pipeline.
-   Publishing to a documentation hosting platform.
-   Using an approved company portal or content delivery system.

Typical process:

1.  Build and validate the HTML5 target.
2.  Identify the approved deployment destination.
3.  Confirm the output path and access permissions.
4.  Upload or deploy the generated files using the organization's
    approved process.
5.  Test the live URL, navigation, search, and links.
6.  Confirm the published version matches the approved source revision.
7.  Record the release or deployment details.

Do not publish internal or confidential documentation to a public
destination.

### 16.6 Deploy or distribute PDF output

1.  Build the PDF target.
2.  Review the generated PDF.
3.  Confirm the filename, version, date, and metadata.
4.  Publish it to the approved document repository, portal, or release
    package.
5.  Verify that users can access and download the correct file.

### 16.7 Other formats

If the installed Flare version supports the required format, create a
separate target and configure its output-specific settings. Availability
depends on the format, version, license, and any required integrations.
Do not assume that all features behave identically in HTML5, PDF, Word,
or other formats.

### 16.8 Output validation checklist

-   [ ] Correct target and TOC selected.
-   [ ] Correct version/product variables displayed.
-   [ ] Conditions include the right content.
-   [ ] No broken links or missing images.
-   [ ] Navigation and search work in HTML5.
-   [ ] Tables, code samples, and images render correctly.
-   [ ] PDF page layout, numbering, headers, and footers are correct.
-   [ ] Accessibility and alternative text have been checked.
-   [ ] Output contains no draft, obsolete, or confidential content.
-   [ ] Build warnings and errors have been reviewed.
-   [ ] The final output has been tested at its actual destination.

## 17. CMS and team content management

### 17.1 What is a CMS?

A content management system (CMS) helps teams manage content,
permissions, workflow, versions, and publication. A component content
management system (CCMS) is especially focused on storing and reusing
small content components across multiple deliverables.

Git and a CMS are not the same thing. Git tracks source changes and
history. A CMS/CCMS may additionally provide content lifecycle
workflows, structured reuse, permissions, assignments, and review or
approval processes.

### 17.2 Flare Desktop, Flare Online, and enterprise CCMS

-   **Flare Desktop:** A desktop authoring and publishing environment
    for project-based documentation.
-   **Flare Online:** A cloud-based companion for supported
    browser-based authoring, review, collaboration, and project
    workflows.
-   **Enterprise CCMS:** A larger content management environment, such
    as an integrated component content management solution, designed for
    broader reuse and governance across teams and products.

The right solution depends on the organization's scale, governance
needs, collaboration model, and budget. Check current product
documentation and licensing before choosing a workflow.

### 17.3 Typical team workflow

1.  A product owner or engineer supplies requirements and implementation
    details.
2.  The technical writer creates or updates topics in the approved
    project.
3.  Shared content is maintained through snippets and variables.
4.  Conditions and targets produce audience-specific documentation.
5.  Git or the content platform records revisions.
6.  SMEs review technical accuracy.
7.  Editors or peer reviewers check clarity, style, and consistency.
8.  The writer resolves comments and rebuilds the output.
9.  An authorized owner approves and publishes the documentation.
10. Feedback and analytics inform future updates.

### 17.4 Governance practices

-   Define ownership for topics and reusable components.
-   Establish naming, style, metadata, and folder standards.
-   Control who can edit, approve, and publish.
-   Use a review process for security, legal, and product claims where
    required.
-   Maintain release and version history.
-   Avoid duplicate sources of truth.
-   Define how archived, obsolete, and translated content is managed.
-   Document the process for emergency corrections and rollback.

## 18. Review, quality checks, and troubleshooting

### 18.1 Technical accuracy review

Validate the content against implementation, acceptance criteria, UI
behavior, API specifications, test cases, and SME confirmation. Do not
invent details to fill gaps. Track unresolved questions and escalate
high-risk ambiguities.

### 18.2 Editorial review

Check:

-   Plain language and active voice.
-   Consistent terminology.
-   Logical heading hierarchy.
-   Task-oriented titles.
-   Correct punctuation and grammar.
-   Numbered steps for sequential actions.
-   Parallel wording in lists.
-   Appropriate warnings and prerequisites.
-   Descriptive links.
-   Consistency between screenshots and current UI.

### 18.3 Common issues

  -----------------------------------------------------------------------
  Problem                             What to check
  ----------------------------------- -----------------------------------
  Topic missing from output           Is it included through the selected
                                      TOC or target settings?

  Image does not appear               Is the file in the project and is
                                      its reference valid?

  Snippet change affects many topics  Identify all snippet usages and
                                      validate each context.

  Variable displays unexpected text   Check the variable set and
                                      target-specific overrides.

  Content appears in the wrong output Check condition tags and target
                                      expressions.

  TOC navigation is incorrect         Check the selected TOC, linked
                                      files, labels, and hierarchy.

  PDF formatting is poor              Check page layouts, print styles,
                                      table widths, and page breaks.

  Git reports a conflict              Inspect both changes, resolve
                                      markup carefully, then build.

  Build fails                         Review the build log and fix broken
                                      references, invalid markup, or
                                      configuration issues.

  Output differs by format            Review target-specific styles,
                                      conditions, and supported features.
  -----------------------------------------------------------------------

### 18.4 Final pre-publication checklist

-   [ ] All required topics are present.
-   [ ] SME questions are resolved or explicitly tracked.
-   [ ] UI and API details are verified.
-   [ ] TOC structure is logical.
-   [ ] Snippets and variables are correct.
-   [ ] Conditions are correct for each target.
-   [ ] Images and links work.
-   [ ] Spelling, grammar, and terminology are consistent.
-   [ ] HTML5 and PDF outputs have been reviewed where required.
-   [ ] Review comments are resolved.
-   [ ] Git changes are committed and merged according to policy.
-   [ ] The correct output is published to the correct destination.

## 19. Recommended end-to-end workflow

For a typical feature documentation update:

1.  Review the user story, requirements, acceptance criteria, design,
    and SME notes.
2.  Explore the feature in the UI or test environment.
3.  Identify documentation impact and unresolved questions.
4.  Create a branch or follow the team's content workflow.
5.  Update or create topics using the approved templates.
6.  Reuse existing snippets and variables where appropriate.
7.  Add or update images and cross-references.
8.  Update the TOC and target configuration if necessary.
9.  Apply conditions for product or audience variants.
10. Build HTML5 and/or PDF.
11. Validate the output and review links, images, navigation, and
    formatting.
12. Request SME and peer review.
13. Address feedback and rebuild.
14. Commit and push changes; open or update the pull request.
15. Resolve conflicts and obtain required approvals.
16. Merge through the approved process.
17. Build from the approved source and publish to the correct
    destination.
18. Verify the live output and record the release.

## 20. Beginner-to-pro learning plan

### Beginner: Learn the project and basic authoring

Practice: - Create a project. - Create, edit, and save topics. - Apply
headings and lists. - Create a TOC. - Insert images and links. - Build a
basic HTML5 target.

You are ready to progress when you can create a short guide and verify
the generated output without assistance.

### Intermediate: Reuse and multi-format publishing

Practice: - Create and insert snippets. - Create and insert variables. -
Maintain stylesheets. - Configure conditions. - Create HTML5 and PDF
targets. - Import a Word document and clean up the result. -
Troubleshoot broken links and images.

You are ready to progress when you can maintain a guide without
duplicating common content and can publish consistent online and print
outputs.

### Advanced: Source control and content architecture

Practice: - Create a Git branch and commit focused changes. - Push a
branch and open a pull request. - Review diffs and resolve conflicts. -
Model content by audience and task. - Use conditions and target
overrides carefully. - Audit links and snippet usage. - Establish
templates, metadata, and naming conventions. - Create a repeatable
publication checklist.

You are ready to progress when you can safely collaborate on a shared
project and explain how each source component affects generated outputs.

### Pro: Team governance and scalable delivery

Practice: - Design reusable content architecture. - Establish review and
approval workflows. - Coordinate Git and publishing permissions. -
Define release/versioning and rollback procedures. - Evaluate Flare
Online or a CCMS where the team's needs justify it. - Automate
appropriate build checks through approved scripts or CI/CD. - Use
feedback and documentation analytics to improve content. - Establish
localization and accessibility quality controls.

At this level, the goal is not just to operate Flare but to design a
sustainable documentation process for the whole team.

## 21. Official learning resources

Use the official help for the exact Flare version installed in your
environment:

-   [MadCap Flare Desktop
    Help](https://help.madcapsoftware.com/flare2026/Content/Home.htm)
-   [Authoring key
    features](https://help.madcapsoftware.com/flare2026/Content/Flare/Key-Concepts-Features/Authoring-Key-Features.htm)
-   [MadCap Flare product
    overview](https://www.madcapsoftware.com/products/flare/)
-   [MadCap Flare Online
    documentation](https://documentation.madcapsoftware.com/flare-online/)
-   [Git documentation](https://git-scm.com/doc)
-   [GitHub pull request
    documentation](https://docs.github.com/en/pull-requests)

**Final reminder:** Flare's menus and feature availability can change by
version and license. Use this guide as a practical workflow reference,
then confirm version-specific steps in the official help and your
organization's documentation standards.
