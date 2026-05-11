# BerryCrush Website

This is the source for [berrycrush.org](https://berrycrush.org), the main landing page for the BerryCrush project.

## Technology

- **Static Site Generator**: Jekyll
- **Hosting**: GitHub Pages
- **CI/CD**: GitHub Actions

## Local Development

### Prerequisites

- Ruby 3.0+
- Bundler

### Setup

```bash
# Install dependencies
bundle install

# Run local server
bundle exec jekyll serve
```

Visit `http://localhost:4000` to preview the site.

## Deployment

The site is automatically deployed to GitHub Pages when changes are pushed to the `main` branch.

## DNS Configuration

To configure the custom domain, add the following DNS records:

### A Records (for apex domain)
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

### CNAME Record (for www subdomain)
```
www.berrycrush.org -> berrycrush.github.io
```

## Related Documentation Sites

| Site | URL | Repository |
|------|-----|------------|
| Library Docs | https://doc.berrycrush.org | berrycrush/berrycrush (doc folder) |
| VS Code Docs | https://vscode.berrycrush.org | berrycrush/vscode (doc folder) |
| IntelliJ Docs | https://intellij.berrycrush.org | berrycrush/intellij (doc folder) |

## License

Apache 2.0
