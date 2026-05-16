# AWS Assignment 2 — Static Website Hosting on S3

## Objective
Host a simple static website using Amazon S3 and make it accessible via a public URL.

---

## Files in This Repo

| File | Description |
|------|-------------|
| `index.html` | The static webpage uploaded to S3 |
| `bucket-policy.json` | S3 bucket policy to allow public read access |
| `README.md` | Step-by-step documentation |

---

## Steps Followed

### Step 1: Create the Website
Created `index.html` — a simple static webpage with HTML and CSS styling.

### Step 2: Create an S3 Bucket
1. Go to **AWS Console → S3 → Create Bucket**
2. Enter a globally unique bucket name (e.g., `pranay-aws-static-site`)
3. Select your preferred region
4. **Uncheck** "Block all public access" (required for public hosting)
5. Acknowledge the warning → Click **Create Bucket**

### Step 3: Upload the File
1. Open the bucket → Click **Upload**
2. Add `index.html` → Click **Upload**

### Step 4: Enable Static Website Hosting
1. Go to bucket → **Properties** tab
2. Scroll to **Static website hosting** → Click **Edit**
3. Enable it → Set **Index document** to `index.html`
4. Click **Save changes**
5. Note the **Bucket website endpoint** URL shown at the bottom

### Step 5: Make the Bucket Public (Bucket Policy)
1. Go to bucket → **Permissions** tab
2. Scroll to **Bucket policy** → Click **Edit**
3. Paste the following policy (replace `your-bucket-name` with your actual bucket name):

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicRead",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::pranay-aws-website-2026-704530913686-us-east-1-an/*"
        }
    ]
}
```

4. Click **Save changes**

---

## Final Output

The website is accessible at:

```
http://your-bucket-name.s3-website-<region>.amazonaws.com
```

Example:
```
http://pranay-aws-static-site.s3-website-us-east-1.amazonaws.com
```

---

## Submission Checklist
- [x] `index.html` created and uploaded
- [x] S3 bucket created with static website hosting enabled
- [x] Bucket policy applied for public access
- [x] Website accessible via public S3 URL
- [x] GitHub repo with `index.html` + `README.md`
- [ ] S3 website link (add your link here after deployment)
- [ ] Screenshots (add screenshots folder after deployment)

---

## Key AWS Concepts Used
- **Amazon S3** — Simple Storage Service for object/file storage
- **Static Website Hosting** — S3 feature to serve HTML files over HTTP
- **Bucket Policy** — JSON-based IAM policy to control access permissions
- **Public Access** — Allowing unauthenticated users to read objects via URL
