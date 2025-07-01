# Homestay Booking & Management App

A Laravel-based web app to manage homestay listings, handle bookings, and process payments.

## MVP Features

- Create & manage homestay listings (CRUD)
- Upload photos
- Search & filter available homestays
- Booking system with availability calendar
- Online payments via Stripe
- Guest, owner, and admin accounts
- Role-based access control (RBAC) using Spatie Laravel Permission
- Admin dashboard
- Email notifications

## Folder Structure

```
/docs/
MVP\_USER\_STORIES.md
WIREFRAMES/
ERD/
/resources/designs/   # Optional for UI files
/routes/
/app/
/database/
/tests/
```

## Tech Stack

- **Framework:** Laravel
- **Auth:** Laravel Breeze/Jetstream
- **RBAC:** [Spatie Laravel Permission](https://spatie.be/docs/laravel-permission)
- **Payments:** Stripe API
- **Database:** MySQL / MariaDB
- **Email:** Laravel Notifications (Mail)
- **Deployment:** TBD (Laravel Forge, shared hosting, etc.)

## Documents

- `/docs/MVP_USER_STORIES.md`
- `/docs/WIREFRAMES/`
- `/docs/ERD/`
- `/docs/ERD/HomestayERD-Spatie.png`

## ERD Preview

![ERD Diagram](/docs/ERD/HomestayERD-Spatie.png)

## Role-Based Access Control (RBAC)

This project uses [Spatie Laravel Permission](https://spatie.be/docs/laravel-permission) for flexible roles and permissions.

**Basic setup:**

1. Install:
```bash
   composer require spatie/laravel-permission
````

2. Publish config and run migrations:

```bash
   php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
   php artisan migrate
```

3. Add `HasRoles` trait to `User` model:

```php
   use Spatie\Permission\Traits\HasRoles;

   class User extends Authenticatable
   {
       use HasRoles;
   }
```

4. Seed your roles & permissions in a database seeder:

```php
   Role::create(['name' => 'admin']);
   Role::create(['name' => 'owner']);
   Role::create(['name' => 'guest']);
```

## Getting Started

1. Clone the repo:
```bash
   git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
````

2. Install dependencies:

```bash
   composer install
   npm install && npm run dev
```

3. Set up `.env`:

```bash
   cp .env.example .env
   php artisan key:generate
```

4. Run migrations:

```bash
   php artisan migrate
```

5. Start local server:

```bash
   php artisan serve
```

## Roadmap

* [x] Define MVP user stories
* [ ] Set up auth & RBAC (Spatie)
* [ ] Build CRUD for listings
* [ ] Implement image uploads
* [ ] Search & filter bookings
* [ ] Booking system & calendar
* [ ] Stripe payment integration
* [ ] Email notifications
* [ ] Testing & deployment

## Contributing

This is a personal project but feedback is welcome!
Open an issue or suggest improvements.

## License

MIT — feel free to fork & adapt.
