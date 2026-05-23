# GitHub Token Setup Guide

To enable syncing your links across all devices, you need to create a GitHub Personal Access Token.

## 🔐 Step 1: Create a Personal Access Token

1. **Go to GitHub Settings**:
   - Visit: https://github.com/settings/tokens
   - Or: Click your profile → Settings → Developer settings → Personal access tokens → Tokens (classic)

2. **Generate New Token**:
   - Click "Generate new token" → "Generate new token (classic)"
   - Give it a name: `IBM Bob Projects Sync`
   - Set expiration: `No expiration` (or choose your preference)

3. **Select Permissions**:
   - ✅ Check **`repo`** (Full control of private repositories)
     - This includes: `repo:status`, `repo_deployment`, `public_repo`, `repo:invite`, `security_events`
   
4. **Generate and Copy**:
   - Click "Generate token" at the bottom
   - **IMPORTANT**: Copy the token immediately (you won't see it again!)
   - It looks like: `ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

## 🔧 Step 2: Add Token to Your Website

1. **Open your website**: https://ibmbob.in

2. **Open Browser Console**:
   - Press `F12` or `Ctrl+Shift+I` (Windows/Linux)
   - Press `Cmd+Option+I` (Mac)
   - Go to the "Console" tab

3. **Set Your Token**:
   ```javascript
   localStorage.setItem('github_token', 'ghp_YOUR_TOKEN_HERE');
   ```
   Replace `ghp_YOUR_TOKEN_HERE` with your actual token

4. **Refresh the page** - Your links will now sync across all devices!

## ✅ Step 3: Verify It's Working

- Add a link on one device
- Open the website on another device
- The link should appear automatically (within 30 seconds or on page refresh)
- Check the sync status indicator at the top of the sidebar

## 🔒 Security Notes

- **Never share your token** with anyone
- The token is stored in your browser's localStorage
- Each device needs the token set once
- If compromised, revoke it immediately at: https://github.com/settings/tokens

## 🔄 Setting Token on Multiple Devices

Repeat Step 2 on each device where you want to access your links:
- Your work computer
- Your home computer  
- Your phone/tablet browser

## ❌ Revoking Access

If you need to revoke the token:
1. Go to: https://github.com/settings/tokens
2. Find "IBM Bob Projects Sync"
3. Click "Delete"
4. Generate a new token and update all devices

## 🆘 Troubleshooting

**Links not syncing?**
- Check if token is set: Open console and type `localStorage.getItem('github_token')`
- Verify token has `repo` permissions
- Check sync status indicator for errors

**Token expired?**
- Generate a new token
- Update it on all devices using Step 2

**Want to remove token?**
```javascript
localStorage.removeItem('github_token');