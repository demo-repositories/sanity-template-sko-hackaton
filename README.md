# Sanity SKO Hackathon - Swag Store Template

A production-ready e-commerce template with Sanity Studio and Next.js frontend.

## Quick Start

### Initialize from Template
```bash
npm create sanity@latest -- --template demo-repositories/sanity-template-sko-hackaton
```

You'll be prompted for:
- **Project name:** Choose something unique
- **Organization:** Select "SKO Hackathon" 
- **Dataset:** Use "production"
- **Output path:** Press enter for current directory

### Deploy Studio
```bash
cd your-project-name/studio
pnpm install
sanity deploy
```

Choose a unique studio hostname (e.g., `your-name-swag-sko`)

### Import Product Data
```bash
# In /studio directory
sanity dataset import /path/to/products.tar.gz production
```

### Launch Frontend
```bash
cd ../frontend
pnpm install

# Copy and configure environment variables
cp .env.local.example .env.local
# Edit .env.local with your project ID (found in studio/sanity.config.ts)

# Start dev server
pnpm dev
```

Visit `http://localhost:3000`

## Project Structure
```
sanity-template-sko-hackaton/
├── studio/                      # Sanity Studio
│   └── schemaTypes/
│       ├── documents/           # Main document types
│       │   ├── product.tsx     # Product schema
│       │   ├── category.tsx
│       │   ├── collection.tsx
│       │   └── ...
│       ├── objects/            # Reusable objects
│       └── singletons/         # Site settings
│
└── frontend/                    # Next.js app
    ├── app/                    # App router
    └── lib/                    # Sanity client
```

## Customizing the Product Schema

To add a custom field to products, edit `studio/schemaTypes/documents/product.tsx`:
```typescript
// Find the fields array and add your field:
{
  name: 'yourFieldName',
  type: 'boolean', // or 'string', 'number', etc.
  title: 'Your Field Title',
  description: 'What this field does'
}
```

### Custom Field Ideas

- `featured: boolean` - Mark products to highlight on homepage
- `staffPick: boolean` - Designate team favorites
- `inStock: boolean` - Track availability
- `material: string` - Product material description
- `sustainabilityScore: number` - Rate eco-friendliness (0-10)
- `comingSoon: boolean` - Mark upcoming products
- `limitedEdition: boolean` - Special release items
- `difficulty: string` - For technical products (beginner/advanced)

After adding fields, redeploy your studio:
```bash
sanity deploy
```

## What's Included

### Core Schemas
- Product with variants, pricing, images
- Categories and collections
- Color themes and variants
- Homepage and page builder
- Blog posts

### Supporting Objects
- Custom product options (colors, sizes)
- Product features and hotspots
- Page builder modules (heroes, grids, CTAs, etc.)
- Navigation and footer configuration
- Shopify integration objects
- SEO settings

## Troubleshooting

**"Command not found: sanity"**
```bash
pnpm install -g @sanity/cli
```

**Authentication issues**
```bash
sanity logout
sanity login
```

**Find your project ID**
```bash
# In /studio directory
cat sanity.config.ts | grep projectId
```

**Port 3000 in use**
```bash
pnpm dev -- -p 3001
```

## Documentation

- [Sanity Schema Types](https://www.sanity.io/docs/schema-types)
- [GROQ Queries](https://www.sanity.io/docs/groq)
- [Next.js App Router](https://nextjs.org/docs)
- [Sanity + Next.js](https://www.sanity.io/plugins/next-sanity)

## Prerequisites

- Node.js v20 or higher
- pnpm (`npm install -g pnpm`)
- Sanity CLI (`pnpm install -g @sanity/cli`)
- Authenticated with Sanity (`sanity login`)

---

Built for Sanity SKO 2026
