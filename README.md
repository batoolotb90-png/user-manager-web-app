# 🌐 User Manager – Web App

A simple PHP + MySQL web app that lets you add users, view them in a table, and toggle their status live — no page reload needed.

---

## 📁 Project Files

| File | Purpose |
|------|---------|
| `index.php` | Main page (HTML + CSS + JS + PHP combined) |
| `config.php` | Database connection settings |
| `add_user.php` | API endpoint – inserts a new user |
| `get_users.php` | API endpoint – returns all users as JSON |
| `toggle_status.php` | API endpoint – flips a user's status (0↔1) |
| `setup.sql` | SQL script to create the `users` table |

---

## 🚀 How to Deploy on InfinityFree (Step by Step)

### Step 1 – Create a Free Hosting Account
1. Go to [https://infinityfree.com](https://infinityfree.com)
2. Register a free account
3. Create a new hosting account (you get a free subdomain like `yourname.infinityfreeapp.com`)

### Step 2 – Create the MySQL Database
1. In the InfinityFree Control Panel, click **MySQL Databases**
2. Create a new database — note the **Database Name**, **Username**, and **Password**
3. Click **phpMyAdmin** to open the database manager
4. Select your database from the left sidebar
5. Click the **SQL** tab at the top
6. Paste the contents of `setup.sql` and click **Go**

This creates the `users` table with columns: `id`, `name`, `age`, `status`.

### Step 3 – Edit config.php with Your Credentials
Open `config.php` and replace the placeholder values:

```php
define('DB_HOST', 'sql.infinityfree.com');   // Leave as-is
define('DB_USER', 'epiz_XXXXXXX');            // Your DB username (from Step 2)
define('DB_PASS', 'your_password_here');      // Your DB password
define('DB_NAME', 'epiz_XXXXXXX_mydb');      // Your DB name
```

> ⚠️ InfinityFree usernames usually start with `epiz_`

### Step 4 – Upload Files via File Manager
1. In the Control Panel, open **Online File Manager**
2. Navigate to the `htdocs` folder (this is your public web root)
3. Upload all 6 project files:
   - `index.php`
   - `config.php`
   - `add_user.php`
   - `get_users.php`
   - `toggle_status.php`
   - `setup.sql` (optional, just for reference)

### Step 5 – Test Your Website
Visit your subdomain, e.g.:
```
http://yourname.infinityfreeapp.com/index.php
```
You should see the form and the empty table. Try adding a user!

---

## 💻 How to Upload to GitHub

### Step 1 – Install Git
Download from [https://git-scm.com](https://git-scm.com) and install it.

### Step 2 – Create a GitHub Repository
1. Go to [https://github.com](https://github.com) and log in
2. Click the **+** icon → **New repository**
3. Name it `user-manager` (or any name you like)
4. Choose **Public**
5. Click **Create repository**

### Step 3 – Initialize Git Locally
Open a terminal (or Git Bash on Windows) in your project folder:

```bash
# Navigate to your project folder
cd path/to/your/webapp

# Initialize git
git init

# Add all files
git add .

# First commit
git commit -m "Initial commit: User Manager web app"
```

### Step 4 – Connect to GitHub and Push
Copy the repository URL from GitHub (looks like `https://github.com/yourusername/user-manager.git`), then:

```bash
# Connect local repo to GitHub
git remote add origin https://github.com/yourusername/user-manager.git

# Push your code
git branch -M main
git push -u origin main
```

### Step 5 – Verify on GitHub
Go to your repository URL on GitHub — you should see all your files listed there.

---

## ⚙️ How the App Works

### Adding a User
1. User types Name + Age and clicks **Submit**
2. JavaScript sends a `POST` request to `add_user.php` (no page reload)
3. PHP validates the input, inserts it into MySQL
4. JavaScript receives the response and adds the new row directly to the table

### Toggling Status
1. User clicks **Toggle** next to any row
2. JavaScript sends a `POST` request to `toggle_status.php` with the user's ID
3. PHP runs `UPDATE users SET status = IF(status=0,1,0) WHERE id = ?`
4. JavaScript updates the badge color and number instantly (0 = red, 1 = green)

---

## 🛠️ Technologies Used

| Layer | Technology |
|-------|-----------|
| Structure | HTML5 |
| Styling | CSS3 (no frameworks) |
| Interactivity | Vanilla JavaScript (Fetch API) |
| Backend | PHP 7+ |
| Database | MySQL (via MySQLi) |
| Hosting | InfinityFree (free PHP+MySQL hosting) |