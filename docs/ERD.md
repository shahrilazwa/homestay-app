[User]
- id (PK)
- name
- email
- password
- role (guest, owner, admin)
- timestamps

[Homestay]
- id (PK)
- user_id (FK → User.id) // Owner
- title
- description
- location
- nightly_rate
- cover_image
- timestamps

[HomestayImage]
- id (PK)
- homestay_id (FK → Homestay.id)
- file_path
- timestamps

[Booking]
- id (PK)
- user_id (FK → User.id) // Guest
- homestay_id (FK → Homestay.id)
- check_in_date
- check_out_date
- total_amount
- payment_status (paid, pending)
- timestamps

[BlockedDate]
- id (PK)
- homestay_id (FK → Homestay.id)
- date
- reason (optional)
- timestamps

[Payment]
- id (PK)
- booking_id (FK → Booking.id)
- amount
- status
- payment_gateway
- transaction_id
- timestamps
