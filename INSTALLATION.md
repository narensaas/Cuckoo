# Installation Guide

## Prerequisites

Before you begin, ensure you have the following installed:

- **PHP** 8.2 or higher
- **Composer** (latest version)
- **Node.js** 18+ and NPM
- **MySQL** 8.0+ or **PostgreSQL** 14+
- **Redis** (for queues and caching)
- **Git**

### PHP Extensions Required:
```bash
php -m | grep -E 'pdo|mysql|mbstring|xml|ctype|json|bcmath|fileinfo|gd|zip'
```

Required extensions:
- PDO
- pdo_mysql (or pdo_pgsql for PostgreSQL)
- mbstring
- xml
- ctype
- json
- bcmath
- fileinfo
- gd
- zip

## Step-by-Step Installation

### 1. Clone the Repository

```bash
git clone <your-repository-url> cuckoo-pm
cd cuckoo-pm
```

### 2. Install PHP Dependencies

```bash
composer install
```

This will install:
- Laravel 11.46.1
- FilamentPHP 3.3.45
- Filament Shield 3.9.10
- Spatie Media Library 11.17.5
- Spatie Laravel Settings 3.5.0
- Spatie Activity Log 4.10.2
- And all their dependencies

### 3. Install Node Dependencies

```bash
npm install
```

### 4. Environment Configuration

Copy the example environment file:

```bash
cp .env.example .env
```

Generate application key:

```bash
php artisan key:generate
```

### 5. Configure Database

Edit `.env` file and configure your database connection:

#### For MySQL:
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=cuckoo_pm
DB_USERNAME=your_username
DB_PASSWORD=your_password
```

#### For PostgreSQL:
```env
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=cuckoo_pm
DB_USERNAME=your_username
DB_PASSWORD=your_password
```

### 6. Create Database

#### MySQL:
```bash
mysql -u root -p
CREATE DATABASE cuckoo_pm CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
EXIT;
```

#### PostgreSQL:
```bash
psql -U postgres
CREATE DATABASE cuckoo_pm;
\q
```

### 7. Run Migrations

```bash
php artisan migrate
```

This will create:
- User tables (Laravel default)
- Permission tables (Filament Shield / Spatie Permission)
- Media library tables (Spatie Media Library)
- Activity log tables (Spatie Activity Log)
- Cache and jobs tables

### 8. Install Filament Shield

Generate Shield permissions and resources:

```bash
php artisan shield:install
```

When prompted:
- Select "Yes" to generate all policies
- Select "Yes" to generate Super Admin role

Generate permissions for all resources:

```bash
php artisan shield:generate --all
```

### 9. Create Super Admin User

```bash
php artisan shield:super-admin
```

You'll be prompted to enter:
- Name
- Email
- Password

This user will have full access to all modules.

### 10. Publish Spatie Configs (Optional)

If you want to customize Spatie package configurations:

```bash
# Media Library
php artisan vendor:publish --provider="Spatie\MediaLibrary\MediaLibraryServiceProvider" --tag="config"

# Activity Log
php artisan vendor:publish --provider="Spatie\Activitylog\ActivitylogServiceProvider" --tag="config"

# Settings
php artisan vendor:publish --provider="Spatie\LaravelSettings\LaravelSettingsServiceProvider"
```

### 11. Create Storage Link

```bash
php artisan storage:link
```

This creates a symbolic link from `public/storage` to `storage/app/public` for file uploads.

### 12. Build Frontend Assets

For development:
```bash
npm run dev
```

For production:
```bash
npm run build
```

### 13. Start Development Server

```bash
php artisan serve
```

The application will be available at: `http://127.0.0.1:8000`

### 14. Access Admin Panel

Navigate to: `http://127.0.0.1:8000/admin`

Login with the super admin credentials you created in step 9.

## Additional Configuration

### Queue Configuration

For production, configure Redis queue:

```env
QUEUE_CONNECTION=redis

REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379
```

Start queue worker:
```bash
php artisan queue:work --tries=3
```

For development, you can use database queue:
```env
QUEUE_CONNECTION=database
```

