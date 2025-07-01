# Policies - Homestay Booking & Management App

This document defines the **authorization Policies** for the project.  
Policies work with Spatie Laravel Permission to enforce **ownership** and **resource-level checks**.

---

## What are Policies?

- **Policies** in Laravel answer: *“Is this user allowed to perform this action on this specific model?”*
- They handle logic that **roles & permissions alone don’t cover** — like “owns this listing”.
- You use them in controllers via `$this->authorize()` or `Gate::allows()`.

---

## Policies in this Project

| Policy            | Model      | Purpose                                                 |
|-------------------|------------|---------------------------------------------------------|
| **HomestayPolicy** | Homestay   | Owners can manage their own listings. Admin can manage any. |
| **BookingPolicy**  | Booking    | Guests can view or cancel their own bookings. Owners can view bookings for listings they own. Admin can manage any. |
| **PaymentPolicy**  | Payment    | Guests can view their own payments. Admin can manage all payments and process refunds. |

---

## Actions per Policy

### **HomestayPolicy**

| Ability   | Who Can Do This                               |
|-----------|-----------------------------------------------|
| view      | Owner (own listing), Guest (any active listing), Admin (any) |
| create    | Owner, Admin                                  |
| update    | Owner (own listing), Admin (any)              |
| delete    | Owner (own listing), Admin (any)              |
| blockDate | Owner (own listing), Admin (any)              |

---

### **BookingPolicy**

| Ability   | Who Can Do This                                       |
|-----------|-------------------------------------------------------|
| view      | Guest (own booking), Owner (for their listings), Admin (any) |
| create    | Guest                                                 |
| cancel    | Guest (own booking), Admin (any)                      |

---

### **PaymentPolicy**

| Ability   | Who Can Do This               |
|-----------|-------------------------------|
| view      | Guest (own payment), Admin    |
| refund    | Admin                         |

---

## Example Usage

**Example in a controller:**
```php
public function update(Homestay $homestay)
{
    $this->authorize('update', $homestay);
    // ... update logic
}
````

**In Blade views:**

```blade
@can('update', $homestay)
   <a href="{{ route('homestays.edit', $homestay) }}">Edit</a>
@endcan
```

---

## How Policies work with Spatie

* **Spatie handles**: *Can this user do this action in general?* (via `hasRole()` / `can()`)
* **Policies handle**: *Is the user allowed to do this action on this model?*

Example:

* `hasRole('owner') && can('update own homestay')`
* `Policy` then checks: *Does the `homestay` belong to the `user`?*

---

## Where Policies Live

* All Policies are in: `/app/Policies/`
* Register them in: `AuthServiceProvider.php`

Example:

```php
protected $policies = [
    Homestay::class => HomestayPolicy::class,
    Booking::class => BookingPolicy::class,
    Payment::class => PaymentPolicy::class,
];
```

---

## To Do

* [ ] Write HomestayPolicy
* [ ] Write BookingPolicy
* [ ] Write PaymentPolicy
* [ ] Add unit tests for Policies

---

**Reference:**

* [Laravel Authorization](https://laravel.com/docs/authorization)
* [Spatie Laravel Permission](https://spatie.be/docs/laravel-permission)
