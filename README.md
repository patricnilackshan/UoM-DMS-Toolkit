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

---

## There are 2 Ways to Use This

| | Method | YouTube | Your logs | Setup needed |
|---|---|---|---|---|
| ⭐ | **Google Colab** *(Recommended)* | ✅ Works | 🔒 Private | None |
| ⚙️ | **GitHub Actions** | ⚠️ Needs extra steps | 🌐 Public | See below |

**If you are not sure which to use — go with Google Colab.**

---

## ⭐ Method 1 — Google Colab *(Recommended)*

No setup. No account needed other than your DMS. YouTube works perfectly. Your activity is private.

1. Click → [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/patricnilackshan/UoM_DMS_Toolkit/blob/main/UoM_DMS_Toolkit.ipynb)
2. Run the **Sign in** cell — enter your DMS username & password
3. Run **Download**, **Upload**, **Share** cells in order

That's it. Dependencies install automatically on first run.

---

## ⚙️ Method 2 — GitHub Actions

Runs entirely on GitHub — no browser tab needed while downloading. But it has two limitations:

- ⚠️ **YouTube downloads require extra steps** (see Notes below)
- 🌐 **Your workflow logs are publicly visible** — anyone can see what links you downloaded

### How to use it privately

> GitHub does not allow making a fork of a public repository private. Instead, **import** this repo as your own private copy.

1. Go to [github.com/new/import](https://github.com/new/import)
2. Paste the source URL: `https://github.com/patricnilackshan/UoM-DMS-Toolkit`
3. Set visibility to **Private** → click **Begin import**
4. In your new private repo, go to **Settings → Secrets and variables → Actions** and add:
   - `DMS_USERNAME` — your DMS username
   - `DMS_PASSWORD` — your DMS password
5. Go to **Actions** → **Download and Upload to DMS** → **Run workflow**
6. Enter the download link — credentials load from secrets automatically

### Supported link types

| Link | Works |
|---|---|
| Any HTTP/HTTPS direct link | ✅ |
| `*.m3u8` stream | ✅ |
| `magnet:?xt=urn:btih:...` torrent | ✅ |
| `youtube.com` / `youtu.be` | ⚠️ Needs cookies — see Notes |

---

## Notes

### YouTube in GitHub Actions

GitHub Actions runs on datacenter servers that YouTube blocks as bots. You will see:

```
Sign in to confirm you're not a bot.
```

**Fix:** Export your YouTube cookies and give them to the workflow.

**How to export cookies:**
1. Install [Get cookies.txt LOCALLY](https://chromewebstore.google.com/detail/get-cookiestxt-locally/cclelndahbckbenkjhflpdbgdldlbecc) in your browser
2. Go to [youtube.com](https://youtube.com) while signed in
3. Click the extension → export in **Netscape format**

**How to use them:**
- **One-time:** Paste the cookie content into the `youtube_cookies` field when running the workflow
- **Permanent:** Save as a secret named `YOUTUBE_COOKIES` under **Settings → Secrets and variables → Actions** — the workflow picks it up automatically every time

> This issue does **not** affect Google Colab — Colab IPs are not blocked by YouTube.

### Filename Sanitization

Filenames are automatically sanitized before upload — any character outside `[a-zA-Z0-9_.]` (including spaces) is replaced with an underscore.

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
