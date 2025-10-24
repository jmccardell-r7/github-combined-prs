# GitHub Combined PRs

A static site to combine and review multiple GitHub Pull Requests at once.

## Features

- 🔐 **Secure Authentication**: Use your own GitHub Personal Access Token (PAT), stored locally in your browser
- 🔗 **Shareable URLs**: PR list is stored in the URL query string for easy sharing
- 📝 **Easy PR Management**: Add PRs via URL or simple path format (owner/repo/pull/123)
- ⚡ **Efficient Data Fetching**: Uses GitHub GraphQL API with aliases to fetch all PR data in a single request
- 🎨 **Beautiful Diffs**: Renders all file changes using diff2html with side-by-side view
- 📁 **File Explorer**: Aggregated tree view of all changed files across all PRs for quick navigation
- 💬 **Comments & Reviews**: View all PR comments, reviews, and inline code comments in one place
- 👁️ **Hide Individual Comments**: Hide/show individual comments with a single click, state persists in localStorage
- 🙈 **Hide Minimized Comments**: Automatically hide minimized comments (spam, outdated, etc.) with a toggle to show them if needed
- 🔗 **Jump Links**: Quick navigation links in the PR list to jump to each PR section
- ✓ **Approval Status**: Visual indicators showing which PRs you have approved
- ✍️ **Add Comments**: Post new comments directly from the interface
- ✅ **PR Approvals**: Approve pull requests with a single click

## Usage

1. **Open the site**: Simply open `index.html` in your browser or host it on any static file server
   - **Try the demo**: Open `demo.html` to see the new features without needing a GitHub token

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
   - The "Current PRs" list shows approval status and jump links for each PR
   - Diffs are rendered in a side-by-side format
   - Read comments and reviews from collaborators
   - **Filter Comments**: Use checkboxes to control comment visibility:
     - Hide automated comments from specific users (checked by default)
     - Hide minimized comments (spam, outdated, resolved, etc. - checked by default)
     - Show/hide inline comments with diffs (checked by default)
   - Hide individual comments by clicking the "Hide" button (hidden state persists)
   - Minimized comments show a [MINIMIZED] badge with the reason when visible
   - Add your own comments using the comment box
   - Approve PRs with the "Approve PR" button

5. **Share**:
   - Copy the URL from your browser to share your PR list with others
   - Anyone with the URL can load the same PRs (with their own PAT)

## URL Format

```
http://your-site.com/?prs=owner/repo/pull/1,owner2/repo2/pull/2
```

The `prs` query parameter contains a comma-separated list of PR paths.

## File Explorer

When you load PRs, a file explorer appears showing all changed files across all PRs:

- **Tree Structure**: Files are organized by directory in a collapsible tree view
- **Quick Navigation**: Click any file to jump directly to its diff in the corresponding PR
- **Multi-PR Indicator**: Files changed in multiple PRs show a badge indicating how many PRs modify that file
- **Statistics**: View total files, directories, and PRs at a glance
- **Familiar UI**: Similar to code review tools like Crucible for easy adoption

The file explorer makes it easy to:
- Get an overview of all changes across multiple PRs
- Navigate directly to specific files you want to review
- Identify files that are being modified in multiple PRs simultaneously

## Comments and Approvals

The application displays all comments and reviews associated with each PR:

- **Issue Comments**: General comments on the PR
- **Review Comments**: Code review feedback with approval state (APPROVED, CHANGES_REQUESTED, etc.)
- **Inline Comments**: Comments on specific lines of code, shown with the file path

You can interact with PRs directly from the interface:

- **Add Comments**: Use the text area below each PR to post new comments
- **Approve PRs**: Click the "Approve PR" button to submit an approval review
  - You can include an optional comment with your approval
  - The default message is "Approved via GitHub PR Combiner" if no comment is provided

**Note**: Your GitHub PAT must have `repo` scope to post comments and approve PRs.

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