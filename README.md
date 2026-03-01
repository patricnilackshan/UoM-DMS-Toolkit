<div align="center">

# 🎓 UoM DMS Toolkit

*Data-free downloads, uploads & sharing for UoM students*

**Torrents · YouTube · M3U8 · Direct Links**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/patricnilackshan/UoM_DMS_Toolkit/blob/main/UoM_DMS_Toolkit.ipynb)
&nbsp;
[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-Workflow-2088FF?logo=githubactions&logoColor=white)](../../actions/workflows/dms.yml)

<img src="https://visitor-badge.laobi.icu/badge?page_id=patricnilackshan.UoM_DMS_Toolkit" align="right"/>

</div>

---

## Features

| | Feature |
|---|---|
| 📥 | Download from direct links, YouTube, M3U8 streams, and Magnet/Torrent links |
| 📤 | Upload files directly to your UoM DMS account via WebDAV |
| 🔗 | Share uploaded files and get a public DMS link instantly |
| 📋 | View all shares in your DMS account |
| 🗑️ | Delete shares by Share ID |
| 🖴 | Mount DMS as a local drive on Windows & Linux |
| ⚙️ | GitHub Actions workflow — download & upload without opening a browser |

---

## Usage

### 🗒️ Google Colab Notebook

The easiest way to use the toolkit. No setup required — all link types including YouTube work out of the box.

1. Open the notebook in [Google Colab](https://colab.research.google.com/github/patricnilackshan/UoM_DMS_Toolkit/blob/main/UoM_DMS_Toolkit.ipynb)
2. Run the **Sign in** cell — enter your DMS username & password (dependencies install automatically)
3. Run **Download**, **Upload**, **Share** cells in order

> Filenames are automatically sanitized before upload — invalid characters are replaced with underscores.

### ⚙️ GitHub Actions Workflow

Download any file and upload it to DMS directly from GitHub — no Colab needed.

1. Go to **Actions** → **Download and Upload to DMS** → **Run workflow**
2. Fill in your DMS username, password, and the download link
3. The workflow downloads the file, zips if multiple files are produced, uploads to DMS, and prints the shareable link

**Supported link types:**

| Link | Handler | Works without extra setup |
|---|---|---|
| `magnet:?xt=urn:btih:...` | libtorrent | ✅ |
| `*.m3u8` | ffmpeg | ✅ |
| Any HTTP/HTTPS URL | requests | ✅ |
| `youtube.com` / `youtu.be` | yt-dlp | ⚠️ Requires cookies (see Notes) |

---

## Notes

### YouTube Downloads in GitHub Actions

GitHub Actions runners use datacenter IPs that YouTube flags as bots, causing yt-dlp to fail with:

```
Sign in to confirm you're not a bot.
```

The fix is to provide your YouTube cookies so yt-dlp can authenticate. There are two ways:

**Option 1 — Workflow input (one-time use):** Paste your cookies directly into the `youtube_cookies` field when running the workflow.

**Option 2 — Repository secret (persistent):** Store your cookies as a secret named `YOUTUBE_COOKIES` under **Settings → Secrets and variables → Actions**. The workflow will use it automatically for every run.

> The input takes priority over the secret if both are provided.

**How to export YouTube cookies:**
1. Install the [Get cookies.txt LOCALLY](https://chromewebstore.google.com/detail/get-cookiestxt-locally/cclelndahbckbenkjhflpdbgdldlbecc) browser extension
2. Go to [youtube.com](https://youtube.com) while signed in
3. Click the extension → export in **Netscape format**
4. Paste the content into the workflow input or save as the `YOUTUBE_COOKIES` secret

> This issue does **not** affect the Google Colab notebook, as Colab IPs are not blocked by YouTube.

### Filename Sanitization

Filenames with spaces or special characters can cause issues when passed to shell commands like `curl`. Both the notebook and the workflow automatically sanitize filenames before upload — replacing any character outside `[a-zA-Z0-9_.]` with an underscore (spaces included).

---

## Mount DMS as a Local Drive

**Windows 🪟** — Run in Command Prompt:
```
net use Z: https://dms.uom.lk/remote.php/webdav/ /user:<userName> <userPassword>
```

**Linux 🐧** — Enter in File Manager → *Connect to Server*:
```
davs://dms.uom.lk/remote.php/webdav/
```

---

<div align="center">

© **Patric Nilackshan** · [pnilackshan@gmail.com](mailto:pnilackshan@gmail.com)

</div>
