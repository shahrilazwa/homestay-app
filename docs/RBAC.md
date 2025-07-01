# RBAC - Roles & Permissions

This document outlines how we manage **Role-Based Access Control (RBAC)** using [Spatie Laravel Permission](https://spatie.be/docs/laravel-permission) for the Homestay Booking & Management App.

## Roles

| Role  | Description                                               |
|-------|-----------------------------------------------------------|
| Admin | Has full access to manage users, listings, bookings, payments. |
| Owner | Manages their own homestay listings and related bookings. |
| Guest | Can search listings, make bookings, and manage their own bookings. |

## Planned Permissions

Here’s a breakdown of **permissions** grouped by functional area.

### Homestays

| Permission                      | Roles with this Permission  |
|---------------------------------|-----------------------------|
| create homestay                 | Admin, Owner                |
| view homestay                   | Admin, Owner, Guest         |
| update own homestay             | Owner                       |
| update any homestay             | Admin                       |
| delete own homestay             | Owner                       |
| delete any homestay             | Admin                       |
| manage homestay availability    | Owner, Admin                |

### Bookings

| Permission                      | Roles with this Permission  |
|---------------------------------|-----------------------------|
| create booking                  | Guest                       |
| view own booking                | Guest                       |
| cancel own booking              | Guest                       |
| view any booking                | Admin, Owner                |
| update booking status           | Admin                       |


### Payments

| Permission                      | Roles with this Permission  |
|---------------------------------|-----------------------------|
| make payment                    | Guest                       |
| view own payment                | Guest                       |
| view any payment                | Admin                       |
| issue refund                    | Admin                       |

### Users & Admin

| Permission                      | Roles with this Permission  |
|---------------------------------|-----------------------------|
| manage users                    | Admin                       |
| assign roles                    | Admin                       |
| view dashboard                  | Admin, Owner                |

## Example Usage

**Guests** can:
- Search listings
- Book stays
- Pay online
- View or cancel their own bookings

**Owners** can:
- Create/edit/delete *their* listings
- Block dates for availability
- View bookings for *their* homestays only

**Admins** can:
- Manage all listings, bookings, and payments
- Manage users & assign roles
- View all data

---

## Notes

- Use Laravel **policies** or **gates** to enforce “own vs any” rules.
- Add middleware like `->middleware('role:admin')` or `->middleware('permission:create homestay')` on your routes/controllers.
- Use Spatie’s `@can` and `@role` Blade directives for frontend checks.

---

## 📝 To Do

- [ ] Implement database seeder for roles & permissions.
- [ ] Write unit tests for roles & permissions.
- [ ] Document any custom policies in `/docs/POLICIES.md`.

---

**Source:** [Spatie Laravel Permission Docs](https://spatie.be/docs/laravel-permission)

---
