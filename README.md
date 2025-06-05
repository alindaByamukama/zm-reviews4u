# ZM-Reviews4U

**A WordPress-powered review site for music, movies & video games**  
Built for the UU-MWD-510-ZM Content Management assignment.

---

## 🚀 Project Overview
*Plugins and themes are subject to availability of a free tier*
- **Content types**: Movie, Music, Video Game reviews (with 1–5 star ratings via YASR)  
- **SEO & Security**: Rank Math SEO | All-In-One WP Security & Firewall  
- **Theme**: Blocksy (Customizer & block-editor-ready)
- **User roles**: Admin, Editor, Author, Contributor (guest), Subscriber  
- **Functionality**: Featured images, external-link popouts, site-wide search, contact form
 
---

## 📄 Assignment Deliverables

| Item                           | Location / How provided                             |
| ------------------------------ | --------------------------------------------------- |
| **Sitemap diagram (PDF/JPEG)** | `zm-reviews4u-sitemap.pdf`                          |
| **Exported site + DB**         | ZIP files *(not in Git)*               |
| **User credentials**           | `credentials.pdf` (lists all roles)  *(not in Git)* |


## 📋 Prerequisites

- PHP 7.4+, MySQL/MariaDB, Apache/Nginx  
- WP-CLI _or_ Composer  
- Git & GitHub account  

---

## 🛠️ Installation

```bash
# 1. Clone
git clone https://github.com/<your-username>/zm-reviews4u.git
cd zm-reviews4u

# 2. Download WordPress core (choose WP-CLI *or* Composer)
wp core download               # via WP-CLI
# or: composer create-project johnpbloch/wordpress .

# 3. Configure environment
cp .env.example .env           # fill in DB creds, salts
cp wp-config-sample.php wp-config.php  # or load from .env

# 4. Database
mysql -u root -p \
  -e "CREATE DATABASE zm_reviews4u CHARSET utf8mb4 COLLATE utf8mb4_unicode_ci;"
wp db import database/zm_reviews4u-schema.sql

# 5. Activate child theme & plugins
wp theme activate zm-child-theme
wp plugin activate yasr wordpress-seo wordfence wpforms-lite

# 6. Create demo users
# Admin set during wp install 
wp user create editor  editor@example.com --role=editor  --user_pass=Passw0rd!
wp user create author  author@example.com --role=author  --user_pass=Passw0rd!
wp user create guest   guest@example.com  --role=contributor --user_pass=Passw0rd!
wp user create viewer  viewer@example.com --role=subscriber --user_pass=Passw0rd!

# 7. Browse
open http://localhost/zm-reviews4u/wp-admin

```
**Note**: 
- For Windows/XAMPP, place the repo in C:\xampp\htdocs\zm-reviews4u\
- For WSL2 or Linux, serve from /var/www/html/zm-reviews4u.

## 📑 Repository Structure

```bash
zm-reviews4u/
├─ wp-content/
│  ├─ themes/
│  │  └─  Blocksy             # Customizer & block-editor-ready
│  └─ plugins/                # Third-party plugins tracked via Composer or ZIP
├─ database/
│  └─ zm_reviews4u-schema.sql # Minimal schema dump
├─ .env.example               # Environment variables template
├─ wp-config-sample.php
├─ .gitignore
├─ README.md
└─ composer.json              # (if using Composer)
```

---

## 👥 Contributing

1. Fork & clone your fork.
2. Create a feature branch: `git checkout -b feature/awesome`
3. Commit early & often, then open a PR against `main`.

---

## ZM-Reviews4U Sitemap

Home  (header: Menu | Search)
├─ Latest / All Reviews   (home feed)
├─ Movies
│   ├─ Genre Tag Archive
│   └─ Individual Movie Review
├─ Music
│   ├─ Genre Tag Archive
│   └─ Individual Music Review
├─ Video Games
│   ├─ Genre / Platform Tag Archive
│   └─ Individual Video-Game Review
├─ Submit a Review
│   └─ Login / Register   (Contributor account)
├─ Contact Us
├─ About
├─ HTML Sitemap  (user)
└─ User Profile / Dashboard
     └─ Login / Register   (Subscriber)


## License

*This repository is for academic purposes only.*
