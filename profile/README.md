# SevaLK - Microservices Architecture Plan

## Project Overview
SevaLK is a service platform with two mobile clients (Customer and Provider) built on a microservices architecture.

---

## Repository Naming Convention

**Format:** `sevaLK-[type]-[name]`

### Complete Repository List (8 Total)

**Mobile Apps (2)**
- `sevaLK-mobile-customer`
- `sevaLK-mobile-provider`

**Backend Microservices (4)**
- `sevaLK-service-auth`
- `sevaLK-service-user`
- `sevaLK-service-booking`
- `sevaLK-service-payment`

**Infrastructure (2)**
- `sevaLK-gateway-api`
- `sevaLK-infra-config`

---

## Project Structure

### Infrastructure Repository (`sevaLK-infra-config`)
```
sevaLK-infra-config/
├── docker/
│   ├── docker-compose.yml
│   └── Dockerfile templates
├── kubernetes/
│   ├── auth-service/
│   │   ├── deployment.yaml
│   │   ├── service.yaml
│   │   └── configmap.yaml
│   ├── user-service/
│   │   ├── deployment.yaml
│   │   ├── service.yaml
│   │   └── configmap.yaml
│   ├── booking-service/
│   │   ├── deployment.yaml
│   │   ├── service.yaml
│   │   └── configmap.yaml
│   ├── payment-service/
│   │   ├── deployment.yaml
│   │   ├── service.yaml
│   │   └── configmap.yaml
│   └── gateway/
│       ├── deployment.yaml
│       └── service.yaml
├── argocd/
│   ├── application.yaml
│   └── project.yaml
└── .github/
    └── workflows/
        └── ci-cd.yml
```

### Service Repository Structure (Example)
```
sevaLK-service-auth/
├── src/
│   ├── controllers/
│   ├── services/
│   ├── models/
│   ├── routes/
│   └── config/
├── tests/
├── Dockerfile
├── package.json
├── .env.example
└── README.md
```

---

## Microservices Responsibilities

## Microservices Responsibilities

### 1. Authentication Service (`sevaLK-service-auth`)

**Responsibilities:**
- User registration (customer & provider)
- User login/logout
- JWT token generation & validation
- Password management (reset, change)
- Role-based access control (Customer, Provider, Admin)

**Database:** PostgreSQL
**Cache:** Redis

---

### 2. User Service (`sevaLK-service-user`)

**Responsibilities:**
- Customer profile management
- Provider profile management
- Profile verification & KYC
- Document upload & storage
- Search providers (location, rating, availability)
- Send notifications (push, email, SMS)

**Database:** PostgreSQL
**Storage:** AWS S3

---

### 3. Booking Service (`sevaLK-service-booking`)

**Responsibilities:**
- Create & manage bookings
- Provider availability management
- Booking status tracking
- Location tracking (real-time)
- Customer-provider messaging/chat
- Reviews & ratings

**Database:** PostgreSQL
**Cache:** Redis
**Real-time:** WebSocket/Socket.io

---

### 4. Payment Service (`sevaLK-service-payment`)

**Responsibilities:**
- Process payments
- Handle refunds
- Transaction history
- Commission calculation
- Payment gateway integration

**Database:** PostgreSQL
**Integrations:** Stripe, PayPal

---

### 5. API Gateway (`sevaLK-gateway-api`)

**Responsibilities:**
- Route requests to microservices
- Authentication verification
- Rate limiting
- CORS handling
- Request/response transformation

**Cache:** Redis

---

## Mobile Applications

### Customer App (`sevaLK-mobile-customer`)
**Features:**
- Browse & search providers
- Book services
- Track provider location
- Make payments
- Rate & review providers
- Push notifications
- In-app chat

### Provider App (`sevaLK-mobile-provider`)
**Features:**
- Manage availability & calendar
- Accept/reject bookings
- Navigate to customer location
- Update service status
- View earnings
- Push notifications
- In-app chat

**Tech Stack:** React Native or Flutter

---

## Architecture Diagram
```
Mobile Apps (Customer & Provider)
         ↓
    API Gateway
         ↓
    ┌────┴────┬─────────┬─────────┐
    ↓         ↓         ↓         ↓
  Auth     User    Booking   Payment
Service  Service  Service   Service
    ↓         ↓         ↓         ↓
  Redis   PostgreSQL databases
```

---

**Version:** 1.0  
**Last Updated:** December 17, 2025
