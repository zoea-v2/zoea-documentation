the erd mermaid code:

---
config:
  layout: elk
---
erDiagram
    user {
        bigint user_id PK
        varchar first_name
        varchar last_name
        varchar email UK
        varchar phone_number
        varchar password_hash
        varchar avatar_url
        varchar default_city
        boolean is_verified
        datetime created_at
        datetime updated_at
    }
    merchant {
        bigint merchant_id PK
        bigint user_id FK "Owner account"
        varchar business_name
        text description
        varchar category "hotel, restaurant, event_venue, tour_operator, shop, service"
        varchar contact_phone
        varchar contact_email
        varchar business_license
        boolean is_verified
        varchar status "pending, active, suspended"
        varchar onboarding_status "pending, in_review, approved, rejected"
        bigint agent_id FK "Referring agent"
        datetime created_at
        datetime updated_at
    }
    agent {
        bigint agent_id PK
        bigint user_id FK
        varchar agent_code UK
        varchar tier "bronze, silver, gold"
        varchar badge "top_performer, certified, elite"
        decimal commission_balance
        decimal total_earnings
        varchar momo_number
        integer leaderboard_rank
        integer successful_referrals
        boolean is_certified
        datetime joined_at
        datetime updated_at
    }
    location {
        bigint location_id PK
        bigint merchant_id FK
        varchar address_line_1
        varchar address_line_2
        varchar city
        varchar district
        varchar neighborhood
        decimal latitude
        decimal longitude
        varchar timezone
    }
    commission {
        bigint commission_id PK
        bigint agent_id FK
        bigint merchant_id FK
        bigint user_id FK
        varchar commission_type "subscription, booking, order"
        decimal amount
        varchar currency
        varchar status "pending, paid"
        bigint related_id "booking_id, order_id, or subscription_id"
        datetime created_at
        datetime updated_at
    }
    leaderboard {
        bigint leaderboard_id PK
        bigint agent_id FK
        varchar period "daily, weekly, monthly"
        integer rank
        integer points
        datetime created_at
    }
    merchant_subscription {
        bigint subscription_id PK
        bigint merchant_id FK
        varchar plan "basic, premium, enterprise"
        date start_date
        date end_date
        varchar status "active, expired, cancelled"
        bigint payment_id FK
        datetime created_at
        datetime updated_at
    }
    order {
        bigint order_id PK
        bigint user_id FK
        bigint listing_id FK
        bigint product_id FK
        integer quantity
        varchar status "pending, confirmed, shipped, delivered, cancelled"
        decimal total_amount
        varchar currency
        bigint payment_id FK
        jsonb shipping_address
        varchar tracking_number
        datetime created_at
        datetime updated_at
    }
    channel_manager_property {
        bigint property_id PK
        bigint merchant_id FK
        varchar ota_id
        varchar ota_name "Booking.com, Airbnb, Expedia"
        varchar sync_status "active, paused, error"
        varchar sync_url
        datetime created_at
        datetime updated_at
    }
    channel_manager_reservation {
        bigint reservation_id PK
        bigint property_id FK
        varchar ota_reservation_id
        varchar source "Zoea, Booking.com, Airbnb, Expedia"
        varchar guest_name
        date checkin_date
        date checkout_date
        varchar room_type
        varchar rate_plan
        varchar status
        decimal total_amount
        varchar currency
        datetime created_at
        datetime updated_at
    }
    saved_location {
        bigint saved_location_id PK
        bigint user_id FK
        varchar city
        varchar district
        varchar neighborhood
        varchar label "Home, Work, Favorite Area"
        datetime created_at
    }
    curated_collection {
        bigint collection_id PK
        varchar title
        text description
        varchar category
        varchar cover_image
        jsonb listing_ids
        boolean is_active
        datetime created_at
        datetime updated_at
    }
    promotion {
        bigint promotion_id PK
        bigint merchant_id FK
        varchar title
        text description
        varchar promotion_type "flash_sale, discount, campaign"
        date start_date
        date end_date
        decimal discount_percent
        decimal discount_amount
        varchar status "active, scheduled, expired"
        datetime created_at
        datetime updated_at
    }
    merchant_analytics {
        bigint analytics_id PK
        bigint merchant_id FK
        integer visits
        integer orders
        integer bookings
        decimal revenue
        varchar period "daily, weekly, monthly"
        datetime created_at
    }
    listing {
        bigint listing_id PK
        bigint merchant_id FK
        bigint location_id FK
        varchar title
        text description
        varchar type "hotel, event, restaurant, tour, product, service"
        jsonb gallery_images
        boolean is_active
        decimal base_price
        <!-- integer min_booking_notice_hours
        integer max_advance_booking_days
        jsonb sercice_config -->
        datetime created_at
        datetime updated_at
    }
        listing_location {
        bigint location_id PK
        bigint listing_id FK
        varchar location_type "primary, branch, service_area, pop_up"
        varchar address
        decimal latitude
        decimal longitude
        jsonb operating_hours
        boolean is_primary
        date start_date
        date end_date
    }
    hotel_room_type {
        bigint room_type_id PK
        bigint listing_id FK
        varchar name
        text description
        integer max_occupancy
        integer total_rooms
        jsonb amenities
        jsonb room_config
        jsonb gallery_images
        datetime created_at
        datetime updated_at
    }
    rate_plan {
        bigint rate_plan_id PK
        bigint room_type_id FK
        varchar name
        varchar board_type "RO, BB, HB, AI"
        boolean is_refundable
        decimal price
        varchar currency
        integer min_stay
        integer max_stay
        jsonb restrictions
        jsonb blackout_dates
        datetime created_at
        datetime updated_at
    }
    event {
        bigint event_id PK
        bigint listing_id FK
        varchar event_name
        datetime event_date
        datetime end_date
        varchar venue_name
        integer total_tickets
        integer available_tickets
        jsonb ticket_tiers
        boolean is_recurring
        datetime created_at
        datetime updated_at
    }
    restaurant_table {
        bigint table_id PK
        bigint listing_id FK
        varchar table_type "indoor, outdoor, private"
        integer capacity
        integer table_count
        integer min_booking_duration_minutes
        datetime created_at
        datetime updated_at
    }
    product {
        bigint product_id PK
        bigint listing_id FK
        varchar product_name
        text description
        integer stock_quantity
        jsonb variants "size, color, etc."
        boolean track_inventory
        decimal price
        varchar currency
        varchar status "active, inactive, out_of_stock"
        datetime created_at
        datetime updated_at
    }
    service_offering {
        bigint service_id PK
        bigint listing_id FK
        varchar service_name
        integer duration_minutes
        integer max_concurrent_customers
        boolean is_available
        decimal price
        datetime created_at
        datetime updated_at
    }
    tour_package {
        bigint tour_id PK
        bigint listing_id FK
        varchar tour_name
        text description
        jsonb images
        jsonb schedule
        jsonb add_ons
        decimal price
        varchar currency
        integer capacity
        integer available_slots
        varchar status
        datetime created_at
        datetime updated_at
    }
    booking {
        bigint booking_id PK
        bigint user_id FK
        bigint listing_id FK
        bigint resource_id "FK to room_type_id, event_id, table_id, etc."
        varchar booking_type "hotel_stay, event_ticket, restaurant, tour, product, service"
        varchar status "pending, confirmed, checked_in, completed, cancelled, no_show"
        datetime start_time
        datetime end_time
        integer quantity
        integer guest_count
        decimal base_amount
        decimal tax_amount
        decimal service_fee
        decimal total_amount
        varchar currency
        jsonb booking_details
        varchar special_requests
        varchar cancellation_reason
        varchar confirmation_code
        datetime created_at
        datetime confirmed_at
        datetime cancelled_at
        datetime updated_at
    }
    booking_participant {
        bigint participant_id PK
        bigint booking_id FK
        varchar full_name
        varchar email
        varchar phone_number
        varchar identification_number
        varchar dietary_restrictions
        boolean is_primary_guest
        boolean checked_in
        datetime checked_in_at
    }
    booking_addon {
        bigint addon_id PK
        bigint booking_id FK
        varchar addon_name
        varchar addon_type "breakfast, airport_pickup, late_checkout, etc."
        decimal price
        integer quantity
        jsonb addon_details
    }
    payment {
        bigint payment_id PK
        bigint user_id FK
        bigint booking_id FK
        bigint order_id FK
        varchar payment_method "irembo_pay, momo, airtel, card"
        varchar payment_type "full, deposit, installment"
        varchar status "pending, processing, completed, failed, refunded"
        decimal amount
        varchar currency
        decimal amount_refunded
        varchar transaction_id
        varchar receipt_url
        boolean is_split_payment
        varchar split_group_id
        varchar payer_name
        varchar payer_email
        varchar payer_phone
        datetime payment_date
        datetime refund_date
        datetime created_at
        datetime updated_at
    }
    payment_split {
        bigint split_id PK
        bigint payment_id FK
        bigint user_id FK
        decimal amount
        varchar status "pending, paid, cancelled"
        varchar share_type "equal, percentage, fixed"
        datetime created_at
        datetime settled_at
    }
    refund {
        bigint refund_id PK
        bigint payment_id FK
        bigint processed_by_user_id FK
        decimal refund_amount
        varchar refund_reason
        varchar status "requested, approved, processed, completed"
        varchar transaction_id
        datetime requested_at
        datetime processed_at
    }
    review {
        bigint review_id PK
        bigint user_id FK
        bigint listing_id FK
        bigint booking_id FK
        bigint order_id FK
        integer rating_overall
        integer rating_quality
        integer rating_value
        integer rating_service
        integer rating_experience
        text comment
        jsonb review_photos
        boolean is_verified
        boolean is_featured
        integer helpful_count
        varchar status "active, flagged, removed"
        datetime created_at
        datetime updated_at
    }
    review_helpful {
        bigint helpful_id PK
        bigint review_id FK
        bigint user_id FK
        datetime created_at
    }
    merchant_reply {
        bigint reply_id PK
        bigint review_id FK
        bigint merchant_id FK
        text reply_text
        boolean is_public
        datetime replied_at
        datetime updated_at
    }
    review_flag {
        bigint flag_id PK
        bigint review_id FK
        bigint user_id FK
        varchar flag_reason "inappropriate, fake, harassment"
        text flag_details
        varchar status "pending, reviewed, resolved"
        datetime created_at
    }
    user_favorite {
        bigint favorite_id PK
        bigint user_id FK
        bigint listing_id FK
        datetime created_at
    }
    user_search_history {
        bigint search_id PK
        bigint user_id FK
        varchar search_query
        jsonb filters
        varchar location
        datetime searched_at
    }
    user ||--o{ booking : "makes"
    user ||--o{ order : "places"
    user ||--o{ review : "writes"
    user ||--o{ payment : "makes"
    user ||--o{ user_favorite : "has"
    user ||--o{ user_search_history : "creates"
    user ||--o{ review_helpful : "marks"
    user ||--o{ review_flag : "creates"
    user ||--o{ merchant : "owns"
    user ||--o{ agent : "is"
    user ||--o{ saved_location : "saves"
    merchant ||--o{ location : "has"
    merchant ||--o{ listing : "owns"
    merchant ||--o{ merchant_reply : "responds_with"
    merchant ||--o{ merchant_subscription : "subscribes_to"
    merchant ||--o{ promotion : "creates"
    merchant ||--o{ merchant_analytics : "has"
    merchant ||--o{ channel_manager_property : "manages"
    merchant }o--|| agent : "onboarded_by"
    agent ||--o{ commission : "earns"
    agent ||--o{ leaderboard : "ranked_in"
    location ||--o{ listing : "located_at"
    listing ||--o{ booking : "receives"
    listing ||--o{ order : "receives"
    listing ||--o{ review : "receives"
    listing ||--o{ user_favorite : "saved_by"
    listing ||--o{ hotel_room_type : "has_rooms"
    listing ||--o{ event : "hosts"
    listing ||--o{ restaurant_table : "has_tables"
    listing ||--o{ product : "sells"
    listing ||--o{ service_offering : "offers"
    listing ||--o{ tour_package : "offers"
     listing ||--o{ listing_location : "has_locations"
    listing }o--o{ curated_collection : "featured_in"
    hotel_room_type ||--o{ rate_plan : "has_pricing"
    booking ||--o{ payment : "has"
    booking ||--o{ booking_participant : "includes"
    booking ||--o{ booking_addon : "includes"
    booking ||--|| review : "generates"
    order ||--o{ payment : "has"
    order ||--|| review : "generates"
    order ||--o{ product : "contains"
    payment ||--o{ payment_split : "can_split_into"
    payment ||--o{ refund : "can_have"
    payment ||--o{ merchant_subscription : "covers"
    channel_manager_property ||--o{ channel_manager_reservation : "receives"
    review ||--o{ review_helpful : "receives"
    review ||--o{ merchant_reply : "receives"
    review ||--o{ review_flag : "can_be_flagged"
