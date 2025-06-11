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
Run the two commands below to copy the sample environment and config files:
  cp .env.example .env                   # Step 1: Create your environment file
  cp wp-config-sample.php wp-config.php  # Step 2: Set up WordPress config (if not already done)

Open .env and fill in your database credentials and secret key values. You can generate WordPress salts here: https://api.wordpress.org/secret-key/1.1/salt/

If you're using the .env approach, uncomment the dotenv loader lines at the top of wp-config.php.

Make sure Composer is installed, then run: composer install

You're ready to run WordPress locally!

# 4. Database
- Log into MariaDB/MySQL: sudo mysql -u root -p
(Enter the root password you set during mysql_secure_installation.)

- Create the database: 
  CREATE DATABASE zm_reviews4u CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
  EXIT;

- Ensure your MySQL/MariaDB user has privileges on that database (if you’re using a non-root user, grant them):
  sudo mysql -u root -p

- Then inside the MariaDB prompt:
  CREATE USER 'wpuser'@'localhost' IDENTIFIED BY 'StrongDBPass123!';
  GRANT ALL PRIVILEGES ON zm_reviews4u.* TO 'wpuser'@'localhost';
  FLUSH PRIVILEGES;
  EXIT;

(You can keep using root if you like, but creating a dedicated wpuser is a good habit.)

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

## Dependencies

This project uses:
- [WordPress](https://wordpress.org/)
- [phpdotenv](https://github.com/vlucas/phpdotenv) (BSD-3-Clause License)

> These plugins and libraries may not be included in this repo. Please install them manually or via WP dashboard.

## License

*This repository is for academic purposes only.*
