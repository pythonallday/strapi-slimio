# Article Schema Changes Summary

## Changes Made

### ✅ Added Fields (Required by Nuxt App)

1. **`tags`** - JSON field
   - Purpose: Array of tags for categorizing and filtering posts
   - Type: `json` (allows array of strings)
   - Usage in Nuxt: `attrs.tags || []`

2. **`seoImage`** - Media field
   - Purpose: Image for Open Graph and social sharing
   - Type: `media` (single image)
   - Usage in Nuxt: `getSeoImageUrl(attrs.seoImage)`

3. **`canonicalUrl`** - String field
   - Purpose: Canonical URL for SEO
   - Type: `string`
   - Usage in Nuxt: `attrs.canonicalUrl`

4. **`readingTime`** - Integer field
   - Purpose: Estimated reading time in minutes
   - Type: `integer` (1-60 minutes)
   - Usage in Nuxt: `attrs.readingTime`

### ✅ Improved Existing Fields

1. **`description`** - Increased maxLength
   - Changed from: `maxLength: 80`
   - Changed to: `maxLength: 200`
   - Reason: Better for SEO descriptions (recommended 150-160 chars)

2. **`title`** - Made required
   - Added: `"required": true`
   - Reason: Ensures all articles have a title

3. **`slug`** - Made required
   - Added: `"required": true`
   - Reason: Ensures all articles have a slug

4. **`cover`** - Restricted to images only
   - Changed from: `"allowedTypes": ["images", "files", "videos"]`
   - Changed to: `"allowedTypes": ["images"]`
   - Reason: Cover should be an image, not a file or video

### ✅ Kept As-Is (Working Correctly)

- **`author`** - Relation to Author (works with Nuxt fallback to string)
- **`category`** - Relation to Category (works with Nuxt fallback to string)
- **`blocks`** - DynamicZone (this is what we use for content)

## Field Mapping: Nuxt App → Strapi Schema

| Nuxt Expects | Strapi Field | Type | Status |
|---------------|-------------|------|--------|
| `title` | `title` | string | ✅ Required |
| `slug` | `slug` | uid | ✅ Required |
| `description` | `description` | text | ✅ Improved (200 chars) |
| `blocks` | `blocks` | dynamiczone | ✅ Works |
| `cover` | `cover` | media | ✅ Images only |
| `author` | `author` | relation | ✅ Works (with fallback) |
| `category` | `category` | relation | ✅ Works (with fallback) |
| `tags` | `tags` | json | ✅ **ADDED** |
| `seoImage` | `seoImage` | media | ✅ **ADDED** |
| `canonicalUrl` | `canonicalUrl` | string | ✅ **ADDED** |
| `readingTime` | `readingTime` | integer | ✅ **ADDED** |

## Next Steps

1. **Commit the changes**:
   ```bash
   cd strapi-slimio
   git add src/api/article/content-types/article/schema.json
   git commit -m "Add tags, seoImage, canonicalUrl, and readingTime fields to Article schema"
   git push origin main
   ```

2. **Wait for Strapi Cloud deployment** (2-5 minutes)

3. **Verify in Strapi Cloud admin**:
   - Go to Content-Type Builder
   - Check that Article has the new fields
   - Create/edit an article to test the new fields

4. **Test in Nuxt app**:
   - The Nuxt app will automatically use these fields
   - No code changes needed in Nuxt (already handles these fields)

## Notes

- All new fields are **optional** (not required) to avoid breaking existing articles
- The `tags` field uses JSON type to allow array of strings
- The `seoImage` is separate from `cover` for better SEO control
- `readingTime` is limited to 1-60 minutes (reasonable range)

