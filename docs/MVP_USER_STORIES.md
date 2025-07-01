# Homestay Booking & Management App - MVP User Stories

This document defines the core user stories for the MVP.

---

## User Stories with Tasks & Acceptance Criteria

### Manage Homestays

1. **As an admin/owner, I want to create a homestay listing**
   - **Tasks:**
     - Add homestays table migration.
     - Create listing form (title, description, price, location).
     - Add image upload field.
   - **Acceptance Criteria:**
     - Owner can submit valid info and see the listing in the system.

2. **As an admin/owner, I want to upload images**
   - **Tasks:**
     - Integrate image upload with storage (local or S3).
     - Display images on the listing page.
   - **Acceptance Criteria:**
     - Images are shown in gallery format; thumbnails display correctly.

3. **As an admin/owner, I want to edit or delete listings**
   - **Tasks:**
     - Create edit & delete routes/controllers.
     - Add confirmation for deletion.
   - **Acceptance Criteria:**
     - Changes update correctly; deleted listings disappear from search.

4. **As an admin/owner, I want to set nightly prices and manually block dates**
   - **Tasks:**
     - Add price field and calendar.
     - Allow admin to mark dates unavailable.
   - **Acceptance Criteria:**
     - Blocked dates cannot be booked.

---

### Booking System

5. **As a guest, I want to search homestays by location and date**
   - **Tasks:**
     - Build search form with filters.
     - Connect search to listings DB.
   - **Acceptance Criteria:**
     - Only available listings show for selected dates.

6. **As a guest, I want to view a homestay’s details**
   - **Tasks:**
     - Create listing detail page.
     - Display all info: images, description, price, availability.
   - **Acceptance Criteria:**
     - Page loads with accurate data.

7. **As a guest, I want to make a booking for specific dates**
   - **Tasks:**
     - Build booking form.
     - Validate date range & guest info.
     - Store booking in DB.
   - **Acceptance Criteria:**
     - Valid booking creates reservation and reduces availability.

8. **As a guest, I want to receive a booking confirmation email**
   - **Tasks:**
     - Set up mail config.
     - Trigger email on booking creation.
   - **Acceptance Criteria:**
     - Email contains booking details.

9. **As an admin/owner, I want to see all bookings in a calendar view**
   - **Tasks:**
     - Add bookings table migration.
     - Create calendar UI.
     - Link bookings to dates.
   - **Acceptance Criteria:**
     - Calendar shows booked/unavailable dates per listing.

---

### Payment

10. **As a guest, I want to pay for my booking online**
    - **Tasks:**
      - Integrate Stripe or chosen gateway.
      - Create checkout page.
    - **Acceptance Criteria:**
      - Successful payment marks booking as paid.

11. **As a guest, I want to receive a payment receipt via email**
    - **Tasks:**
      - Extend email logic to include payment receipt.
    - **Acceptance Criteria:**
      - Email includes transaction ID, amount, booking details.

---

### User & Admin

12. **As a guest, I want to register and log in**
    - **Tasks:**
      - Use Laravel Breeze/Jetstream for auth.
    - **Acceptance Criteria:**
      - Guests can sign up, log in, log out.

13. **As an admin/owner, I want to log in to an admin dashboard**
    - **Tasks:**
      - Create separate admin route/middleware.
      - Dashboard shows listings and bookings.
    - **Acceptance Criteria:**
      - Only admin/owner can access dashboard.

14. **As an admin/owner, I want to get notifications of new bookings**
    - **Tasks:**
      - Trigger email notification on new booking.
    - **Acceptance Criteria:**
      - Admin receives email with booking info.

---

### 📨 Notifications

15. **As a guest, I want to get reminders for upcoming stays**
    - **Tasks:**
      - Schedule email reminders (optional for MVP).
    - **Acceptance Criteria:**
      - Guests receive reminder X days before check-in.

---

## Suggested Sprint Milestones

| Sprint | Focus                                             |
|--------|---------------------------------------------------|
| Sprint 1 | Auth & basic admin dashboard                    |
| Sprint 2 | CRUD for listings + image uploads               |
| Sprint 3 | Search, view listings, booking form             |
| Sprint 4 | Payments integration + email notifications      |
| Sprint 5 | Booking calendar for admin, polish & test       |

---

