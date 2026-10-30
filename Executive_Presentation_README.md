# Executive Presentation Builder

A reusable, company-specific executive interview presentation system. Provide **only a job description and resume**. The system identifies the employer, researches its business, matches the candidate's documented experience to the role, and generates a polished interactive HTML presentation and an editable PowerPoint.

**This repository is a permanent workflow, not a one-time deck.** The same instructions, design standards, research process, and quality checks must apply to every new employer without requiring repeated prompts.

## Required inputs

Place these two files in `input/`:

- `job-description.*` — the full position description (PDF, DOCX, TXT, or Markdown)
- `resume.*` — the current resume (PDF, DOCX, TXT, or Markdown)

The user should not need to provide a company overview, brand colors, slide outline, research instructions, or design guidance. Derive the employer and role from the job description. If multiple employer names appear, use the hiring company rather than a recruiter, customer, or parent unless the position description establishes otherwise. If the employer genuinely cannot be identified, report the limitation instead of guessing.

## Mandatory company-specific branding

**Every presentation MUST use the actual target company's colors.** The company is the employer identified in the supplied job description, or the company explicitly provided by the user.

1. Research the employer's official website, publicly accessible brand guidelines, media/press kit, and other authoritative materials.
2. Identify its primary and secondary brand colors and their intended uses. Record the verified hex values, source URLs, and access dates in the company-specific `DESIGN.md`.
3. Apply those colors consistently to slide backgrounds, accents, headings, navigation, charts, cards, timelines, and the editable PowerPoint. Maintain readable contrast and accessibility.
4. Use an official logo only when an authorized, accessible asset is available; preserve its proportions and do not invent or alter it.
5. If no authoritative color specifications are available, derive a clearly labeled approximate palette from the company's public visual identity. Do **not** present approximations as official colors.
6. **Do not reuse RWE NewCo colors, logos, or content for another employer.** The RWE reference establishes the presentation's design quality, structure, and interactions, not the next company's brand.

## Reference materials

- Original example: `references/RWE_NewCo 30-60-90.html` (add this file to the repository)
- Pitch-deck narrative reference: https://github.com/rohitg00/awesome-claude-design/blob/main/recipes/pitch-deck-from-readme.md
- Brand-research reference: https://github.com/rohitg00/awesome-claude-design/blob/main/recipes/brand-extraction.md

These links are reference recipes, **not** dependencies on the paid Claude Design product. Do not require paid design services, premium templates, paid image-generation APIs, or additional paid subscriptions. Use free and appropriately licensed local tooling. Existing Claude Code usage limits still apply.

## Automatic workflow

### 1. Parse inputs

Read both documents completely. Extract the company, role, responsibilities, strategic priorities, requirements, and the candidate's relevant accomplishments. Never fabricate employment history, responsibilities, metrics, qualifications, or dates.

### 2. Research the company

Use accessible public sources to investigate its business model, products, leadership, ownership, relevant financial or operating priorities, recent news, competitive context, and plausible organizational/people implications. Prioritize official company materials and reliable recent reporting. Save source links and dates. Distinguish **verified facts**, **reasonable interpretations**, and **unknowns**. If internet research is unavailable, disclose that limitation and do not claim current verification.

### 3. Align the candidate to the job

Select achievements directly supported by the resume. Explain why they matter for this specific employer and role. Write in credible, natural executive language. Avoid generic HR claims, inflated ownership, invented numbers, and unsupported promises.

### 4. Build the executive story

Create approximately 8–12 slides, adapting the sequence to the position:

1. About Me / executive introduction
2. Understanding the Company and Role
3. Why My Experience Aligns
4. Business and People Priorities
5. Leadership Approach
6. Relevant Results and Proof
7. First 30 Days
8. Days 31–60
9. Days 61–90
10. Strategic Outcomes and Measures of Success
11. Executive Commitment / Closing

Combine or add slides when warranted by the evidence. The 30/60/90-day plan should name practical actions, stakeholders, deliverables, and success indicators. Do not imply that unverified problems exist or that speculative targets are guaranteed.

### 5. Apply the correct design

Analyze the RWE HTML reference for its full-screen layout, hierarchy, metric cards, transitions, timeline treatments, navigation, and responsive behavior. Preserve its polished executive presentation style while **replacing its branding with the researched target company's brand palette**. Create and save a company-specific `DESIGN.md`. Ensure HTML and PowerPoint use the same approved content and colors.

### 6. Generate deliverables

Produce both:

- **Interactive HTML:** standalone or clearly packaged with all required local assets, full-screen slides, working previous/next and keyboard navigation, progress indicators, responsive layouts, and functioning transitions.
- **Editable PPTX:** editable text, shapes, tables, and diagrams wherever feasible; visually aligned with the HTML deck. Do not substitute screenshots of whole slides for editable slide content.

Use free tools such as HTML/CSS/JavaScript, PptxGenJS, and Playwright. Avoid additional paid APIs and commercially restricted packages.

### 7. Test and repair

Run the available build and automated tests. Open and inspect the HTML in a browser, navigate through every slide, check desktop and mobile layouts, and detect missing assets, clipped text, overlaps, and broken controls. Generate and inspect rendered PPTX slides with locally available tools; verify slide count, content, and editability where possible. Cross-check all factual claims and metrics against the saved sources and resume. Fix detected problems before marking the deliverables complete. Explicitly disclose any checks that could not run.

## Proposed repository structure

```text
.
├── README.md
├── CLAUDE.md                  # Persistent Claude Code project rules
├── DESIGN.md                  # Shared design and interaction standards
├── package.json
├── input/
│   ├── job-description.*
│   └── resume.*
├── references/
│   └── RWE_NewCo 30-60-90.html
├── templates/
├── scripts/
├── tests/
└── companies/
    └── company-name/
        ├── research.md
        ├── sources.md
        ├── DESIGN.md          # Verified company-specific colors and brand rules
        ├── content.md
        ├── presentation.html
        ├── presentation.pptx
        └── qa-report.md
```

This structure describes the intended implementation; files other than this README are not assumed to exist until created and verified.

## One-command usage

**After the generator has been implemented and tested**, the intended workflow is:

1. Put the current job description and resume in `input/`.
2. Open the repository in Claude Code.
3. Say **“Build my presentation.”**

Claude Code must read `CLAUDE.md` and this README, perform the company research, and orchestrate the build and QA. Implement `npm run build-deck` for repeatable local generation and testing after the research inputs have been prepared. Do not claim that a plain npm script can independently perform AI-powered web research without an actual research integration.

Save each employer's files in a separate directory. Never overwrite a prior presentation. Preserve reusable standards and verified progress in the repository so new Claude Code sessions can resume without starting from scratch.

## Definition of done

A presentation is complete only when:

- Both input documents have been fully processed.
- The correct employer and role have been identified.
- Company research is sourced and limitations are disclosed.
- **The target company's verified brand colors have been applied to both HTML and PPTX**, or clearly labeled approximations are used when official values cannot be verified.
- Resume claims and metrics are supported by the resume.
- The interactive HTML has been functionally tested.
- The PowerPoint has been generated and inspected for content and editability.
- Both formats are saved under the correct employer.
- The QA report accurately identifies passed, failed, and unrun checks.

Do not stop at a plan, a slide outline, or a mockup. Implement, test, repair, and deliver the actual files.
