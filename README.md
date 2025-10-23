# GitHub Combined PRs

A static site to combine and review multiple GitHub Pull Requests at once.

## Features

- 🔐 **Secure Authentication**: Use your own GitHub Personal Access Token (PAT), stored locally in your browser
- 🔗 **Shareable URLs**: PR list is stored in the URL query string for easy sharing
- 📝 **Easy PR Management**: Add PRs via URL or simple path format (owner/repo/pull/123)
- ⚡ **Efficient Data Fetching**: Uses GitHub GraphQL API with aliases to fetch all PR data in a single request
- 🎨 **Beautiful Diffs**: Renders all file changes using diff2html with side-by-side view

## Usage

1. **Open the site**: Simply open `index.html` in your browser or host it on any static file server

2. **Add your GitHub PAT**:
   - Enter your GitHub Personal Access Token in the first section
   - Click "Save Token" (stored in browser localStorage)
   - Your token needs `repo` scope to access private repositories

3. **Add Pull Requests**:
   - Enter PR URLs or paths in the format:
     - Full URL: `https://github.com/owner/repo/pull/123`
     - Short path: `owner/repo/pull/123`
   - Click "Add PR" to add to the list
   - PRs are automatically added to the URL query string

4. **Load and Review**:
   - Click "Load PRs" to fetch all PR data from GitHub
   - View PR details, metadata, and full file diffs
   - Diffs are rendered in a side-by-side format

5. **Share**:
   - Copy the URL from your browser to share your PR list with others
   - Anyone with the URL can load the same PRs (with their own PAT)

## URL Format

```
http://your-site.com/?prs=owner/repo/pull/1,owner2/repo2/pull/2
```

The `prs` query parameter contains a comma-separated list of PR paths.

## Requirements

- Modern web browser with JavaScript enabled
- GitHub Personal Access Token with appropriate permissions
- Internet connection to fetch from GitHub API and CDN resources

## Technical Details

- Pure HTML/CSS/JavaScript (no build step required)
- Uses GitHub GraphQL API for efficient data fetching
- diff2html loaded from CDN for diff rendering
- All data stored client-side (PAT in localStorage, PRs in URL)

## Security

- Your GitHub PAT is stored only in your browser's localStorage
- The PAT is never transmitted except directly to GitHub's API
- No server-side components or third-party services

## License

MIT