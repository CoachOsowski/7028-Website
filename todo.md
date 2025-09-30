7) Prepare Bluehost for deploys

Preferred: SFTP/SSH (Option A).

Enable SSH access in your Bluehost account (cPanel → Security → SSH Access → Manage SSH Keys). 
Bluehost

Create/authorize an SSH key, and note your SSH hostname and username. 
Bluehost

Typical web root path is /home/<youruser>/public_html/ (addon domains map to subfolders). 
Bluehost

Fallback: FTPS (Option B).

Create an FTP account; your server path for the primary domain is /public_html/. 
Bluehost

8) Add GitHub Secrets

If using SFTP (Option A):

SSH_HOST (e.g., box###.bluehost.com or your domain)

SSH_USER (your hosting user)

SSH_PRIVATE_KEY (paste your private key; no passphrase for CI or use an Actions secret for it)

If using FTPS (Option B):

FTP_SERVER (Bluehost FTP host or domain)

FTP_USERNAME / FTP_PASSWORD

Repo → Settings → Secrets and variables → Actions → New repository secret.

9) Push and watch it deploy

Commit anything (even a typo fix) and push to main.
Actions should: checkout (with submodules), install Hugo, build, then deploy to Bluehost via your chosen method. 
GitHub
+1

10) Day-to-day editing (Markdown + images)

Add posts under content/posts/.

Put images in static/img/ and reference them with /img/....

git commit → git push → site auto-rebuilds + redeploys. 
Hugo

Add-ons (optional, when you care)

Speed up CI by caching Hugo resources/:

- uses: actions/cache@v4
  with:
    path: resources
    key: ${{ runner.os }}-hugo-${{ hashFiles('**/*') }}
    restore-keys: ${{ runner.os }}-hugo-


Subdomain / addon domain: change server-dir (FTPS) or target (SFTP) to that domain’s mapped folder (e.g., /public_html/blog/). 
Bluehost

Theme vendoring: if you dislike submodules, you can copy the theme into themes/PaperMod and drop the submodules: recursive bit.

Common pitfalls (quick fixes)

Theme not found in CI → ensure actions/checkout fetches submodules (submodules: recursive).

Blank homepage → your post is still draft: true; set draft: false or run hugo server -D. 
Hugo

Wrong live path → verify Bluehost root (/home/<user>/public_html/...) and permissions. 
Bluehost

Long FTPS uploads / timeouts → prefer SFTP (Option A). 
Stack Overflow
