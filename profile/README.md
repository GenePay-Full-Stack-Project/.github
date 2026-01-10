# 📚 GenePay Microservices Repository Guide

**Complete guide to the GenePay system's microservices architecture and repository organization.**

## 🎯 Overview

GenePay is a biometric payment system split into **7 independent microservice repositories** for better scalability, maintainability, and deployment flexibility. This document provides an overview of all repositories and how they work together.

## 📁 Repository Structure

The GenePay project uses the **[genepay-core](https://github.com/GenePay-Full-Stack-Project/genepay-core)** repository as the central hub. This repository contains automated scripts to clone and organize all GenePay services into a structured workspace:

```
genepay-core/
├── modules/                              # Backend Services
│   ├── genepay-biometric-service/       # Python FastAPI - Face recognition
│   ├── genepay-payment-service/         # Java Spring Boot - Payment processing
│   └── genepay-blockchain-service/      # Node.js - Blockchain integration
├── web/                                 # Web Applications
│   ├── genepay-admin-dashboard/         # React - Admin panel
│   └── genepay-blockchain-dashboard/    # React TypeScript - Blockchain explorer
└── mobile/                              # Mobile Applications
    ├── genepay_merchant_app/            # Flutter - Merchant app
    └── genepay_user_app/                # Flutter - User app
```

### 🚀 Quick Setup with genepay-core

Clone the genepay-core repository and run the setup script:

```bash
# Clone genepay-core
git clone https://github.com/GenePay-Full-Stack-Project/genepay-core.git
cd genepay-core

# Run the appropriate script for your OS:
# Windows Command Prompt:
clone-repos.bat

# Windows PowerShell:
.\clone-repos.ps1

# Linux/macOS:
chmod +x clone-repos.sh
./clone-repos.sh
```

The script will automatically create the folder structure and clone all repositories.

### Backend Services (3 Repositories)

#### 1. [GenePay Biometric Service](https://github.com/GenePay-Full-Stack-Project/genepay-biometric-service)
**Face Recognition & Verification Microservice**

- **Technology**: Python, FastAPI
- **Database**: MongoDB
- **Purpose**: Face registration, verification, liveness detection
- **Port**: 8001
- **Key Features**:
  - Face embedding generation (128-dimensional vectors)
  - Real-time 1:1 face matching
  - Anti-spoofing liveness detection
  - AWS S3 integration for face image storage
  - RESTful API with automatic Swagger documentation

**Repository**: `git clone https://github.com/GenePay-Full-Stack-Project/genepay-biometric-service.git`

**Location**: `modules/genepay-biometric-service/`

---

#### 2. [GenePay Payment Service](https://github.com/GenePay-Full-Stack-Project/genepay-payment-service)
**Core Payment Processing Microservice**

- **Technology**: Java 21, Spring Boot 3.5.7
- **Database**: PostgreSQL
- **Purpose**: User management, payment processing, merchant onboarding
- **Port**: 8080
- **Key Features**:
  - User registration and JWT authentication
  - Stripe payment integration
  - Card tokenization and management
  - Merchant Stripe Connect onboarding
  - Transaction history and reporting
  - Withdrawal management
  - Blockchain integration for audit trail

**Repository**: `git clone https://github.com/GenePay-Full-Stack-Project/genepay-payment-service.git`

**Location**: `modules/genepay-payment-service/`

---

#### 3. [GenePay Blockchain Service](https://github.com/GenePay-Full-Stack-Project/genepay-blockchain-service)
**Blockchain Audit Ledger Microservice**

- **Technology**: Solidity, Node.js, Express, ethers.js
- **Blockchain**: Ethereum (Sepolia testnet/Mainnet)
- **Purpose**: Immutable transaction audit trail
- **Port**: 3000 (Relay Service)
- **Key Features**:
  - Solidity smart contract (AuditLedger.sol)
  - Node.js blockchain relay API
  - Automatic transaction recording
  - Batch transaction recording
  - Transaction query interface
  - Blockchain statistics and analytics
  - Hardhat development environment

**Repository**: `git clone https://github.com/GenePay-Full-Stack-Project/genepay-blockchain-service.git`

**Location**: `modules/genepay-blockchain-service/`

---

### Frontend Applications (4 Repositories)

#### 4. [GenePay Admin Dashboard](https://github.com/GenePay-Full-Stack-Project/genepay-admin-dashboard)
**Web-based Administration Panel**

- **Technology**: React 18, JavaScript, Vite
- **Purpose**: Platform administration and monitoring
- **Key Features**:
  - User management (view, suspend, block users)
  - Merchant management and approval
  - Transaction monitoring and analytics
  - Withdrawal request approval
  - Platform statistics dashboard
  - System health monitoring

**Repository**: `git clone https://github.com/GenePay-Full-Stack-Project/genepay-admin-dashboard.git`

**Location**: `web/genepay-admin-dashboard/`

---

#### 5. [GenePay User App](https://github.com/GenePay-Full-Stack-Project/genepay-user-app)
**Customer Mobile Application**

- **Technology**: Flutter 3.24+, Dart 3.5+
- **Platform**: iOS & Android
- **Purpose**: Customer payment interface
- **Key Features**:
  - User registration and authentication
  - Face enrollment wizard
  - Card management (add/remove cards via Stripe)
  - QR code scanning for payments
  - Face verification for payment authorization
  - Transaction history and receipts
  - Profile management

**Repository**: `git clone https://github.com/GenePay-Full-Stack-Project/genepay-user-app.git`

**Location**: `mobile/genepay_user_app/`

---

#### 6. [GenePay Merchant App](https://github.com/GenePay-Full-Stack-Project/genepay-merchant-app)
**Merchant Mobile Application**

- **Technology**: Flutter 3.24+, Dart 3.5+
- **Platform**: iOS & Android
- **Purpose**: Merchant payment acceptance
- **Key Features**:
  - Merchant registration and onboarding
  - Stripe Connect Express integration
  - Payment QR code generation
  - Real-time payment notifications
  - Earnings dashboard and analytics
  - Withdrawal requests to bank account
  - Transaction management and reporting

**Repository**: `git clone https://github.com/GenePay-Full-Stack-Project/genepay-merchant-app.git`

**Location**: `mobile/genepay_merchant_app/`

---

#### 7. [GenePay Blockchain Dashboard](https://github.com/GenePay-Full-Stack-Project/genepay-blockchain-dashboard)
**Blockchain Transaction Explorer**

- **Technology**: React 18, TypeScript, Vite
- **Purpose**: Blockchain transparency and audit
- **Key Features**:
  - Real-time transaction feed from blockchain
  - Transaction search and filtering
  - Etherscan integration
  - Blockchain statistics dashboard
  - Transaction volume analytics
  - Platform fee breakdown
  - Animated UI with floating lines background

**Repository**: `git clone https://github.com/GenePay-Full-Stack-Project/genepay-blockchain-dashboard.git`

**Location**: `web/genepay-blockchain-dashboard/`

---

## 🔄 System Integration Flow

```
┌─────────────────────────────────────────────────────────────────────┐
│                         GenePay System Architecture                  │
└─────────────────────────────────────────────────────────────────────┘

┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│   User App   │  │ Merchant App │  │Admin Dashboard│  │Blockchain DB │
│  (Flutter)   │  │  (Flutter)   │  │   (React)     │  │(React+TS)    │
└──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘
       │                 │                  │                  │
       └─────────────────┴──────────────────┴──────────────────┘
                                   │
                          ┌────────▼────────┐
                          │   API Gateway   │
                          │     (Nginx)     │
                          └────────┬────────┘
                                   │
                 ┌─────────────────┼─────────────────┐
                 │                 │                 │
         ┌───────▼────────┐ ┌─────▼────────┐ ┌─────▼─────────┐
         │  Payment        │ │  Biometric   │ │  Blockchain   │
         │  Service        │◄┤  Service     │ │  Relay        │
         │  (Spring Boot)  │ │  (FastAPI)   │ │  (Node.js)    │
         └────────┬────────┘ └──────┬───────┘ └───────┬───────┘
                  │                 │                  │
         ┌────────▼────────┐ ┌──────▼───────┐  ┌──────▼────────┐
         │   PostgreSQL    │ │   MongoDB    │  │   Ethereum    │
         │   (User/Txn)    │ │ (Biometric)  │  │   Network     │
         └─────────────────┘ └──────────────┘  └───────────────┘
```

## 🚀 Quick Start Guide

### Option 1: Automated Setup (Recommended)

Use the **genepay-core** repository for automated cloning and folder organization:

```bash
# Clone genepay-core repository
git clone https://github.com/GenePay-Full-Stack-Project/genepay-core.git
cd genepay-core

# Run the appropriate script for your OS:

# Windows (Command Prompt):
clone-repos.bat

# Windows (PowerShell):
.\clone-repos.ps1

# Linux/macOS:
chmod +x clone-repos.sh
./clone-repos.sh
```

The script will automatically:
- Create `modules/`, `web/`, and `mobile/` folders
- Clone all 7 repositories into their correct locations
- Provide progress tracking and error reporting

### Option 2: Manual Clone

```bash
# Create project directory
mkdir genepay-system && cd genepay-system

# Create folder structure
mkdir modules web mobile

# Clone backend services
git clone https://github.com/GenePay-Full-Stack-Project/genepay-biometric-service.git modules/genepay-biometric-service
git clone https://github.com/GenePay-Full-Stack-Project/genepay-payment-service.git modules/genepay-payment-service
git clone https://github.com/GenePay-Full-Stack-Project/genepay-blockchain-service.git modules/genepay-blockchain-service

# Clone web applications
git clone https://github.com/GenePay-Full-Stack-Project/genepay-admin-dashboard.git web/genepay-admin-dashboard
git clone https://github.com/GenePay-Full-Stack-Project/genepay-blockchain-dashboard.git web/genepay-blockchain-dashboard

# Clone mobile applications
git clone https://github.com/GenePay-Full-Stack-Project/genepay-merchant-app.git mobile/genepay_merchant_app
git clone https://github.com/GenePay-Full-Stack-Project/genepay-user-app.git mobile/genepay_user_app
```

## 📋 Prerequisites by Service

### Backend Services
- **Payment Service**: Java 21, Maven 3.8+, PostgreSQL 15+
- **Biometric Service**: Python 3.11+, MongoDB 6.0+, CMake
- **Blockchain Service**: Node.js 18+, Ethereum wallet, Infura/Alchemy API

### Frontend Applications
- **Admin Dashboard**: Node.js 18+, npm/yarn
- **User App**: Flutter 3.24+, Dart 3.5+, Android Studio/Xcode
- **Merchant App**: Flutter 3.24+, Dart 3.5+, Android Studio/Xcode
- **Blockchain Dashboard**: Node.js 18+, npm/yarn

### Development Tools
- **Version Control**: Git
- **Code Editors**: VS Code, IntelliJ IDEA, Android Studio

## 🔧 Development Workflow

### 1. Local Development Setup

Each service can be developed independently:

```bash
# Example: Payment Service
cd modules/genepay-payment-service
cp .env.example .env
# Edit .env with your configuration
mvn spring-boot:run

# Example: Biometric Service
cd modules/genepay-biometric-service
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload

# Example: Admin Dashboard
cd web/genepay-admin-dashboard
npm install
npm run dev

# Example: Merchant App
cd mobile/genepay_merchant_app
flutter pub get
flutter run
```

### 2. Running All Services Locally

Each service runs on its designated port:

```bash
# Terminal 1: Payment Service (Port 8080)
cd modules/genepay-payment-service
mvn spring-boot:run

# Terminal 2: Biometric Service (Port 8001)
cd modules/genepay-biometric-service
uvicorn app.main:app --reload

# Terminal 3: Blockchain Service (Port 3000)
cd modules/genepay-blockchain-service
npm install
npm start

# Terminal 4: Admin Dashboard (Port 3001)
cd web/genepay-admin-dashboard
npm install
npm run dev

# Terminal 5: Blockchain Dashboard (Port 3002)
cd web/genepay-blockchain-dashboard
npm install
npm run dev
```

## 🔗 Service Communication

### API Endpoints

| Service | Port | Base URL | Purpose |
|---------|------|----------|---------|
| Payment Service | 8080 | `/api` | Core business logic |
| Biometric Service | 8001 | `/api/v1/biometric` | Face verification |
| Blockchain Relay | 3000 | `/api` | Blockchain recording |
| Admin Dashboard | 3001 | `/` | Admin interface |
| Blockchain Dashboard | 3002 | `/` | Blockchain explorer |

### Service Dependencies

```
Payment Service
  ├── → Biometric Service (face verification)
  ├── → Blockchain Relay (transaction recording)
  ├── → Stripe API (payment processing)
  └── → PostgreSQL (data storage)

Biometric Service
  ├── → MongoDB (biometric data)
  └── → AWS S3 (image storage, optional)

Blockchain Relay
  ├── → Ethereum Network (transaction recording)
  └── → AuditLedger Smart Contract

User/Merchant Apps
  └── → Payment Service (all operations)

Admin Dashboard
  └── → Payment Service (admin operations)

Blockchain Dashboard
  └── → Blockchain Relay (transaction queries)
```

## 🌐 Deployment Architecture

### Development Environment
- Local machines
- Docker Compose
- Hot reload enabled
- Debug logging

### Staging Environment
- Kubernetes cluster
- Separate namespace
- Shared databases
- Similar to production

### Production Environment
- Kubernetes cluster (EKS/GKE/AKS)
- Multiple replicas per service
- Load balancers
- Auto-scaling enabled
- Production databases (replica sets)
- CDN for frontend assets
- SSL/TLS certificates
- Monitoring and alerting

## 📊 Technology Stack Summary

| Layer | Technologies |
|-------|-------------|
| **Backend** | Java 21 (Spring Boot), Python 3.11 (FastAPI), Node.js 18 (Express) |
| **Frontend** | React 18, TypeScript, Flutter 3.24, Dart 3.5 |
| **Databases** | PostgreSQL 15, MongoDB 6.0 |
| **Blockchain** | Solidity, Ethereum, ethers.js, Hardhat |
| **Payments** | Stripe SDK, Stripe Connect |

## 🔒 Security Considerations

### Service-Level Security
- JWT authentication for all APIs
- HTTPS/TLS in production
- API rate limiting
- Input validation and sanitization
- SQL injection prevention (parameterized queries)
- XSS protection

### Data Security
- Encrypted data at rest (database encryption)
- Encrypted data in transit (TLS)
- Secure storage (Flutter Secure Storage, Spring Security)
- No sensitive data on blockchain (only hashes)
- Biometric data encryption

### Secrets Management
- Environment variables (never committed to Git)
- Stripe API keys secured
- Private keys never exposed
- MongoDB connection strings secured
- Database credentials protected

## 🤝 Contributing to GenePay

### Contribution Guidelines

1. **Fork the relevant repository**
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Follow coding standards**:
   - Java: Google Java Style Guide
   - Python: PEP 8
   - JavaScript/TypeScript: ESLint + Prettier
   - Dart/Flutter: Effective Dart
4. **Write tests** for new features
5. **Update documentation** as needed
6. **Commit with clear messages**: `git commit -m 'Add amazing feature'`
7. **Push to branch**: `git push origin feature/amazing-feature`
8. **Open Pull Request** with detailed description

### Code Review Process
- All PRs require review by 2+ team members
- Automated tests must pass
- Code coverage must not decrease
- Documentation must be updated

## 📞 Support & Contact

### General Support
- **Organization**: [GenePay-Full-Stack-Project](https://github.com/GenePay-Full-Stack-Project)
- **Documentation**: Check individual repository README files

### Service-Specific Issues
- **Payment Service**: [GitHub Issues](https://github.com/GenePay-Full-Stack-Project/genepay-payment-service/issues)
- **Biometric Service**: [GitHub Issues](https://github.com/GenePay-Full-Stack-Project/genepay-biometric-service/issues)
- **Blockchain Service**: [GitHub Issues](https://github.com/GenePay-Full-Stack-Project/genepay-blockchain-service/issues)
- **Admin Dashboard**: [GitHub Issues](https://github.com/GenePay-Full-Stack-Project/genepay-admin-dashboard/issues)
- **Blockchain Dashboard**: [GitHub Issues](https://github.com/GenePay-Full-Stack-Project/genepay-blockchain-dashboard/issues)
- **Merchant App**: [GitHub Issues](https://github.com/GenePay-Full-Stack-Project/genepay-merchant-app/issues)
- **User App**: [GitHub Issues](https://github.com/GenePay-Full-Stack-Project/genepay-user-app/issues)

## 📚 Additional Resources

### Technology Documentation
- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [Flutter Documentation](https://flutter.dev/docs)
- [React Documentation](https://react.dev/)
- [Ethereum Documentation](https://ethereum.org/en/developers/docs/)
- [Stripe Documentation](https://stripe.com/docs)
- [MongoDB Documentation](https://www.mongodb.com/docs/)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)

## 📄 License

All GenePay repositories are part of an academic project. Please refer to individual repository LICENSE files for details.

---

## 🗂️ Repository Links Summary

| # | Repository | Technology | Location | Purpose |
|---|------------|------------|----------|---------|
| 0 | [genepay-core](https://github.com/GenePay-Full-Stack-Project/genepay-core) | Scripts | Root | Setup & organization |
| 1 | [genepay-payment-service](https://github.com/GenePay-Full-Stack-Project/genepay-payment-service) | Java/Spring Boot | modules/ | Core payment processing |
| 2 | [genepay-biometric-service](https://github.com/GenePay-Full-Stack-Project/genepay-biometric-service) | Python/FastAPI | modules/ | Face recognition |
| 3 | [genepay-blockchain-service](https://github.com/GenePay-Full-Stack-Project/genepay-blockchain-service) | Node.js/Solidity | modules/ | Audit ledger |
| 4 | [genepay-admin-dashboard](https://github.com/GenePay-Full-Stack-Project/genepay-admin-dashboard) | React/JavaScript | web/ | Admin panel |
| 5 | [genepay-blockchain-dashboard](https://github.com/GenePay-Full-Stack-Project/genepay-blockchain-dashboard) | React/TypeScript | web/ | Blockchain explorer |
| 6 | [genepay-merchant-app](https://github.com/GenePay-Full-Stack-Project/genepay-merchant-app) | Flutter/Dart | mobile/ | Merchant mobile app |
| 7 | [genepay-user-app](https://github.com/GenePay-Full-Stack-Project/genepay-user-app) | Flutter/Dart | mobile/ | User mobile app |

---

**Built with ❤️ by the GenePay Team**  
**Academic Project - NIBM 3rd Year, Semester 01, Agile Software Development
