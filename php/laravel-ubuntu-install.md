To run a Laravel project on Ubuntu Desktop, you need to follow these steps to set up your environment and get the project running.

### 1. Install Required Software

Before running Laravel, you need to install a few tools and dependencies on your Ubuntu system:

- **PHP**: Laravel is a PHP framework, so you’ll need PHP installed.
- **Composer**: Composer is a dependency manager for PHP and is required to install Laravel dependencies.
- **Web Server (Apache or Nginx)**: Laravel can run with either Apache or Nginx, but Apache is commonly used.
- **Database (MySQL or SQLite)**: Laravel uses a database, so you’ll need to install MySQL or SQLite.

Here’s a step-by-step guide:

### 2. Update the System
First, make sure your system is up to date:
```bash
sudo apt update && sudo apt upgrade
```

### 3. Install PHP and Extensions
Laravel 10 requires PHP 8.1 or higher, along with some common PHP extensions. You can install them with the following commands:

```bash
sudo apt install php php-cli php-fpm php-mbstring php-xml php-bcmath php-json php-zip php-mysql php-curl php-imagick
```

### 4. Install Composer
You need Composer to manage Laravel's dependencies.

Run the following commands to download and install Composer:

```bash
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
```

To verify that Composer is installed:

```bash
composer --version
```

### 5. Install MySQL or SQLite
Laravel supports several databases, but MySQL is the most commonly used with Laravel. To install MySQL:

```bash
sudo apt install mysql-server
sudo mysql_secure_installation
```

To set the password for the root user in the latest Ubuntu.

First access mysql as superuser with::

```bash
$ sudo mysql -u root
```

Then just update the login plugin and grant the “grant” to the root user with the following SQL:

```bash
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'senha-de-root';
```

Update privileges with the query:

```bash
FLUSH PRIVILEGES;
```

Exit mysql with a **\q** and test with the command:

```bash
 mysql -u root -p
```

If you're using SQLite, you don't need to install anything extra for the database, as SQLite is built into PHP.

### 6. Install Apache or Nginx (Optional)
If you want to use Apache, install it with:

```bash
sudo apt install apache2
```

To install PHP support for Apache:

```bash
sudo apt install libapache2-mod-php
```

After installing Apache, enable the `mod_rewrite` module:

```bash
sudo a2enmod rewrite
```

Restart Apache to apply the changes:

```bash
sudo systemctl restart apache2
```

If you prefer Nginx, you can install it by:

```bash
sudo apt install nginx
```

### 7. Download or Clone Your Laravel Project and Permissions
Permission
```bash
$ cd /var/www/html/
/var/www/html$ sudo chmod -R 777 .
```

Navigate to the folder where you want to store your Laravel project:

```bash
cd /var/www
```

Clone your Laravel project from GitHub or download it:

```bash
git clone https://github.com/your-username/your-laravel-project.git
cd your-laravel-project
```

Alternatively, if you already have a Laravel project, navigate to its directory:

```bash
cd /path/to/your/project
```

### 8. Install Laravel Dependencies
Run Composer to install Laravel’s dependencies:

```bash
composer install
```

### 9. Set Up the .env File
Laravel uses the `.env` file for configuration. If it doesn't exist, create it by copying `.env.example`:

```bash
cp .env.example .env
```

Now, open the `.env` file and configure your database connection and other settings.

For MySQL, you’ll need to set the following:

```ini
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=your_database_name
DB_USERNAME=your_database_user
DB_PASSWORD=your_database_password
```

For SQLite, just set:

```ini
DB_CONNECTION=sqlite
DB_DATABASE=/path/to/database/database.sqlite
```

### 10. Generate Application Key
Run the following command to generate the application key:

```bash
php artisan key:generate
```

### 11. Run Migrations (If Required)
If your project has database migrations, you can run them with:

```bash
php artisan migrate
```

### 12. Set Directory Permissions
Make sure the storage and bootstrap cache directories are writable by the web server:

```bash
sudo chmod -R 775 storage bootstrap/cache
sudo chown -R www-data:www-data storage bootstrap/cache
```

### 13. Configure Apache or Nginx to Serve the Laravel Project
If you're using Apache, create a virtual host configuration for your Laravel project. Here’s an example for Apache:

Create a new config file:

```bash
sudo nano /etc/apache2/sites-available/your-laravel-project.conf
```

Add the following content:

```apache
<VirtualHost *:80>
    ServerName your-laravel-project.local
    DocumentRoot /var/www/your-laravel-project/public

    <Directory /var/www/your-laravel-project/public>
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

Enable the site and restart Apache:

```bash
sudo a2ensite your-laravel-project.conf
sudo systemctl restart apache2
```

If you’re using Nginx, you need to set up a server block. Here’s an example Nginx config:

```nginx
server {
    listen 80;
    server_name your-laravel-project.local;
    root /var/www/your-laravel-project/public;

    index index.php index.html index.htm;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }
}
```

Enable the site and restart Nginx:

```bash
sudo ln -s /etc/nginx/sites-available/your-laravel-project.conf /etc/nginx/sites-enabled/
sudo systemctl restart nginx
```

### 14. Add Local Domain (Optional)
To access your project via a local domain (`your-laravel-project.local`), edit your `/etc/hosts` file:

```bash
sudo nano /etc/hosts
```

Add the following line:

```bash
127.0.0.1   your-laravel-project.local
```

### 15. Run the Laravel Development Server (Optional)
If you don’t want to use Apache or Nginx, you can run Laravel’s built-in development server:

```bash
php artisan serve
```

By default, this will make your project accessible at `http://127.0.0.1:8000`.

### 16. Open the Project in Your Browser
Visit `http://your-laravel-project.local` (or `http://127.0.0.1:8000` if using `php artisan serve`) to see your Laravel project in action.

---

### Troubleshooting

- **Permission Issues**: If you encounter issues related to file permissions, make sure the `storage` and `bootstrap/cache` directories are writable by the web server user (`www-data`).
- **Database Connection**: Make sure that your database is running and that the credentials in the `.env` file are correct.
- **Apache/Nginx Not Working**: Double-check the configuration files and ensure your virtual host/server block is set correctly.

By following these steps, you should be able to set up and run a Laravel project on your Ubuntu desktop.
