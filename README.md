# SAIT ITS Slides

This is a GitHub Pages site hosting educational slides for SAIT (Southern Alberta Institute of Technology) courses, powered by [reveal.js](https://revealjs.com/).

**Live Site:** https://sait-its.github.io/

## Overview

This repository contains slide presentations for various courses:
- **CPRG-217**: Scripting course covering Python, Linux/Windows scripting, network programming, and Ansible
- **CPSY-350**: Additional course materials

## Technology Stack

### Reveal.js Framework
- **Version**: 5.2.1
- **Description**: HTML-based presentation framework for creating beautiful, interactive slide decks
- **Features**:
  - Markdown support for easy content authoring
  - Syntax highlighting via highlight.js
  - Speaker notes
  - Responsive design
  - PDF export capability

### Key Dependencies
- **marked**: Markdown parser for converting `.md` files to slides
- **highlight.js**: Syntax highlighting for code blocks
- **Node.js**: Build tooling (requires Node.js >= 18.0.0)

## Project Structure

```
.
├── cprg-217/               # CPRG-217 course slides
│   ├── viewer.html         # Universal slide viewer (loads markdown dynamically)
│   ├── index.html          # Course navigation page
│   ├── cprg-217-extras.html # Extra topics navigation
│   ├── unit-XX-slides.md   # Markdown slide content for each unit
│   ├── py-*.md             # Python topic slides
│   └── *.assets/           # Images and assets for slides
├── cpsy-350/               # CPSY-350 course slides
├── dist/                   # Reveal.js distribution files
├── plugin/                 # Reveal.js plugins
└── assets/                 # Shared assets (favicons, logos)
```

## Adding New Slides

### For CPRG-217 Course

#### 1. Create Markdown Content
Create a new `.md` file in the `cprg-217/` directory:

```bash
cd cprg-217/
touch my-new-topic.md
```

#### 2. Write Slide Content
Use Reveal.js markdown syntax. Separate slides with `---`:

```markdown
### My New Topic
Introduction slide

---

### Slide 2
Content here

---

#### Code Example
```python
def hello():
    print("Hello, World!")
```
#### 3. Add Assets (Optional)
If you need images or other assets:
1. Create a directory: `my-new-topic.assets/`
2. Place your images there
3. Reference them in markdown: `![Description](./my-new-topic.assets/image.png)`

#### 4. Link to Your Slides
Add a link to your slides in the appropriate navigation page:

**For main units** - Edit `cprg-217/index.html`:
```html
<a href="./viewer.html?file=my-new-topic.md">My New Topic</a></br>
```

**For extra topics** - Edit `cprg-217/cprg-217-extras.html`:
```html
<a href="./viewer.html?file=my-new-topic.md">My New Topic</a></br>
```

#### 5. Test Locally
```bash
# Install dependencies (first time only)
npm install

# Start local server
npm start

# Visit http://localhost:8000/cprg-217/
```

### For Other Courses

Follow the same pattern as CPRG-217:
1. Create markdown files in the course directory
2. Use the `viewer.html` pattern or create course-specific HTML files
3. Update navigation pages

## Development

### Local Development Server
```bash
npm start
```
Starts a local server at `http://localhost:8000`

### Building
```bash
npm run build
```
Builds the reveal.js distribution files (usually not needed unless modifying reveal.js itself)

## Reveal.js Markdown Syntax Tips

- **Slide separator**: `---` (three dashes)
- **Vertical slides**: `----` (four dashes)
- **Speaker notes**: Use `Note:` followed by your notes
- **Fragments** (incremental reveals): Use `<!-- .element: class="fragment" -->`
- **Background colors**: Set via `data-background-color` in HTML section tag

For more details, see the [Reveal.js documentation](https://revealjs.com/).

## Deployment

This site is automatically deployed via GitHub Pages from the `main` branch. Any push to `main` will update the live site.

## License

MIT licensed | Copyright © 2024-2025

