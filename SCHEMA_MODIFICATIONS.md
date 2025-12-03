# Article Schema Modifications for Nuxt Integration

## Current Schema Analysis

### ✅ Fields Already Present
- `title` - String (required)
- `slug` - UID (auto-generated from title)
- `description` - Text (max 80 chars)
- `cover` - Media (single image)
- `author` - Relation to Author (manyToOne)
- `category` - Relation to Category (manyToOne)
- `blocks` - DynamicZone (with rich-text, media, quote, slider components)

### ❌ Fields Missing (Expected by Nuxt App)
- `tags` - Array of strings (for categorizing posts)
- `seoImage` - Media field (for Open Graph/social sharing)
- `canonicalUrl` - String (for SEO)
- `readingTime` - Number (estimated reading time in minutes)

### ⚠️ Potential Issues
- `author` is a **relation** but Nuxt code can handle both relation and string
- `category` is a **relation** but Nuxt code can handle both relation and string
- `description` has maxLength: 80, but Nuxt might need longer descriptions

## Recommended Schema Modifications

### Option 1: Add Missing Fields (Recommended)
Add the missing fields to support all Nuxt features without breaking existing functionality.

### Option 2: Keep Current Schema (Works but Limited)
The current schema works with the Nuxt app, but you'll miss:
- Tags functionality
- SEO image for social sharing
- Canonical URL
- Reading time display

## Decision

**Recommendation**: Add the missing fields to fully support your Nuxt blog features.

