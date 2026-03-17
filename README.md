# Dylan Bergen — Engineering Portfolio

## Quick Start

1. Buy a domain (e.g., `dylanbergen.com`) from Namecheap or Cloudflare Registrar (~$10/yr)
2. Create a GitHub account if you don't have one
3. Create a new repository called `dylanbergen.github.io` (or any name)
4. Push this entire folder to the repo
5. Enable GitHub Pages in repo Settings > Pages > Source: main branch
6. Connect your custom domain in Settings > Pages > Custom domain
7. Add a CNAME record at your registrar pointing to `dylanbergen.github.io`

Your site will be live at `https://dylanbergen.com` within minutes.

---

## Adding Your Photos

### Image locations
Put all project images in the `images/projects/` folder. Recommended format: JPEG for photos, PNG for screenshots.

### Image sizing
- **Project card thumbnails** (homepage grid): aim for ~800x500px or similar 16:10 ratio
- **Gallery images** (project detail pages): aim for ~1200x900px or similar 4:3 ratio
- **File size**: keep under 500KB per image. Use a tool like https://squoosh.app to compress

### How to add a photo
In each HTML file, find the placeholder blocks that look like this:

```html
<div class="project-gallery-item">
  <span class="project-card-placeholder">downpipes.jpg</span>
</div>
```

Replace the entire inner content with an img tag:

```html
<div class="project-gallery-item">
  <img src="../images/projects/downpipes.jpg" alt="Custom TIG welded downpipes">
</div>
```

For the homepage project cards, the pattern is similar:

```html
<!-- Before -->
<div class="project-card-image">
  <span class="project-card-placeholder">Add photo: e90-hero.jpg</span>
</div>

<!-- After -->
<div class="project-card-image">
  <img src="images/projects/e90-hero.jpg" alt="BMW E90 build">
</div>
```

### Recommended photos per project

**E90 BMW Build:**
- Hero: Overall engine bay or car shot
- Exhaust: downpipes, welding in progress, completed exhaust
- Cooling: oil cooler setup, AN lines routed, diff cover mod
- Brackets: catch can mount, solenoid mount

**Wiring Harnesses:** (most important project for defense jobs)
- Hero: A complete harness laid out on a table
- Close-up of concentric twist with Raychem
- DTM connector detail with sealed boots
- DMC crimp tooling setup
- Crimp cross-section if you have one

**PCB Design:**
- Hero: KiCad 3D render of a board
- Schematic screenshot
- Layout screenshot showing layers
- Assembled board (when available)

**Miata ITB:**
- Hero: Throttle bodies installed on engine
- Machining the manifold on the Bridgeport
- Welding the ITBs to the manifold
- Megasquirt installed / wiring

**FSAE:**
- Hero: Car on track or in paddock
- Suspension components (designed and machined)
- You working on the car
- Competition shots

---

## File Structure

```
portfolio/
├── index.html              ← Homepage with project grid
├── about.html              ← Background, skills, equipment, experience
├── css/
│   └── style.css           ← All styling
├── js/
│   └── main.js             ← Mobile nav toggle
├── images/
│   └── projects/           ← Drop your photos here
├── projects/
│   ├── e90.html            ← BMW E90 build detail
│   ├── harness.html        ← Wiring harness detail
│   ├── pcb.html            ← PCB design detail
│   ├── miata.html          ← Miata ITB / ECU detail
│   └── fsae.html           ← FSAE team detail
└── README.md               ← This file
```

---

## Customization

### Adding a resume PDF
1. Drop your resume PDF in the root folder as `Dylan_Bergen_Resume.pdf`
2. Uncomment the resume link in the nav (in every HTML file):
   ```html
   <li><a href="Dylan_Bergen_Resume.pdf" target="_blank">Resume</a></li>
   ```

### Adding a new project
1. Copy any existing project HTML file in `projects/`
2. Update the content
3. Add a new card to the grid in `index.html`

### Changing colors
Edit the CSS variables at the top of `css/style.css`:
- `--accent`: The amber/gold accent color
- `--bg-primary`: Main background
- `--bg-card`: Project card background

---

## GitHub Pages Deployment (Step by Step)

```bash
# 1. Initialize git in this folder
cd portfolio
git init

# 2. Add all files
git add .

# 3. Commit
git commit -m "Initial portfolio"

# 4. Create repo on GitHub, then push
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git branch -M main
git push -u origin main

# 5. Go to GitHub repo > Settings > Pages
#    Source: Deploy from a branch
#    Branch: main, / (root)
#    Save

# 6. Your site is live at https://YOUR_USERNAME.github.io/YOUR_REPO/
#    Or at your custom domain once you set up DNS
```

### Custom Domain DNS Setup (Namecheap example)
1. In Namecheap, go to Domain List > Manage > Advanced DNS
2. Add these records:
   - Type: A, Host: @, Value: 185.199.108.153
   - Type: A, Host: @, Value: 185.199.109.153
   - Type: A, Host: @, Value: 185.199.110.153
   - Type: A, Host: @, Value: 185.199.111.153
   - Type: CNAME, Host: www, Value: YOUR_USERNAME.github.io.
3. In GitHub repo Settings > Pages > Custom domain: enter `dylanbergen.com`
4. Check "Enforce HTTPS"
5. Wait 10-30 minutes for DNS propagation
