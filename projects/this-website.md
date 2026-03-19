A personal portfolio website built with React, TypeScript, Vite, and Tailwind CSS to showcase my work, background, and interests in a clean and interactive way. The site brings together project pages, work experience, education, documents, a GitHub chart, and personal sections into a single cohesive experience.

Rather than being a static portfolio, this project was designed as an actively evolving website that I could keep refining over time. It focuses on clear storytelling, polished UI details, responsive layouts, and a structure that makes it easy to expand with new content.

---

## Features

- Responsive portfolio homepage with a structured personal introduction
- Dedicated projects page with animated cards and tag filtering
- Individual project detail pages rendered from Markdown
- Work experience and education sections with custom card layouts
- Important documents section for resume and transcript access
- GitHub contribution chart integration
- "What Drives Me" and "Who Drives Me" sections for more personal context
- Light, dark, and system theme toggle
- Reusable components for navigation, cards, dropdowns, and content sections

---

## Project Structure

The website is divided into a few main parts:

1. A homepage that introduces me and highlights key sections such as TL;DR, experience, education, and current projects.
2. A projects listing page that fetches project metadata from a remote JSON source.
3. Dynamic project detail pages that load Markdown write-ups based on project id.
4. Shared UI components that keep the site visually consistent across pages.

This structure makes the portfolio easy to update without rewriting the whole site each time a new project is added.

---

## Technical Implementation

### Core Technologies

- React for the UI layer
- TypeScript for safer component and data modeling
- Vite for development and production builds
- Tailwind CSS for utility-first styling
- Framer Motion for animations and card transitions
- React Router for multi-page navigation
- React Markdown for rendering project write-ups

---

## Data Flow

The projects system is designed around remote content:

1. Project metadata is fetched from a hosted `projects.json` file.
2. The projects page extracts tags from that data and allows filtering.
3. Clicking a project opens a detail route like `/projects/[id]`.
4. The detail page fetches the corresponding Markdown file and combines it with the metadata.
5. The Markdown content is rendered into a styled project write-up.

This setup separates content from the frontend code, making the portfolio easier to maintain and extend.

---

## UI and Interaction Design

This project places a strong emphasis on small interface details:

- animated project cards with hover states
- tag-based filtering with an interactive dropdown
- section layouts tuned for readability and proportion
- reusable cards for work experience and education
- subtle transitions, hover effects, and theme-aware surfaces
- a header that stays visually consistent across home, projects, and project detail pages

These details help the site feel more intentional and polished than a basic resume website.

---

## Strengths of the Project

- Organizes both technical and personal information in a clear way
- Scales well as more projects and sections are added
- Uses reusable components rather than page-specific one-off code
- Separates project content into remote JSON and Markdown sources
- Includes both professional information and more personal storytelling
- Supports multiple theme modes for better user preference handling

---

## Current Limitations

- Some content is still manually maintained rather than powered by a full CMS
- Project metadata and Markdown depend on external hosted files being available
- There is no admin editing interface for adding or updating content
- The design system is still evolving through iterative refinement
- The site currently prioritizes presentation over analytics or advanced SEO features

---

## Future Improvements

- Add richer project media such as screenshots or embedded demos
- Improve SEO metadata and social sharing previews
- Add smoother page transitions between routes
- Introduce a more structured content pipeline for projects
- Expand accessibility testing and keyboard interaction polish
- Add a custom favicon and more refined branding details

---

## Libraries and Tools

- React
- TypeScript
- Vite
- Tailwind CSS
- Framer Motion
- React Router
- React Markdown

---

## Conclusion

This portfolio project is both a personal website and a design-and-engineering sandbox. It reflects how I think about frontend development: structure matters, presentation matters, and small interaction details can meaningfully improve the experience. More than just listing information, the site is built to communicate who I am, what I build, and how I approach my work.
