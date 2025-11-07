# Zoea V2 API Documentation

## Table of Contents
- [Authentication & Users](#authentication--users)
- [Merchant Management](#merchant-management)
- [Agent System](#agent-system)
- [Listings & Inventory](#listings--inventory)
- [Bookings & Orders](#bookings--orders)
- [Payments](#payments)
- [Reviews & Ratings](#reviews--ratings)
- [Discovery & Search](#discovery--search)
- [Channel Manager](#channel-manager)
- [Analytics](#analytics)
- [Admin APIs](#admin-apis)

---

## Authentication & Users

### User Registration & Authentication ✅
```http
POST /api/v1/auth/register
POST /api/v1/auth/login
POST /api/v1/auth/logout
POST /api/v1/auth/refresh-token
POST /api/v1/auth/forgot-password
POST /api/v1/auth/reset-password
POST /api/v1/auth/verify-email
```

### User Profile Management
```http
GET    /api/v1/users/me
PUT    /api/v1/users/me
PATCH  /api/v1/users/me
DELETE /api/v1/users/me
GET    /api/v1/users/{user_id}
PUT    /api/v1/users/{user_id}/avatar
```

### Saved Locations
```http
GET    /api/v1/users/me/saved-locations
POST   /api/v1/users/me/saved-locations
PUT    /api/v1/users/me/saved-locations/{saved_location_id}
DELETE /api/v1/users/me/saved-locations/{saved_location_id}
```

### User Favorites
```http
GET    /api/v1/users/me/favorites
POST   /api/v1/users/me/favorites
DELETE /api/v1/users/me/favorites/{listing_id}
```

### User Search History
```http
GET    /api/v1/users/me/search-history
DELETE /api/v1/users/me/search-history/{search_id}
DELETE /api/v1/users/me/search-history
```

---

## Merchant Management

### Merchant Onboarding
```http
POST   /api/v1/merchants/apply
GET    /api/v1/merchants/onboarding-status
PUT    /api/v1/merchants/onboarding/{merchant_id}
POST   /api/v1/merchants/{merchant_id}/documents
```

### Merchant Profile Management
```http
GET    /api/v1/merchants/me
PUT    /api/v1/merchants/me
GET    /api/v1/merchants/{merchant_id}
GET    /api/v1/merchants/search
```

### Merchant Locations
```http
GET    /api/v1/merchants/me/locations
POST   /api/v1/merchants/me/locations
PUT    /api/v1/merchants/me/locations/{location_id}
DELETE /api/v1/merchants/me/locations/{location_id}
```

### Merchant Subscriptions
```http
GET    /api/v1/merchants/me/subscriptions
POST   /api/v1/merchants/me/subscriptions
PUT    /api/v1/merchants/me/subscriptions/{subscription_id}
DELETE /api/v1/merchants/me/subscriptions/{subscription_id}
```

### Merchant Promotions
```http
GET    /api/v1/merchants/me/promotions
POST   /api/v1/merchants/me/promotions
PUT    /api/v1/merchants/me/promotions/{promotion_id}
DELETE /api/v1/merchants/me/promotions/{promotion_id}
```

---

## Agent System

### Agent Registration & Management
```http
POST   /api/v1/agents/apply
GET    /api/v1/agents/me
PUT    /api/v1/agents/me
GET    /api/v1/agents/{agent_id}
```

### Agent Onboarding
```http
POST   /api/v1/agents/onboard-user
POST   /api/v1/agents/onboard-merchant
GET    /api/v1/agents/onboarding-stats
```

### Commission Management
```http
GET    /api/v1/agents/me/commissions
GET    /api/v1/agents/me/commissions/summary
POST   /api/v1/agents/me/commissions/{commission_id}/payout
```

### Leaderboard
```http
GET    /api/v1/agents/leaderboard
GET    /api/v1/agents/leaderboard/{period}
GET    /api/v1/agents/me/leaderboard-position
```

### Agent Analytics
```http
GET    /api/v1/agents/me/analytics
GET    /api/v1/agents/me/performance
```

---

## Listings & Inventory

### Listings Management
```http
GET    /api/v1/listings
POST   /api/v1/listings
GET    /api/v1/listings/{listing_id}
PUT    /api/v1/listings/{listing_id}
DELETE /api/v1/listings/{listing_id}
PATCH  /api/v1/listings/{listing_id}/status
```

### Listing Locations
```http
GET    /api/v1/listings/{listing_id}/locations
POST   /api/v1/listings/{listing_id}/locations
PUT    /api/v1/listings/{listing_id}/locations/{location_id}
DELETE /api/v1/listings/{listing_id}/locations/{location_id}
```

### Hotel Room Types
```http
GET    /api/v1/listings/{listing_id}/room-types
POST   /api/v1/listings/{listing_id}/room-types
GET    /api/v1/room-types/{room_type_id}
PUT    /api/v1/room-types/{room_type_id}
DELETE /api/v1/room-types/{room_type_id}
```

### Hotel Availability (bulk)
```http
POST   /api/v1/room-types/{room_type_id}/availability/bulk
PUT    /api/v1/room-types/{room_type_id}/availability/{date}
```

### Rate Plans
```http
GET    /api/v1/room-types/{room_type_id}/rate-plans
POST   /api/v1/room-types/{room_type_id}/rate-plans
GET    /api/v1/rate-plans/{rate_plan_id}
PUT    /api/v1/rate-plans/{rate_plan_id}
DELETE /api/v1/rate-plans/{rate_plan_id}
```

### Events Management
```http
GET    /api/v1/listings/{listing_id}/events
POST   /api/v1/listings/{listing_id}/events
GET    /api/v1/events/{event_id}
PUT    /api/v1/events/{event_id}
DELETE /api/v1/events/{event_id}
```
### Event Ticket Tiers
```http
GET    /api/v1/events/{event_id}/ticket-tiers
POST   /api/v1/events/{event_id}/ticket-tiers
PUT    /api/v1/ticket-tiers/{tier_id}
DELETE /api/v1/ticket-tiers/{tier_id}
```

### Restaurant Tables
```http
GET    /api/v1/listings/{listing_id}/tables
POST   /api/v1/listings/{listing_id}/tables
GET    /api/v1/tables/{table_id}
PUT    /api/v1/tables/{table_id}
DELETE /api/v1/tables/{table_id}
POST   /api/v1/listings/{listing_id}/table-availability/check
```


### Products Management
```http
GET    /api/v1/listings/{listing_id}/products
POST   /api/v1/listings/{listing_id}/products
GET    /api/v1/products/{product_id}
PUT    /api/v1/products/{product_id}
DELETE /api/v1/products/{product_id}
PATCH  /api/v1/products/{product_id}/inventory
```

### Services Management
```http
GET    /api/v1/listings/{listing_id}/services
POST   /api/v1/listings/{listing_id}/services
GET    /api/v1/services/{service_id}
PUT    /api/v1/services/{service_id}
DELETE /api/v1/services/{service_id}
POST   /api/v1/services/{service_id}/availability
PUT    /api/v1/services/{service_id}/availability/{date}
```

### Tour Packages
```http
GET    /api/v1/listings/{listing_id}/tours
POST   /api/v1/listings/{listing_id}/tours
GET    /api/v1/tours/{tour_id}
PUT    /api/v1/tours/{tour_id}
DELETE /api/v1/tours/{tour_id}
```

### Tour Schedule & Add-ons
```http
GET    /api/v1/tours/{tour_id}/schedule
POST   /api/v1/tours/{tour_id}/schedule
PUT    /api/v1/tour-schedule/{schedule_id}
DELETE /api/v1/tour-schedule/{schedule_id}

GET    /api/v1/tours/{tour_id}/addons
POST   /api/v1/tours/{tour_id}/addons
PUT    /api/v1/tour-addons/{addon_id}
DELETE /api/v1/tour-addons/{addon_id}
```

### Availability Management
```http
GET    /api/v1/listings/{listing_id}/availability
POST   /api/v1/listings/{listing_id}/availability/bulk
PUT    /api/v1/listings/{listing_id}/availability/{date}
DELETE /api/v1/listings/{listing_id}/availability/{date}
```

---

## Bookings & Orders

### Booking Search & Availability
```http
GET    /api/v1/bookings/availability
POST   /api/v1/bookings/check-availability
GET    /api/v1/bookings/calendar/{listing_id}
```

### Booking Creation & Management
```http
GET    /api/v1/bookings
POST   /api/v1/bookings
GET    /api/v1/bookings/{booking_id}
PUT    /api/v1/bookings/{booking_id}
DELETE /api/v1/bookings/{booking_id}
PATCH  /api/v1/bookings/{booking_id}/status
GET    /api/v1/bookings/user      # my trips (for users)
GET    /api/v1/bookings/merchant  # my guests (for merchants)
```

### Booking Participants
```http
GET    /api/v1/bookings/{booking_id}/participants
POST   /api/v1/bookings/{booking_id}/participants
PUT    /api/v1/bookings/{booking_id}/participants/{participant_id}
DELETE /api/v1/bookings/{booking_id}/participants/{participant_id}
```

### Booking Add-ons
```http
GET    /api/v1/bookings/{booking_id}/addons
POST   /api/v1/bookings/{booking_id}/addons
PUT    /api/v1/bookings/{booking_id}/addons/{addon_id}
DELETE /api/v1/bookings/{booking_id}/addons/{addon_id}
```

### Order Management
```http
GET    /api/v1/orders
POST   /api/v1/orders
GET    /api/v1/orders/{order_id}
PUT    /api/v1/orders/{order_id}
DELETE /api/v1/orders/{order_id}
PATCH  /api/v1/orders/{order_id}/status
```

### Check-in/Check-out
```http
POST   /api/v1/bookings/{booking_id}/checkin
POST   /api/v1/bookings/{booking_id}/checkout
POST   /api/v1/bookings/{booking_id}/participants/{participant_id}/checkin
```

---

## Payments

### Payment Processing
```http
POST   /api/v1/payments/initiate
POST   /api/v1/payments/confirm
POST   /api/v1/payments/webhook/momo
POST   /api/v1/payments/webhook/airtel
POST   /api/v1/payments/webhook/irembo
```

### Payment Management
```http
GET    /api/v1/payments
GET    /api/v1/payments/{payment_id}
POST   /api/v1/payments/{payment_id}/refund
POST   /api/v1/payments/{payment_id}/capture
```

### Split Payments
```http
POST   /api/v1/payments/{payment_id}/split
GET    /api/v1/payments/{payment_id}/splits
POST   /api/v1/payments/splits/{split_id}/settle
```

### Refunds
```http
GET    /api/v1/refunds
POST   /api/v1/refunds
GET    /api/v1/refunds/{refund_id}
PUT    /api/v1/refunds/{refund_id}
```

---

## Reviews & Ratings

### Reviews Management
```http
GET    /api/v1/reviews
POST   /api/v1/reviews
GET    /api/v1/reviews/{review_id}
PUT    /api/v1/reviews/{review_id}
DELETE /api/v1/reviews/{review_id}
```

### Review Helpful Votes
```http
POST   /api/v1/reviews/{review_id}/helpful
DELETE /api/v1/reviews/{review_id}/helpful
```

### Merchant Replies
```http
GET    /api/v1/reviews/{review_id}/replies
POST   /api/v1/reviews/{review_id}/replies
PUT    /api/v1/replies/{reply_id}
DELETE /api/v1/replies/{reply_id}
```

### Review Flags
```http
POST   /api/v1/reviews/{review_id}/flag
GET    /api/v1/review-flags
PUT    /api/v1/review-flags/{flag_id}
```

---

## Discovery & Search

### Search & Discovery
```http
GET    /api/v1/discover/search
GET    /api/v1/discover/nearby
GET    /api/v1/discover/map-pins
GET    /api/v1/discover/categories
GET    /api/v1/discover/categories/{category}/listings
```

### Curated Collections
```http
GET    /api/v1/collections
GET    /api/v1/collections/{collection_id}
POST   /api/v1/collections
PUT    /api/v1/collections/{collection_id}
DELETE /api/v1/collections/{collection_id}
```

```http
GET    /api/v1/community/feed
POST   /api/v1/community/posts
GET    /api/v1/community/posts/{post_id}
POST   /api/v1/community/stories
GET    /api/v1/community/guides
GET    /api/v1/community/guides/{guide_id}
```

---

## Channel Manager

### Property Management
```http
GET    /api/v1/channel-manager/properties
POST   /api/v1/channel-manager/properties
GET    /api/v1/channel-manager/properties/{property_id}
PUT    /api/v1/channel-manager/properties/{property_id}
DELETE /api/v1/channel-manager/properties/{property_id}
```

### OTA Connections
```http
POST   /api/v1/channel-manager/properties/{property_id}/connect-ota
PUT    /api/v1/channel-manager/properties/{property_id}/ota-connections/{connection_id}
DELETE /api/v1/channel-manager/properties/{property_id}/ota-connections/{connection_id}
```

### Sync Management
```http
POST   /api/v1/channel-manager/properties/{property_id}/sync
GET    /api/v1/channel-manager/properties/{property_id}/sync-status
POST   /api/v1/channel-manager/properties/{property_id}/force-sync
```

### Reservations
```http
GET    /api/v1/channel-manager/reservations
GET    /api/v1/channel-manager/reservations/{reservation_id}
PUT    /api/v1/channel-manager/reservations/{reservation_id}
POST   /api/v1/channel-manager/webhook/ota-reservation
```

### Rate & Inventory Sync
```http
POST   /api/v1/channel-manager/properties/{property_id}/push-rates
POST   /api/v1/channel-manager/properties/{property_id}/push-inventory
GET    /api/v1/channel-manager/properties/{property_id}/sync-logs
```

---

## Analytics

### Merchant Analytics
```http
GET    /api/v1/analytics/merchant/overview
GET    /api/v1/analytics/merchant/visits
GET    /api/v1/analytics/merchant/orders
GET    /api/v1/analytics/merchant/bookings
GET    /api/v1/analytics/merchant/revenue
GET    /api/v1/analytics/merchant/customer-insights
```

### Platform Analytics
```http
GET    /api/v1/analytics/platform/overview
GET    /api/v1/analytics/platform/user-growth
GET    /api/v1/analytics/platform/merchant-growth
GET    /api/v1/analytics/platform/revenue
GET    /api/v1/analytics/platform/geographic
```

### Channel Manager Analytics
```http
GET    /api/v1/analytics/channel-manager/performance
GET    /api/v1/analytics/channel-manager/ota-performance
GET    /api/v1/analytics/channel-manager/revpar
GET    /api/v1/analytics/channel-manager/occupancy
```

---

## Admin APIs

### User Management (Admin)
```http
GET    /api/v1/admin/users
GET    /api/v1/admin/users/{user_id}
PUT    /api/v1/admin/users/{user_id}
DELETE /api/v1/admin/users/{user_id}
PATCH  /api/v1/admin/users/{user_id}/status
```

### Merchant Management (Admin)
```http
GET    /api/v1/admin/merchants
GET    /api/v1/admin/merchants/{merchant_id}
PUT    /api/v1/admin/merchants/{merchant_id}
PATCH  /api/v1/admin/merchants/{merchant_id}/verification
PATCH  /api/v1/admin/merchants/{merchant_id}/status
```

### Agent Management (Admin)
```http
GET    /api/v1/admin/agents
GET    /api/v1/admin/agents/{agent_id}
PUT    /api/v1/admin/agents/{agent_id}
PATCH  /api/v1/admin/agents/{agent_id}/certification
PATCH  /api/v1/admin/agents/{agent_id}/tier
```

### Supported Merchant Types Configuration
```http
GET    /api/v1/admin/merchant-types
POST   /api/v1/admin/merchant-types
GET    /api/v1/admin/merchant-types/{type_id}
PUT    /api/v1/admin/merchant-types/{type_id}
DELETE /api/v1/admin/merchant-types/{type_id}
PATCH  /api/v1/admin/merchant-types/{type_id}/status
```

### Merchant Type Features & Requirements
```http
GET    /api/v1/admin/merchant-types/{type_id}/features
POST   /api/v1/admin/merchant-types/{type_id}/features
PUT    /api/v1/admin/merchant-types/{type_id}/features/{feature_id}
DELETE /api/v1/admin/merchant-types/{type_id}/features/{feature_id}
```

### Onboarding Requirements per Type
```http
GET    /api/v1/admin/merchant-types/{type_id}/requirements
POST   /api/v1/admin/merchant-types/{type_id}/requirements
PUT    /api/v1/admin/merchant-types/{type_id}/requirements/{requirement_id}
DELETE /api/v1/admin/merchant-types/{type_id}/requirements/{requirement_id}
```

### Commission Settings per Merchant Type
```http
GET    /api/v1/admin/merchant-types/{type_id}/commission
PUT    /api/v1/admin/merchant-types/{type_id}/commission
```

### Subscription Plans per Merchant Type
```http
GET    /api/v1/admin/merchant-types/{type_id}/subscription-plans
POST   /api/v1/admin/merchant-types/{type_id}/subscription-plans
PUT    /api/v1/admin/merchant-types/{type_id}/subscription-plans/{plan_id}
DELETE /api/v1/admin/merchant-types/{type_id}/subscription-plans/{plan_id}
```

### Commission Management (Admin)
```http
GET    /api/v1/admin/commissions
PUT    /api/v1/admin/commissions/{commission_id}
POST   /api/v1/admin/commissions/bulk-payout
```

### Content Moderation
```http
GET    /api/v1/admin/reviews/pending
PATCH  /api/v1/admin/reviews/{review_id}/moderation
GET    /api/v1/admin/review-flags
PUT    /api/v1/admin/review-flags/{flag_id}
```

### System Management
```http
GET    /api/v1/admin/system/health
GET    /api/v1/admin/system/metrics
GET    /api/v1/admin/system/logs
POST   /api/v1/admin/system/maintenance
```

### Financial Reports
```http
GET    /api/v1/admin/financial/transactions
GET    /api/v1/admin/financial/revenue
GET    /api/v1/admin/financial/commissions
GET    /api/v1/admin/financial/refunds
```

---

## Webhooks & External Integrations

### Payment Webhooks
```http
POST   /api/v1/webhooks/payments/momo
POST   /api/v1/webhooks/payments/airtel
POST   /api/v1/webhooks/payments/irembo
POST   /api/v1/webhooks/payments/card
```

### Channel Manager Webhooks
```http
POST   /api/v1/webhooks/channel-manager/reservation
POST   /api/v1/webhooks/channel-manager/inventory
POST   /api/v1/webhooks/channel-manager/rates
```

### SMS & Notification Webhooks
```http
POST   /api/v1/webhooks/sms/delivery
POST   /api/v1/webhooks/email/delivery
```

---

## Mobile-Specific APIs

### Push Notifications
```http
POST   /api/v1/notifications/register-device
DELETE /api/v1/notifications/device/{device_token}
POST   /api/v1/notifications/send
```

### Offline Sync
```http
GET    /api/v1/sync/last-update
POST   /api/v1/sync/pull
POST   /api/v1/sync/push
```

### Location Services
```http
GET    /api/v1/location/suggest
GET    /api/v1/location/geocode
GET    /api/v1/location/reverse-geocode
```

---

## Public APIs

### Public Listings
```http
GET    /api/v1/public/listings
GET    /api/v1/public/listings/{listing_id}
GET    /api/v1/public/listings/{listing_id}/reviews
```

### Public Merchant Profiles
```http
GET    /api/v1/public/merchants/{merchant_id}
GET    /api/v1/public/merchants/{merchant_id}/listings
```

### Public Events & Activities
```http
GET    /api/v1/public/events
GET    /api/v1/public/events/{event_id}
GET    /api/v1/public/collections
```

---

## Notes on Implementation

### Authentication & Authorization
- JWT-based authentication for all endpoints
- Role-based access control (User, Merchant, Agent, Admin)
- API rate limiting per user/merchant
- Webhook signature verification

### Pagination & Filtering
All list endpoints support:
- `page`, `limit` for pagination
- `sort` for ordering
- `filter` for field-based filtering
- `search` for text search
- `include` for related entities

### Error Handling
Standard error response format:
```json
{
  "error": {
    "code": "ERROR_CODE",
    "message": "Human readable message",
    "details": {}
  }
}
```

### Webhook Payloads
All webhooks include:
- Signature verification headers
- Retry mechanisms
- Idempotency keys

### File Uploads
- Support for images, documents
- File size and type validation

This API structure provides comprehensive coverage for all Zoea V2 features while maintaining scalability and security. Each endpoint should include proper validation, error handling, and documentation.