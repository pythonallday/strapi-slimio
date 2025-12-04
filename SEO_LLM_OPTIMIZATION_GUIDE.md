# SEO & LLM Optimization Guide for Strapi Articles

## Schema Changes Made

### ✅ Added Fields for SEO & LLM Accessibility

1. **`publishedDate`** - Manual published date
   - Type: `datetime`
   - Purpose: Allow manual control over publication date (separate from auto-managed `publishedAt`)
   - Usage: Set the exact date you want the article to appear as published

2. **`authorName`** - Manual author name
   - Type: `string`
   - Purpose: Fallback author name if author relation is not populated
   - Usage: Ensures author is always available for structured data

3. **`metaTitle`** - SEO meta title
   - Type: `string` (max 60 chars)
   - Purpose: Separate SEO title from article title (can be optimized for search)
   - Usage: If not set, falls back to article title

4. **`metaDescription`** - SEO meta description
   - Type: `text` (max 160 chars)
   - Purpose: Separate SEO description optimized for search snippets
   - Usage: If not set, falls back to article description

5. **`keywords`** - SEO keywords
   - Type: `text`
   - Purpose: Comma-separated keywords for SEO and LLM indexing
   - Usage: Helps search engines and LLMs understand article topics

## SEO Features Implemented

### 1. Meta Tags (Open Graph & Twitter Cards)
- ✅ `og:title` - Uses metaTitle or title
- ✅ `og:description` - Uses metaDescription or description
- ✅ `og:image` - Uses seoImage or cover image
- ✅ `og:type` - Set to "article"
- ✅ `og:url` - Canonical URL
- ✅ `article:published_time` - Publication date
- ✅ `article:modified_time` - Last updated date
- ✅ `article:author` - Author name
- ✅ `article:section` - Category
- ✅ Twitter Card support

### 2. Structured Data (JSON-LD)
Added Schema.org BlogPosting structured data for:
- ✅ Better search engine understanding
- ✅ Rich snippets in search results
- ✅ LLM/AI accessibility (OpenAI, Gemini, etc.)
- ✅ Article metadata (title, description, dates, author)
- ✅ Publisher information
- ✅ Keywords and categories

### 3. Semantic HTML
- ✅ Proper `<article>` tags
- ✅ `<time>` elements with datetime attributes
- ✅ Breadcrumb navigation
- ✅ Proper heading hierarchy

## How LLMs Access Your Content

### OpenAI, Gemini, and Other LLMs
LLMs can access your content through:
1. **Web Crawling** - They crawl your public pages
2. **Structured Data** - JSON-LD helps them understand content structure
3. **Meta Tags** - Provide context about the content
4. **Semantic HTML** - Proper HTML structure aids understanding

### Best Practices for LLM Accessibility

1. **Clear Structure**
   - ✅ Use proper headings (H1, H2, H3)
   - ✅ Semantic HTML elements
   - ✅ Clear article structure

2. **Rich Metadata**
   - ✅ Complete meta tags
   - ✅ Structured data (JSON-LD)
   - ✅ Keywords and categories

3. **Content Quality**
   - ✅ Descriptive titles
   - ✅ Clear descriptions
   - ✅ Well-organized content blocks

## Field Usage Guide

### When Creating/Editing Articles

1. **Title** - Main article title (required)
2. **Meta Title** - SEO-optimized title (optional, max 60 chars)
   - Example: "10% Omzetgroei met Slimio" (shorter, keyword-focused)
   - If empty, uses main title

3. **Description** - Article summary (max 200 chars)
4. **Meta Description** - SEO description (optional, max 160 chars)
   - Example: "Ontdek hoe Monkey Donky 10% omzetgroei realiseerde met Slimio CRM voor kinderopvang"
   - If empty, uses description

5. **Published Date** - Manual publication date
   - Set the exact date you want the article to show as published
   - Useful for scheduling or backdating articles

6. **Keywords** - Comma-separated keywords
   - Example: "kinderopvang, rondleidingen, CRM, omzetgroei, Slimio"
   - Helps with SEO and LLM understanding

7. **Tags** - Array of tags (for filtering/categorization)
   - Example: ["kinderopvang", "casestudy", "rondleidingen"]

8. **SEO Image** - Image for social sharing (1200x630px recommended)
   - Used for Open Graph and Twitter Cards
   - If not set, uses cover image

## Testing SEO & LLM Accessibility

### 1. Test Structured Data
Use Google's Rich Results Test:
- https://search.google.com/test/rich-results
- Enter your article URL
- Check for BlogPosting schema

### 2. Test Meta Tags
Use Open Graph Debugger:
- https://www.opengraph.xyz/
- Enter your article URL
- Verify all meta tags are present

### 3. Test LLM Access
Ask ChatGPT or Gemini:
- "Summarize the article at https://slimio.nl/blog/your-article-slug"
- They should be able to access and understand your content

## Next Steps

1. **Commit schema changes**:
   ```bash
   cd strapi-slimio
   git add src/api/article/content-types/article/schema.json
   git commit -m "Add publishedDate, SEO fields, and LLM optimization fields"
   git push origin main
   ```

2. **Wait for Strapi Cloud deployment** (2-5 minutes)

3. **Update existing articles**:
   - Add `publishedDate` to existing articles
   - Add `metaTitle` and `metaDescription` for better SEO
   - Add `keywords` for better discoverability

4. **Test in production**:
   - Verify structured data appears in Google Search Console
   - Test social sharing (Facebook, Twitter, LinkedIn)
   - Verify LLMs can access your content

## Summary

✅ **Manual Published Date** - Full control over publication dates  
✅ **SEO Optimization** - Meta title, description, keywords  
✅ **Structured Data** - JSON-LD for search engines and LLMs  
✅ **LLM Accessibility** - Optimized for AI content understanding  
✅ **Social Sharing** - Open Graph and Twitter Cards  

Your articles are now optimized for both search engines and AI/LLM systems!

