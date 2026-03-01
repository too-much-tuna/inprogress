# How to Deploy Your In Progress Website on GitHub Pages

## What's in the zip file

```
inprogress-site/
├── index.html            ← Your website
├── logo-black.png        ← Logo for light mode
├── logo-white.png        ← Logo for dark mode
├── dude-black.png        ← Mascot for light mode
├── dude-white.png        ← Mascot for dark mode
├── favicon.png           ← Browser tab icon
├── apple-touch-icon.png  ← iOS home screen icon
├── CNAME                 ← Points to inprogress.ing
├── .nojekyll             ← Tells GitHub to serve files as-is
└── README.md             ← Repo description
```

---

## Step 1: Create a GitHub account (skip if you have one)

1. Go to **github.com** and click **Sign up**
2. Use any email — your personal one is fine
3. Pick a username (this won't be public-facing since you have a custom domain)

---

## Step 2: Create a new repository

1. Click the **+** icon in the top right → **New repository**
2. Name it: **inprogress-site** (or whatever you want)
3. Set it to **Public** (required for free GitHub Pages)
4. **Do NOT** check "Add a README file" — we already have one
5. Click **Create repository**

---

## Step 3: Upload your files

After creating the repo, you'll see a setup page. The easiest method:

1. Click **"uploading an existing file"** link on that page
2. Unzip the `inprogress-site.zip` file on your computer
3. Drag **all files from inside the `inprogress-site` folder** into the upload area
   - Make sure you're dragging the files themselves, NOT the folder
   - You should see: `index.html`, `CNAME`, `.nojekyll`, all the `.png` files, `README.md`
   - **Important:** The `.nojekyll` file is a hidden file. On Mac, press `Cmd+Shift+.` in Finder to show hidden files before dragging
4. Scroll down, click **Commit changes**

---

## Step 4: Enable GitHub Pages

1. In your repo, click **Settings** (tab at the top)
2. In the left sidebar, click **Pages**
3. Under **Source**, select **Deploy from a branch**
4. Under **Branch**, select **main** and folder **/ (root)**
5. Click **Save**
6. Wait 1-2 minutes — GitHub will build and deploy your site
7. You'll see a green banner with your URL: `https://yourusername.github.io/inprogress-site/`

---

## Step 5: Connect your custom domain (inprogress.ing)

### In GitHub:
1. Still on the **Settings → Pages** screen
2. Under **Custom domain**, type: **inprogress.ing**
3. Click **Save**
4. Check **Enforce HTTPS** once it becomes available (may take a few minutes)

### At your domain registrar (where you bought inprogress.ing):
You need to update your DNS records. Go to your domain registrar's DNS settings and:

**Option A — If you want `inprogress.ing` (apex domain):**

Add these **A records** pointing to GitHub's servers:

```
Type    Name    Value
A       @       185.199.108.153
A       @       185.199.109.153
A       @       185.199.110.153
A       @       185.199.111.153
```

**Option B — If you also want `www.inprogress.ing`:**

Add a **CNAME record** as well:

```
Type    Name    Value
CNAME   www     yourusername.github.io
```

### DNS propagation:
- Changes take **5 minutes to 48 hours** to propagate worldwide
- You can check status at: **dnschecker.org**
- Once propagated, your site will be live at **https://inprogress.ing**

---

## Step 6: Verify everything works

Check these things:

- [ ] Site loads at https://inprogress.ing
- [ ] Dark mode is the default
- [ ] Light/dark toggle works in the upper right
- [ ] Logo swaps correctly between modes
- [ ] Mascot swaps correctly between modes
- [ ] Clicking "Please reach out" slides the yellow email banner from the left
- [ ] Clicking the email opens your mail client
- [ ] Clicking outside the banner closes it
- [ ] Yellow glow appears when cursor approaches edges (desktop)
- [ ] Social links open in new tabs
- [ ] Favicon appears in browser tab
- [ ] Mobile layout looks correct on your phone

---

## Making future updates

To edit your site later:

1. Go to your repo on github.com
2. Click on `index.html`
3. Click the **pencil icon** (Edit this file)
4. Make your changes
5. Click **Commit changes**
6. Wait ~1 minute for the update to go live

Or, if I build you a new version:

1. Go to your repo
2. Click **Add file → Upload files**
3. Drag the new `index.html` in
4. It will ask to overwrite — confirm
5. Commit changes

---

## If you're migrating from Cargo

Once your GitHub Pages site is live and working:

1. Go to your Cargo dashboard
2. If Cargo is managing your DNS for `inprogress.ing`, you'll need to transfer DNS management to your domain registrar first
3. Update DNS records at your registrar to point to GitHub (Step 5 above)
4. You can keep your Cargo account active or cancel it — the sites are independent

**Important:** Don't update DNS until your GitHub Pages site is fully working at the `yourusername.github.io` URL first. Test everything there, then switch DNS.
