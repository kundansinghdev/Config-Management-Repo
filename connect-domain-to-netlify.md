
# 🌐 Connect Your Custom Domain to Netlify — Full Guide (One-Time Setup)

This guide walks you through linking a custom domain (like `thebuilderstudio.in`) to your Netlify site using **Netlify DNS**. No need for CNAMEs, A-records, or manual SSL — Netlify handles it all for you.

---

## 📋 Prerequisites

Before you begin:

- ✅ A Netlify project is already deployed (e.g. `thebuilderstudio.netlify.app`)
- ✅ You own a domain (e.g. `thebuilderstudio.in`)
- ✅ You have login access to your domain registrar (Hostinger, GoDaddy, Namecheap, etc.)

---

## 🪜 Step-by-Step Setup

---

### 1️⃣ Add Your Domain to Netlify

1. Visit 👉 [https://app.netlify.com](https://app.netlify.com)
2. Open your site
3. Go to:  
   **Site Settings → Domain Management → Custom Domains**
4. Click **“Add custom domain”**
5. Enter your domain (e.g. `thebuilderstudio.in`)
6. Click **Verify**, then **Yes, add domain**
7. Set it as the **Primary domain**

---

### 2️⃣ Set Up Netlify DNS

1. Click **“Set up Netlify DNS”**
2. Netlify will show 4 nameservers:

dns1.p09.nsone.net
dns2.p09.nsone.net
dns3.p09.nsone.net
dns4.p09.nsone.net


---

### 3️⃣ Update Nameservers at Your Domain Provider

Login to the registrar where you purchased the domain:

1. Go to:
Domains → Manage → DNS / Nameservers

markdown

2. Locate the **Nameservers** or **Custom DNS** section
3. Replace any existing nameservers with Netlify’s:

dns1.p09.nsone.net
dns2.p09.nsone.net
dns3.p09.nsone.net
dns4.p09.nsone.net


4. Click **Save / Update**

> ⏳ **Note:** It can take up to 24 hours for DNS changes to propagate globally.

---

### 4️⃣ Wait for DNS Propagation

Use this tool to monitor DNS update status:  
🔍 [https://dnschecker.org](https://dnschecker.org)

- Enter your domain: `thebuilderstudio.in`
- Select **NS** (Nameserver) from the dropdown
- Confirm that all 4 Netlify nameservers appear across the globe

---

### 5️⃣ Confirm Setup in Netlify

Once DNS is updated:

- ✅ Netlify will mark the domain as **Verified**
- 🔒 A free SSL certificate will be issued automatically
- 🌍 Your site will be accessible via `https://thebuilderstudio.in`

---

### 6️⃣ www → non-www Auto Redirect (Optional)

Netlify will automatically redirect:

www.thebuilderstudio.in → thebuilderstudio.in


- No CNAME or separate DNS entry is needed
- You can test both URLs in your browser

---

## ⚙️ Troubleshooting Tips

| Problem                          | Solution                                                              |
|----------------------------------|------------------------------------------------------------------------|
| ❌ Still showing old Hostinger page | Wait 15–30 min, then try Incognito mode or different device           |
| ❌ Works in Incognito but not normal | Clear browser cache or flush DNS locally                              |
| ❌ Doesn’t work on mobile          | Switch from WiFi to Mobile Data or reboot network                     |
| ❌ SSL not working                | Give it 30 mins — Netlify auto-generates SSL once DNS is connected    |

---

## 🧹 Flush DNS Cache (If Needed)

**On macOS:**
```bash
sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder
On Windows (CMD):

cmd

ipconfig /flushdns
On Chrome Browser:

Visit chrome://net-internals/#dns

Click Clear host cache

✅ You’re All Set!
Your Netlify site is now live on your custom domain, secured with HTTPS, and fully DNS-managed by Netlify.

📎 Useful Links
Netlify Docs → https://docs.netlify.com/domains-https/custom-domains/

DNS Checker → https://dnschecker.org


