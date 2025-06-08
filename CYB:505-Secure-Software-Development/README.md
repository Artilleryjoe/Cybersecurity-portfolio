# Applying the SDLC to a Cybersecurity Lab Portfolio

## Course  
CYB/505 – Secure Software Development

## Objective  
This document applies the Software Development Life Cycle (SDLC) to the ongoing development and maintenance of a professional cybersecurity lab portfolio. The portfolio is treated as a living software product that evolves over time through structured, secure, and maintainable practices.

---

## Project Overview

**Project Name:** Cybersecurity Portfolio  
**System Type:** Documentation and source-code archive  
**Primary User:** The developer (self)  
**Secondary Users:** Instructors, hiring managers, peers, recruiters  

This project is managed like a secure documentation platform that must remain professional, usable, and auditable over time.

---

## SDLC Breakdown

### 1. Planning

- Define the scope: Represent each course in the cybersecurity program with its own structured folder and README.
- Identify stakeholders: You (as the student), instructors, potential employers, career coaches.
- Success criteria:
  - All relevant courses and labs are documented in a consistent format
  - Repository is clean, navigable, and readable
  - Labs are technically accurate and professionally written
  - No missing or placeholder content

---

### 2. Requirements Gathering

**Functional Requirements:**
- Markdown-based lab reports
- Organized folders per course
- Individual README for each course folder
- Git-based version control and change history

**Non-functional Requirements:**
- Plain-text compatibility and readability
- Cross-platform compatibility (GitHub web, desktop, mobile)
- No emojis or unprofessional language
- Structured format to support automated generation in the future

---

### 3. Design

 **File and folder structure:**
  Cybersecurity-portfolio/
  
├── CYB-500_Advanced_Cybersecurity_Concepts/

│ └── README.md

├── CYB-505_Secure_Software_Development/

│ └── README.md

└── README.md
- Standard Markdown template for labs:
- Title
- Course
- Objective
- Tools Used
- Procedure
- Results
- Lessons Learned

- Commit naming conventions:
- Use clear, descriptive messages (e.g., "Add XSS lab write-up", "Update Snort config notes")

---

### 4. Development

- Write labs in Markdown using the standardized template
- Commit each completed lab with a meaningful message
- Maintain folder consistency as new courses and labs are added
- Optionally use automation (e.g., shell script, snippet) to generate lab templates

---

### 5. Testing

- Manually review Markdown rendering via GitHub UI
- Confirm that internal links and file paths are valid
- Run basic formatting validation (e.g., Markdown linter)
- Cross-check lab outputs and descriptions for technical accuracy

---

### 6. Deployment

- Repository is hosted on GitHub under:
[https://github.com/Artilleryjoe/Cybersecurity-portfolio](https://github.com/Artilleryjoe/Cybersecurity-portfolio)
- Portfolio is accessible and shareable via direct link
- Future-ready for integration with static site generators or PDF export tools

---

### 7. Maintenance

- Add new courses and labs as completed
- Refactor older lab write-ups for consistency and clarity
- Track potential improvements or missing content in GitHub issues or a personal changelog
- Archive deprecated or duplicate content appropriately

---

## Future Enhancements

- Add a top-level index with auto-generated links to each course and lab
- Build a static HTML site from this content (e.g., using Jekyll or MkDocs)
- Explore adding GitHub Actions to automate formatting checks or README updates



