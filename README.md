Here’s the complete `README.md` in markdown format for your repository `docsify-on-aws`:

---

```markdown
# 📘 docsify-on-aws

This project demonstrates how to deploy a static website powered by [Docsify](https://docsify.js.org/) to AWS using [Pulumi YAML](https://www.pulumi.com/docs/using-pulumi/yaml/). It sets up an S3 bucket to host the site, configures it for static hosting, and optionally sets up a CloudFront CDN for global delivery.

---

## 🚀 Deployment Overview

- 📁 Static site built using [Docsify](https://docsify.js.org)
- ☁️ Hosted on AWS S3 with public access
- 🌐 Distributed via CloudFront CDN
- 🛠️ Infrastructure as Code with Pulumi YAML

---

## 🧰 Prerequisites

Before you begin, ensure you have the following:

- [Pulumi CLI](https://www.pulumi.com/docs/get-started/install/)
- AWS CLI configured with access to S3 and CloudFront
- [Python 3.x and venv](https://www.python.org/downloads/)
- Git & GitHub account

---

## 📦 Project Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/docsify-on-aws.git
cd docsify-on-aws
```

> Replace `your-username` with your GitHub username if you fork it.

---

### 2. Create and Activate a Python Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate
```

---

### 3. Install Required Dependencies

```bash
pip install pulumi pulumi-aws
```

---

### 4. Install Pulumi Plugin (if needed)

```bash
pulumi plugin install resource aws v6.74.0
```

---

### 5. Initialize Pulumi

```bash
pulumi login
pulumi stack init dev
pulumi config set aws:region us-west-2
```

---

### 6. Define Your Website Content

Place your `index.html` and `404.html` files inside the `www/` directory. You can start with a basic [Docsify site](https://docsify.js.org/#/quickstart) or use this example:

```html
<!-- www/index.html -->
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>My Docs Site</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/vue.css">
</head>
<body>
  <div id="app">Loading Docs...</div>
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
</body>
</html>
```

---

### 7. Set Pulumi Configuration

```bash
pulumi config set docsify-on-aws:indexDocument index.html
pulumi config set docsify-on-aws:errorDocument 404.html
pulumi config set docsify-on-aws:path ./www
```

---

### 8. Deploy the Site

```bash
pulumi up
```

After confirmation, you’ll see the origin and CDN URLs in the output:

```bash
Outputs:
    cdnHostname   : xyz.cloudfront.net
    cdnURL        : https://xyz.cloudfront.net
    originHostname: bucket-name.s3-website-region.amazonaws.com
    originURL     : http://bucket-name.s3-website-region.amazonaws.com
```

---

## 🧹 Clean Up

To delete all AWS resources created:

```bash
pulumi destroy
```

---

## 📂 Repo Structure

```
docsify-on-aws/
├── Pulumi.yaml
├── Pulumi.dev.yaml
├── www/
│   ├── index.html
│   └── 404.html
└── README.md
```

---

## 📘 Useful Resources

- [Pulumi YAML Language Guide](https://www.pulumi.com/docs/using-pulumi/yaml/)
- [Docsify Docs](https://docsify.js.org)
- [AWS S3 Static Hosting](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)
- [AWS CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)

---

## 🏁 Final Notes

If you see a 404 page from CloudFront:
- Make sure your `index.html` exists in the `www/` folder.
- Confirm CloudFront has updated its cache or invalidate the cache manually.

---

📬 Questions? Feel free to open an [issue](https://github.com/your-username/docsify-on-aws/issues)!

```

---

Let me know if you want this pushed to a GitHub repo with action workflows, custom domains, or HTTPS settings!
