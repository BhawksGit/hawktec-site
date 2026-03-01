# HawkTec Website

Static product showcase site for [www.hawktec.shop](https://www.hawktec.shop), hosted on GitHub Pages with a Namecheap domain.

## File Structure

```
hawktec-site/
├── index.html          ← Main page (loads products from products.js)
├── products.js         ← Product data (edit this to add/update products)
├── logo.png            ← YOUR LOGO FILE (430x158px) — add this yourself
├── CNAME               ← Custom domain config for GitHub Pages
├── README.md
├── r4xmp/
│   └── index.html      ← R4xMP product help page
└── dspico/
    └── index.html      ← DSPico product help page
```

## Adding / Editing Products

Edit `products.js`. Each product is a JS object in the `PRODUCTS` array. Copy an existing entry and edit it. Fields:

| Field | Description | Leave as `""` if unavailable |
|---|---|---|
| `title` | Amazon product title | No |
| `url` | Amazon listing URL | No |
| `image_url` | Amazon product image URL | Shows placeholder |
| `price` | Price (e.g. `"17.49"`) | Card shows "Coming Soon" |
| `stars` | Star rating (e.g. `"4.5"`) | Stars hidden |
| `review_count` | Number of reviews | Stars hidden |
| `sales_per_month` | e.g. `"200+"` | Hidden |
| `help_path` | Path to help page, e.g. `"/r4xmp"` | Help button hidden |

**To get Amazon image URLs:** Right-click the main product image on Amazon → "Open image in new tab" → copy the URL. It will look like `https://m.media-amazon.com/images/I/XXXXX._AC_SL1500_.jpg`.

**To add a new product:** Copy one of the objects in `products.js` and edit the fields. For a new help page, create a new folder (e.g. `newproduct/index.html`) and set `help_path` to `"/newproduct"`.

## Setup: GitHub Pages

1. Create a new GitHub repo (e.g. `hawktec-site`)
2. Push all these files to the `main` branch
3. Go to **Settings → Pages**
4. Under "Source", select **Deploy from a branch** → `main` → `/ (root)`
5. Under "Custom domain", enter `www.hawktec.shop` → Save
6. Check **Enforce HTTPS** once the certificate is provisioned

## Setup: Namecheap DNS

In your Namecheap dashboard for `hawktec.shop`:

1. Go to **Advanced DNS**
2. Add a **CNAME Record**:
   - Host: `www`
   - Value: `YOUR-GITHUB-USERNAME.github.io`
   - TTL: Automatic
3. Add **A Records** pointing the apex domain to GitHub's IPs:
   - Host: `@` → `185.199.108.153`
   - Host: `@` → `185.199.109.153`
   - Host: `@` → `185.199.110.153`
   - Host: `@` → `185.199.111.153`
4. (Optional) Add a **URL Redirect** from `hawktec.shop` to `www.hawktec.shop`

DNS changes may take up to 48 hours to propagate. Once done, GitHub will automatically provision an SSL certificate.

## Logo

Add your HawkTec logo as `logo.png` in the root directory. The site expects a 430×158px image. If the logo file is missing, the text "HawkTec" will display as a fallback.
