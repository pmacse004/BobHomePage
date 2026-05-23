# IBM Bob Projects - Homepage

A modern, minimal web application for managing project links with cross-device sync.

## 🌟 Features

- ✨ Modern gradient UI design with collapsible sidebar
- 🔗 Add and manage project links
- 🔄 **Cross-device sync via GitHub** (optional)
- 💾 Automatic data persistence (localStorage + GitHub)
- 📱 Fully responsive design
- 🚀 Zero dependencies - pure HTML/CSS/JS
- 🖼️ Iframe-based content loading (URL stays the same)

## 🚀 Live Demo

Visit: [https://pmacse004.github.io/BobHomePage](https://pmacse004.github.io/BobHomePage)

## 🔄 Cross-Device Sync Setup

To sync your links across all devices, follow these steps:

1. **Create a GitHub Personal Access Token**
   - See detailed instructions in [GITHUB_TOKEN_SETUP.md](GITHUB_TOKEN_SETUP.md)
   - Visit: https://github.com/settings/tokens
   - Generate token with `repo` permissions

2. **Configure on each device**
   - Open browser console (F12)
   - Run: `localStorage.setItem('github_token', 'YOUR_TOKEN_HERE')`
   - Refresh the page

3. **Verify sync is working**
   - Check the sync status indicator at the top of the sidebar
   - Should show "✅ Synced with GitHub"

**Note**: Without a token, links are saved locally only (per device).

## 📦 Deployment

### GitHub Pages
1. Push to GitHub
2. Go to Settings → Pages
3. Select `main` branch
4. Your site will be live at `https://pmacse004.github.io/BobHomePage`

### GoDaddy Hosting (ibmbob.in)
1. Upload `index.html` to your hosting root directory
2. Access via your domain
3. Set up GitHub token on each device for sync

## 💻 Local Development

Simply open `index.html` in your browser - no build process needed!

## 📝 Usage

1. **Add Links**: Enter name and URL, click "Add Link"
2. **View Content**: Click any link to load it in the iframe (URL stays the same)
3. **Delete Links**: Click the 🗑️ button
4. **Collapse Sidebar**: Click the ◀ button for more screen space
5. **Sync Status**: Click the status bar to manage GitHub token

### Sync Behavior
- **With Token**: Links sync across all devices automatically
- **Without Token**: Links saved locally per device only
- **Auto-refresh**: Syncs every 30 seconds when token is configured

## 🎨 Customization

All styles are in the `<style>` section of `index.html`. Modify colors, fonts, or layout as needed.

## 📄 License

Free to use and modify.