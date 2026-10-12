# Student Portfolio Workshop

Build your own portfolio with HTML and CSS, then publish it on AWS.
No JavaScript, framework or build step is needed. Navigation and email links
use built-in browser behavior.

**Use the files in this main folder.** The nested `aws_portfolio_workshop/` folder
contains an older template.

## 1. Open the website

Double-click `index.html` to open it in your browser. After editing, save your
files and refresh the page to see your changes.

For a local server, run either command from this folder:

```bash
python3 -m http.server 8000
```

Or, if you have Node.js and npm:

```bash
npm run dev
```

Visit [localhost:8000](http://localhost:8000). The npm command downloads `serve`
on its first run.

## 2. Make it yours

| File | What to change |
| --- | --- |
| `index.html` | Your name, bio, school, skills, projects, experience and links |
| `404.html` | Your name on the “page not found” page |
| `assets/photo.jpg` | Default avatar: replace with your photo; keep the file name |
| `assets/resume.pdf` | Replace with your résumé; keep the file name |
| `style_2.css` | Optional: colors, fonts and layout |

In your editor, use **Find** (Ctrl+F, or Cmd+F on Mac) to locate these placeholders:

- `Your Name` and `Your University`: add your full name and school.
- `Name's <em>Portfolio</em>` in both HTML files: replace `Name` with your last name (for example, `Smith's <em>Portfolio</em>`).
- `your@email.com`: add your email address.
- `yourusername`: add your GitHub and LinkedIn usernames.
- `your-domain.com`: add your site's address once it is published.

Update the page title, internship status, graduation date, city and footer year
too. Replace the example stats by editing the displayed numbers, such as `12`
or `99%`. Delete anything that does not apply to you.

## 3. Add your work

The comments in `index.html` mark each section: **ABOUT**, **SKILLS**,
**PROJECTS**, **EXPERIENCE** and **CONTACT**.

- **Projects:** copy an entire `<article class="card project">...</article>` block. Edit the title, description, tools, result and links.
- **Skills:** edit the `<li class="chip">...</li>` items. Copy a whole `skill-group` block to add a category.
- **Experience:** copy a whole `timeline__item` block. Include internships, research, teaching or club roles, with the newest first.
- **Sections:** if you remove or reorder a section, update the navigation links to match.

Card colors and section/project numbers update automatically.

Describe **what you built and what changed because of it**. For example:
“Built a study-group finder with AWS Lambda and DynamoDB, used by 150 students.”
Only use numbers you can explain in an interview.

Optional project screenshot: create `assets/projects/`, add your image, and put
this inside the project's `project__banner` div:

```html
<img src="assets/projects/my-app.jpg" alt="Screenshot of My App" loading="lazy" />
```

## 4. Change the look (optional)

Start with the `:root` block at the top of `style_2.css`:

- `--paper`: page background.
- `--ochre`: main accent color.
- `--sky`, `--sun`, `--leaf`: card colors.
- `--font-display`, `--font-body`, `--font-mono`: fonts. If you choose new fonts, update the Google Fonts links in both HTML files too.

The rest of the CSS is labeled by component. Mobile and print styles are near
the bottom.

Try one change at a time, save, and refresh:

- Change `--ochre` and see which parts of the page use it.
- Edit one stat; its value is plain text in `index.html`.
- Copy a project card and see the grid, colors and numbers update.
- Narrow your browser window and see the navigation links wrap.

## 5. Publish on AWS

Use the S3 bucket and CloudFront distribution configured during the workshop.
If you still need to set up hosting, follow the
[AWS hosting guide](https://docs.aws.amazon.com/AmazonS3/latest/userguide/HostingWebsiteOnS3Setup.html).

1. Upload `index.html`, `404.html`, `style_2.css` and the `assets/` folder to your bucket. Keep the folder structure.
2. Open your website URL and check it loads.
3. Replace `your-domain.com` in `index.html` with your real address, then upload that file again. This updates the link previews and search information.
4. After changes, upload the changed files. If you use CloudFront, create an **invalidation** for `/*` to refresh its cached copies.

You do not need to upload the README, `package.json`, `signin.jpg` or the older
template folder. For a custom link-preview image, replace `assets/og-image.jpg`
with a 1200 × 630 px image.

**Set up the error page:** for S3 website hosting, set the **Error document** to
`404.html`. For CloudFront with a private S3 bucket, add custom error responses
for both **403** and **404**, using `/404.html` and response code **404**. See
[AWS custom error pages](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/GeneratingCustomErrorResponses.html).

## Before you share

- [ ] Replace all placeholder text, links and example numbers.
- [ ] Click the project links, résumé links and Email link.
- [ ] Check the layout and navigation links on your phone.
- [ ] Visit a made-up URL such as `/nope` to check the error page.
- [ ] Check the printed version with Ctrl+P (Cmd+P on Mac).
