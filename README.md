# Justin Joseph — AWS Portfolio

[![Deploy portfolio](https://github.com/JJosephE/aws-portfolio-website/actions/workflows/deploy.yml/badge.svg)](https://github.com/JJosephE/aws-portfolio-website/actions/workflows/deploy.yml)

My personal portfolio website, built with HTML, CSS, and JavaScript. It shares my background, cybersecurity experience, projects, and resume.

The website is hosted on Amazon S3 and served through Amazon CloudFront. GitHub Actions automatically deploys updates when I push changes to the `main` branch.

## How deployment works

1. I edit the website files and push the changes to `main`.
2. GitHub Actions downloads the latest code and prepares the frontend files.
3. It authenticates to AWS using temporary credentials through OpenID Connect (OIDC).
4. It uploads the website files to the S3 bucket.
5. It invalidates the CloudFront cache so visitors can receive the updated website.

The workflow is in [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml). This is a static website, so no build step is needed.

## Tools used

| Tool | Purpose |
| --- | --- |
| HTML, CSS, and JavaScript | Website content, styling, and interactions |
| Amazon S3 | Stores the website files |
| Amazon CloudFront | Serves the website and caches its files |
| GitHub Actions | Automatically deploys updates |
| AWS IAM and OIDC | Give the workflow temporary, restricted access to AWS |

## Security setup

- No permanent AWS access keys are stored in GitHub.
- The deployment role trusts only this repository's `main` branch.
- The role can list the portfolio bucket, upload approved frontend paths, and invalidate the portfolio's CloudFront distribution.
- Repository documentation and configuration files are excluded from deployment.

## Main files

| File or folder | Purpose |
| --- | --- |
| `index.html` | Main portfolio page |
| `404.html` | Custom error page |
| `content.js` | Website JavaScript |
| `portfolio.css` and `style_2.css` | Stylesheets |
| `assets/` | Resume, headshot, icons, and other website assets |
| `.github/workflows/deploy.yml` | Automatic deployment workflow |

## Testing the pipeline

I tested automatic deployment by changing the website in GitHub, confirming the workflow completed successfully, and checking that the change appeared on the live site.

To test future updates:

1. Make a small visible change in `index.html`.
2. Commit it to `main`.
3. Check the run in the repository's **Actions** tab.
4. Wait for the CloudFront invalidation to complete, then check the live site.

The current workflow uploads new and changed files without deleting existing S3 objects. Removed or renamed files need separate cleanup.

## What I learned

This project gave me hands-on practice with AWS static website hosting, GitHub Actions, IAM permissions, OIDC authentication, and CloudFront cache invalidation.

It also helped me troubleshoot deployment permissions and connect source control to a working cloud deployment process.
