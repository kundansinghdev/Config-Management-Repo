✅ connect-domain-to-netlify.md
md
Copy
Edit
# 🌐 Connect Your Custom Domain to Netlify — Full Guide (One-Time Setup)

This guide helps you link your custom domain (like `thebuilderstudio.in`) to your Netlify project. You'll be using Netlify DNS to fully manage the domain via Netlify — no need for A records, CNAMEs, or SSL setup.

---

## 📋 What You Need Before Starting

- A Netlify project already deployed (e.g. `thebuilderstudio.netlify.app`)
- Access to your domain provider (e.g. Hostinger, GoDaddy, Namecheap, etc.)
- Your custom domain purchased (e.g. `thebuilderstudio.in`)

---

## 🪜 Step-by-Step Setup Process

---

### 1️⃣ Add Your Custom Domain in Netlify

1. Go to [https://app.netlify.com](https://app.netlify.com)
2. Open your project
3. Navigate to:

Site Settings → Domain Management → Custom Domains

markdown
Copy
Edit

4. Click **“Add custom domain”**
5. Enter your domain (e.g. `thebuilderstudio.in`)
6. Click **Verify**, then **Yes, add domain**
7. Set it as the **Primary domain**

---

### 2️⃣ Setup Netlify DNS (Recommended)

After you’ve added the domain:

1. Click **“Set up Netlify DNS”**
2. Netlify will show 4 nameservers like below:

dns1.p09.nsone.net
dns2.p09.nsone.net
dns3.p09.nsone.net
dns4.p09.nsone.net

yaml
Copy
Edit

---

### 3️⃣ Change Nameservers in Your Domain Provider

Login to where you bought your domain (e.g., Hostinger):

1. Go to:
Domains > Manage > DNS / Nameservers

markdown
Copy
Edit
2. Find the **Nameservers** or **Use Custom DNS** section
3. Replace all existing nameservers with the 4 given by Netlify:

dns1.p09.nsone.net
dns2.p09.nsone.net
dns3.p09.nsone.net
dns4.p09.nsone.net

yaml
Copy
Edit

4. Click **Save / Update**

> ⚠️ Important: This change will take time to reflect globally (DNS Propagation)

---

### 4️⃣ Wait for DNS Propagation

DNS changes can take anywhere between 15 minutes to 24 hours.

You can check live DNS status at:
🔍 [https://dnschecker.org](https://dnschecker.org)

- Enter your domain (`thebuilderstudio.in`)
- Select `NS` record type
- You should see all 4 Netlify nameservers appearing worldwide

---

### 5️⃣ Final Check in Netlify

After DNS is updated:

- Netlify will show ✅ **Domain verified**
- SSL certificate (HTTPS) will be automatically enabled
- You can now access your site at `https://thebuilderstudio.in`

---

### 6️⃣ Auto Redirect from www → non-www

- Netlify automatically handles:
www.thebuilderstudio.in → thebuilderstudio.in

yaml
Copy
Edit
- No CNAME or extra DNS settings needed
- You can verify this by visiting both in browser

---

## 📱 Troubleshooting Tips

| Issue                             | Fix                                                                 |
|----------------------------------|----------------------------------------------------------------------|
| ❌ Still showing old Hostinger page | Wait for DNS propagation (up to 24 hrs) or try Incognito mode        |
| ❌ Working in Incognito, not normal | Clear browser DNS cache or flush system DNS cache                    |
| ❌ Not working on mobile          | Mobile network DNS is slower — try restarting network or use 4G data |
| ❌ SSL not working                | Wait 15–30 mins after DNS is fully set — Netlify issues free SSL     |

---

## 🧹 Flush Your DNS Cache (if needed)

**On Mac:**
```bash
sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder
