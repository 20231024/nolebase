# Nólëbase - AI Agent Development Guide

## Project Overview

Nólëbase is a knowledge base system built with VitePress, designed to create a personal knowledge management website. The name comes from Quenya (Tolkien's Elvish language) "nólë" meaning "knowledge" and English "base", literally "knowledge base".

This project serves as both a personal knowledge repository and a demonstration of how to build sophisticated knowledge base websites using modern web technologies. It integrates with Obsidian for local knowledge management and VitePress for web deployment.

## Technology Stack

### Core Technologies
- **VitePress**: Static site generator based on Vite and Vue.js
- **Vue.js 3**: Progressive JavaScript framework for building user interfaces
- **TypeScript**: Primary development language for type safety
- **Node.js 23.x**: Runtime environment
- **pnpm**: Package manager (version 10.24.0)

### Styling & UI
- **UnoCSS**: Atomic CSS engine for styling
- **VitePress Default Theme**: Base theme with custom extensions
- **Custom Vue Components**: Enhanced layout components in `.vitepress/theme/components/`

### Markdown Processing
- **Markdown-it**: Extensible Markdown parser with multiple plugins:
  - `markdown-it-footnote`: Footnote support
  - `markdown-it-mathjax3`: Mathematical formula rendering
  - `@nolebase/markdown-it-bi-directional-links`: Obsidian-style bidirectional links
  - `@nolebase/markdown-it-unlazy-img`: Enhanced image processing

### Nólëbase Integrations
The project heavily utilizes the `@nolebase/integrations` package which provides:
- Enhanced readability features
- Git changelog integration
- Page properties and metadata
- Sidebar calculation
- Targeted heading highlighting
- Inline link previews
- Thumbnail hash generation
- Open Graph image generation

## Project Structure

```
E:\note\远程提交\nolebase/
├── .vitepress/                    # VitePress configuration
│   ├── config.ts                  # Main VitePress configuration
│   ├── head.ts                    # HTML head metadata
│   ├── theme/                     # Custom theme extensions
│   │   ├── components/            # Vue components
│   │   │   ├── AppContainer.vue
│   │   │   ├── DocFooter.vue
│   │   │   ├── HomePage.vue
│   │   │   └── Share.vue
│   │   ├── styles/                # Custom CSS
│   │   └── index.ts               # Theme configuration
├── .obsidian/                     # Obsidian configuration
├── metadata/                      # Site metadata and configuration
│   └── index.ts                   # Creators, links, site info
├── scripts/                       # Build and utility scripts
├── public/                        # Static assets
├── zh-CN/                         # Content (Chinese)
│   ├── 笔记/                      # Notes directory
│   ├── 编目 Catalog/              # Catalog directory (Books, Articles, Anime)
│   └── index.md                   # Homepage
└── netlify.toml                   # Netlify deployment configuration
```

## Build Process & Commands

### Development
```bash
# Install dependencies
pnpm install

# Start development server
pnpm dev
# or
pnpm docs:dev
```

### Production Build
```bash
# Build static site
pnpm build
# or
pnpm docs:build

# Preview production build
pnpm serve
# or
pnpm docs:serve
```

### Update Scripts
```bash
# Run update scripts
pnpm update
```

## Configuration Files

### Primary Configurations
- **`vite.config.ts`**: Vite configuration with Nólëbase integrations
- **`.vitepress/config.ts`**: VitePress configuration with theme and markdown settings
- **`tsconfig.json`**: TypeScript configuration
- **`eslint.config.js`**: ESLint configuration using Anthony Fu's preset
- **`uno.config.ts`**: UnoCSS configuration with custom shortcuts

### Package Management
- **`package.json`**: Dependencies and scripts
- **`pnpm-lock.yaml`**: Lock file for reproducible builds

## Content Organization

### Directory Structure
- **`zh-CN/`**: Chinese language content (primary language)
  - **`笔记/`**: Personal notes and knowledge entries
  - **`编目 Catalog/`**: Cataloged content organized by type:
    - `书籍/`: Book reviews and notes
    - `文章/`: Article summaries and references
    - `番剧/`: Anime reviews and information
    - `视频/`: Video content documentation

### Content Guidelines
The project follows structured documentation standards:
1. **Title**: Main heading using H1
2. **Author**: Document creator information
3. **Tags**: Frontmatter tags for categorization
4. **Archive Information**: For archived content with source attribution
5. **Document Compatibility**: Version information for technical docs
6. **Overview**: TL;DR for lengthy documents
7. **Table of Contents**: Navigation structure
8. **Main Content**: Well-structured with proper heading hierarchy
9. **Extended Reading/References**: External resources and citations
10. **Footnotes**: Additional explanations and references

## Deployment Process

### Automated Deployment
The project uses GitHub Actions for automated deployment:
- **Trigger**: Push to `main` branch or manual dispatch
- **Build Environment**: Ubuntu latest with Node.js 23.x
- **Package Manager**: pnpm with frozen lockfile
- **Deployment Target**: Netlify

### Deployment Steps
1. Code checkout with full history
2. pnpm and Node.js setup
3. Dependency installation
4. Font installation (Source Han Sans)
5. Static site build
6. Netlify CLI deployment

### Hosting Configuration
- **Primary Host**: Netlify
- **Domain**: `nolebase.ayaka.io`
- **Fallback**: GitHub Pages (configured but not primary)
- **CDN**: Global distribution via Netlify

## Development Conventions

### Code Style
- **ESLint**: Anthony Fu's configuration with UnoCSS support
- **TypeScript**: Strict mode enabled
- **Indentation**: 2 spaces
- **Line Endings**: LF
- **Charset**: UTF-8
- **Trailing Whitespace**: Trimmed

### Component Development
- Vue 3 Composition API preferred
- TypeScript for all components
- UnoCSS for styling
- Follow VitePress theme extension patterns

### Markdown Standards
- Frontmatter for metadata
- Proper heading hierarchy
- Obsidian-compatible bidirectional links
- Footnotes for references
- Math support via MathJax3

## Testing Strategy

### Current State
- No automated tests currently implemented
- Manual testing through development server
- Build verification in CI/CD pipeline

### Testing Recommendations
- Consider adding unit tests for utility functions
- Integration tests for build process
- Visual regression testing for UI components
- Link validation for markdown content

## Security Considerations

### Content Security
- All content is static (no server-side processing)
- No user authentication or data storage
- Public GitHub repository with open content

### Build Security
- Dependency pinning via pnpm-lock.yaml
- GitHub Actions with minimal permissions
- No secrets exposed in repository
- Netlify deployment via secure tokens

### External Dependencies
- All dependencies from npm registry
- Regular dependency updates recommended
- No custom or unverified packages

## Performance Optimizations

### Build Optimizations
- Vite-based fast development and building
- Automatic code splitting
- Asset optimization and compression
- Image processing with Sharp

### Runtime Optimizations
- Static site generation (SSG)
- Progressive enhancement
- Lazy loading for images
- Efficient CSS with UnoCSS

## Monitoring & Analytics

### Analytics Integration
- Plausible Analytics (privacy-focused)
- Proxied through Netlify to avoid ad-blockers
- Domain: `nolebase.ayaka.io`

### Performance Monitoring
- Netlify built-in performance monitoring
- GitHub Actions build time tracking
- No custom performance tracking currently

## Troubleshooting Common Issues

### Build Issues
- Ensure Node.js 23.x compatibility
- Check pnpm version matches lockfile
- Verify font files are present in public directory

### Development Issues
- Clear `.vitepress/cache/` if rendering issues
- Check for TypeScript errors
- Verify markdown syntax compatibility

### Deployment Issues
- Netlify token configuration
- Build timeout settings (currently 10 minutes)
- Domain and DNS configuration

## Extension Points

### Adding New Content Types
1. Create new directory under `zh-CN/编目 Catalog/`
2. Update sidebar configuration in `.vitepress/config.ts`
3. Add appropriate icons and styling

### Custom Components
1. Create Vue component in `.vitepress/theme/components/`
2. Register in `.vitepress/theme/index.ts`
3. Use in markdown with proper Vue syntax

### Theme Customization
1. Modify `.vitepress/theme/styles/`
2. Update UnoCSS configuration
3. Override VitePress theme variables

This knowledge base represents a sophisticated approach to personal knowledge management, combining the power of Obsidian for local editing with VitePress for web publishing, enhanced by a rich ecosystem of plugins and integrations.