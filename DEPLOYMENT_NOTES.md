# Deployment Notes

This site is static HTML/CSS/JS and should remain deployable on GitHub Pages without a build step.

Recommended cache behavior when fronted by Cloudflare or another CDN:

- HTML: short cache, for example `Cache-Control: public, max-age=300, must-revalidate`
- CSS/JS: medium cache, for example `Cache-Control: public, max-age=86400`
- Images and favicon: long cache, for example `Cache-Control: public, max-age=31536000, immutable`

GitHub Pages does not support custom response headers directly. Configure these rules at the CDN/proxy layer when available.
