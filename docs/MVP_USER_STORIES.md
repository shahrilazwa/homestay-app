# Homestay Booking & Management App - MVP User Stories

This document defines the **core MVP user stories**, each mapped to **roles** and **permissions** (using Spatie Laravel Permission).  

---

## User Roles

- **Admin** — Manages everything: listings, bookings, payments, users.
- **Owner** — Manages *their own* listings and related bookings.
- **Guest** — Searches listings, books stays, pays online.

---

## User Stories

---

### Homestay Management

1. **As an owner**, I want to **create a homestay listing** so that I can offer my property for booking.  
   - **Role:** Owner, Admin  
   - **Permission:** `create homestay`
   - **Acceptance Criteria:** Owner can submit valid info (title, description, location, price) and see it listed.

2. **As an owner**, I want to **upload images** for my listing so that guests can see what my property looks like.  
   - **Role:** Owner, Admin  
   - **Permission:** `update own homestay`
   - **Acceptance Criteria:** Images are stored and displayed in a gallery on the detail page.

3. **As an owner**, I want to **edit or delete my listings** so that I can keep them accurate or remove them if needed.  
   - **Role:** Owner, Admin  
   - **Permissions:** `update own homestay`, `delete own homestay` (`Admin` has `update any`/`delete any`)
   - **Acceptance Criteria:** Owners can edit only their listings; Admins can edit or delete any listing.

4. **As an owner**, I want to **block dates for availability** so that I don’t get bookings when my homestay is not available.  
   - **Role:** Owner, Admin  
   - **Permission:** `manage homestay availability`
   - **Acceptance Criteria:** Dates are blocked on the calendar and guests cannot book those dates.

---

### Booking System

5. **As a guest**, I want to **search homestays by location and date** so that I can find available stays.  
   - **Role:** Guest  
   - **Permission:** `view homestay`
   - **Acceptance Criteria:** Search returns only available listings for the selected date range.

6. **As a guest**, I want to **view homestay details** so that I know what’s included before booking.  
   - **Role:** Guest  
   - **Permission:** `view homestay`
   - **Acceptance Criteria:** Details include images, description, price, amenities, and availability calendar.

7. **As a guest**, I want to **make a booking** for specific dates so that I can reserve my stay.  
   - **Role:** Guest  
   - **Permission:** `create booking`
   - **Acceptance Criteria:** Guest can select dates, provide contact info, and see a booking summary.

8. **As a guest**, I want to **receive a booking confirmation email** so that I know my reservation is secure.  
   - **Role:** Guest  
   - **Permission:** `create booking` (triggers notification)
   - **Acceptance Criteria:** Email contains booking ID, dates, amount paid.

9. **As an owner**, I want to **view all bookings for my homestays** so that I can manage check-ins.  
   - **Role:** Owner, Admin  
   - **Permissions:** `view any booking` (Admin) / `view own booking` (Owner)
   - **Acceptance Criteria:** Owner sees only bookings for their listings.

10. **As a guest**, I want to **cancel my booking** so that I can change my travel plans.  
   - **Role:** Guest  
   - **Permission:** `cancel own booking`
   - **Acceptance Criteria:** Booking status updates and owner is notified.

---

### Payments

11. **As a guest**, I want to **pay for my booking online** so that my reservation is guaranteed.  
   - **Role:** Guest  
   - **Permission:** `make payment`
   - **Acceptance Criteria:** Stripe payment works and status changes to “paid”.

12. **As a guest**, I want to **receive a payment receipt via email** so that I have proof of payment.  
   - **Role:** Guest  
   - **Permission:** `make payment` (triggers receipt)
   - **Acceptance Criteria:** Email includes transaction ID and booking info.

13. **As an admin**, I want to **issue refunds** when necessary so that guests are refunded correctly.  
   - **Role:** Admin  
   - **Permission:** `issue refund`
   - **Acceptance Criteria:** Refund is processed via Stripe and status updates in system.

---

### Users & RBAC

14. **As a guest**, I want to **register and log in** so that I can view my bookings.  
   - **Role:** Guest  
   - **Permission:** `view own booking`
   - **Acceptance Criteria:** Auth works via Laravel Breeze/Jetstream.

15. **As an admin**, I want to **manage user roles** so that I can control who does what.  
   - **Role:** Admin  
   - **Permission:** `assign roles`
   - **Acceptance Criteria:** Admin can assign/remove roles to/from users.

16. **As an admin**, I want to **manage users** so that I can ban or reactivate accounts.  
   - **Role:** Admin  
   - **Permission:** `manage users`
   - **Acceptance Criteria:** Admin sees user list, can deactivate/reactivate.

17. **As an admin**, I want to **view a dashboard** with all listings, bookings, and payments so that I can oversee operations.  
   - **Role:** Admin  
   - **Permissions:** `view any homestay`, `view any booking`, `view any payment`
   - **Acceptance Criteria:** Dashboard aggregates core stats.

---

## Sprint Milestones

| Sprint   | Focus                                              |
|----------|----------------------------------------------------|
| Sprint 0 | Auth setup, install Spatie, seed roles & permissions |
| Sprint 1 | Owner CRUD for homestays & image uploads           |
| Sprint 2 | Guest search & booking flow                        |
| Sprint 3 | Payments (Stripe) + booking confirmation emails    |
| Sprint 4 | Admin dashboard, role management, test RBAC flows  |

---

## Notes

- Use **Spatie’s `@role` & `@can`** Blade directives for conditional UI.
- Apply **middleware** to protect routes by permission.
- Implement **policies** for “own vs any” actions.

---
