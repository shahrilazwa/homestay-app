# Homestay Booking & Management App

A Laravel-based web app to manage homestay listings, handle bookings, and process payments.

## MVP Features

- Create & manage homestay listings (CRUD)
- Upload photos
- Search & filter available homestays
- Booking system with availability calendar
- Online payments via Stripe
- Guest & owner accounts
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
- **Payments:** Stripe API
- **Database:** MySQL / MariaDB
- **Email:** Laravel Notifications (Mail)
- **Deployment:** TBD (Laravel Forge, shared hosting, etc.)

## Documents

- `/docs/MVP_USER_STORIES.md`
- `/docs/WIREFRAMES/`
- `/docs/ERD/`

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
* [ ] Set up auth & roles
* [ ] Build CRUD for listings
* [ ] Booking system & calendar
* [ ] Stripe payment integration
* [ ] Email notifications
* [ ] Testing & deployment

## Contributing

This is a personal project but feedback is welcome!
Open an issue or suggest improvements.

## License

MIT — feel free to fork & adapt.
