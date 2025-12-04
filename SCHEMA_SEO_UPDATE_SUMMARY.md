# Schema Updates: Published Date & SEO/LLM Optimization

## ✅ Changes Made

### 1. Manual Published Date Field
- **Field**: `publishedDate` (datetime)
- **Purpose**: Manual control over publication date
- **Usage**: Set exact date you want article to show as published
- **Fallback**: If not set, uses `publishedAt` (auto-managed) or `createdAt`

### 2. SEO Optimization Fields

#### `metaTitle` (string, max 60 chars)
- Separate SEO-optimized title
- Falls back to main `title` if not set
- Optimized for search engine snippets

#### `metaDescription` (text, max 160 chars)
- Separate SEO-optimized description
- Falls back to main `description` if not set
- Optimized for search result snippets

#### `keywords` (text)
- Comma-separated keywords for SEO
- Helps search engines and LLMs understand content topics
- Example: "kinderopvang, rondleidingen, CRM, omzetgroei"

#### `authorName` (string)
- Manual author name field
- Fallback if author relation is not populated
- Ensures author is always available for structured data

### 3. Enhanced Description Field
- Increased `description` maxLength from 80 to 200 characters
- Better for SEO descriptions (recommended 150-160 chars)

## SEO & LLM Features Implemented in Nuxt

### ✅ Meta Tags
- Open Graph tags (Facebook, LinkedIn)
- Twitter Card tags
- Article-specific meta tags (published time, modified time, author, section)
- Keywords meta tag

### ✅ Structured Data (JSON-LD)
Added Schema.org BlogPosting structured data:
- `@type`: BlogPosting
- Headline, description, image
- Date published & modified
- Author information
- Publisher information
- Keywords and article section
- Main entity of page

**Benefits**:
- ✅ Better search engine understanding
- ✅ Rich snippets in Google search results
- ✅ LLM/AI accessibility (OpenAI, Gemini can read your content)
- ✅ Improved social sharing previews

## How LLMs Access Your Content

### OpenAI, Gemini, Claude, etc.
These AI systems can now:
1. **Crawl your articles** via web scraping
2. **Understand structure** via JSON-LD structured data
3. **Extract metadata** via meta tags
4. **Index keywords** for better topic understanding

### Example LLM Query
Users can ask:
- "Summarize the article about Monkey Donky on Slimio's blog"
- "What are the key points in Slimio's case studies?"
- "Tell me about Slimio's blog posts on kinderopvang"

The LLM will be able to:
- Find your articles
- Understand the content structure
- Extract relevant information
- Provide accurate summaries

## Next Steps

1. **Commit and push schema changes**:
   ```bash
   cd strapi-slimio
   git add src/api/article/content-types/article/schema.json
   git commit -m "Add publishedDate, SEO fields (metaTitle, metaDescription, keywords), and authorName for better SEO and LLM accessibility"
   git push origin main
   ```

2. **Wait for Strapi Cloud deployment** (2-5 minutes)

3. **Update existing articles**:
   - Set `publishedDate` for each article
   - Add `metaTitle` and `metaDescription` for better SEO
   - Add `keywords` for better discoverability
   - Add `authorName` if author relation is not set

4. **Test SEO**:
   - Use Google Rich Results Test: https://search.google.com/test/rich-results
   - Use Open Graph Debugger: https://www.opengraph.xyz/
   - Check Google Search Console for structured data

5. **Test LLM Access**:
   - Ask ChatGPT: "Summarize articles from slimio.nl/blog"
   - Ask Gemini: "What topics does Slimio blog about?"

## Field Usage Examples

### Creating a New Article

```json
{
  "title": "Hoe Monkey Donky 10% omzetgroei realiseerde",
  "metaTitle": "10% Omzetgroei met Slimio CRM | Casestudy",
  "description": "Ontdek hoe Monkey Donky Speelhuis hun rondleidingsproces verbeterde...",
  "metaDescription": "Casestudy: Monkey Donky realiseerde 10% omzetgroei met Slimio CRM voor kinderopvang. Lees hoe zij hun rondleidingsproces optimaliseerden.",
  "publishedDate": "2025-12-03T09:40:18.639Z",
  "authorName": "Slimio Team",
  "keywords": "kinderopvang, rondleidingen, CRM, omzetgroei, Slimio, casestudy",
  "tags": ["kinderopvang", "casestudy", "rondleidingen"],
  "readingTime": 5
}
```

## Summary

✅ **Manual Published Date** - Full control  
✅ **SEO Meta Fields** - Optimized titles and descriptions  
✅ **Keywords** - Better discoverability  
✅ **Structured Data** - JSON-LD for search engines and LLMs  
✅ **LLM Accessibility** - Optimized for AI content understanding  

Your articles are now fully optimized for both search engines and AI/LLM systems!