### Mail Configuration

Configure mail settings in `.env`:

```env
MAIL_MAILER=smtp
MAIL_HOST=smtp.mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=your_username
MAIL_PASSWORD=your_password
MAIL_ENCRYPTION=tls
MAIL_FROM_ADDRESS=noreply@cuckoo-pm.com
MAIL_FROM_NAME="${APP_NAME}"
```

### File Storage

For local storage (development):
```env
FILESYSTEM_DISK=local
```

For S3 storage (production):
```env
FILESYSTEM_DISK=s3
AWS_ACCESS_KEY_ID=your_key
AWS_SECRET_ACCESS_KEY=your_secret
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=your_bucket_name
```

### Application Settings

Update in `.env`:

```env
APP_NAME="Cuckoo PM"
APP_URL=http://your-domain.com
APP_ENV=production
APP_DEBUG=false
```

## Verification

### 1. Check Installation

```bash
php artisan about
```

This shows your Laravel installation details.

### 2. Test Database Connection

```bash
php artisan tinker
>>> DB::connection()->getPdo();
```

Should return PDO instance without errors.

### 3. Check Filament Installation

Navigate to `/admin` - you should see the Filament login page.

### 4. Verify Permissions

After logging in as super admin, navigate to:
- Admin → Shield → Roles
- Admin → Shield → Permissions

You should see the Super Admin role and all generated permissions.

## Troubleshooting

### Issue: "Class not found" errors
**Solution:**
```bash
composer dump-autoload
php artisan config:clear
php artisan cache:clear
```

### Issue: "Permission denied" on storage
**Solution:**
```bash
chmod -R 775 storage bootstrap/cache
chown -R www-data:www-data storage bootstrap/cache
```

### Issue: Assets not loading
**Solution:**
```bash
npm run build
php artisan filament:assets
```

### Issue: Database connection failed
**Solution:**
- Verify database credentials in `.env`
- Ensure database server is running
- Check if database exists
- Verify PHP PDO extension is installed

### Issue: Filament Shield not showing
**Solution:**
```bash
php artisan shield:install --fresh
php artisan shield:generate --all
php artisan config:clear
```

## Default Roles

After installation, these roles will be available:

1. **Super Admin** - Full system access (created during setup)
2. **Admin** - Administrative access (auto-generated by Shield)
3. **panel_user** - Basic panel access (auto-generated by Shield)

You'll need to create custom roles for:
- Project Manager
- Developer
- QA
- Freelancer
- Finance

(These will be added in Phase 2)

## Next Steps

After successful installation:

1. ✅ Read `NEXT_STEPS.md` for development roadmap
2. ✅ Review `README.md` for feature specifications
3. ✅ Start Phase 2: Database schema and models
4. ✅ Create custom roles and permissions
5. ✅ Build Filament resources

## Development Commands

Useful commands during development:

```bash
# Clear all caches
php artisan optimize:clear

# Run tests
php artisan test

# Code formatting
./vendor/bin/pint

# Database reset (⚠️ deletes all data)
php artisan migrate:fresh --seed

# Create new migration
php artisan make:migration create_projects_table

# Create new model
php artisan make:model Project -m

# Create Filament resource
php artisan make:filament-resource Project

# Generate Shield permissions for specific resource
php artisan shield:generate --resource=ProjectResource
```

## Production Deployment

For production deployment:

1. Set `APP_ENV=production` and `APP_DEBUG=false`
2. Use Redis for cache and queue
3. Configure proper database backups
4. Setup SSL certificate
5. Configure web server (Nginx/Apache)
6. Setup supervisor for queue workers
7. Enable OPcache
8. Use CDN for assets (optional)
9. Setup monitoring (Laravel Telescope, Sentry, etc.)

## Support

For issues or questions:
- Check documentation in `README.md`
- Review Laravel docs: https://laravel.com/docs
- Review Filament docs: https://filamentphp.com/docs
- Review Filament Shield docs: https://github.com/bezhanSalleh/filament-shield

---

**Installation complete!** 🎉

You're ready to start Phase 2: Building the project management system.
