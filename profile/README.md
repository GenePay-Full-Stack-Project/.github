# 🔐 BioPay System

**Biometric Payment System** - Secure face-based payment solution with microservices architecture.

## 📋 Project Overview

BioPay is a secure payment system that uses facial recognition technology to process payments. The system consists of microservices backend, mobile applications for users and merchants, and an admin panel for management.

### 🏗️ Architecture

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   User App      │     │  Merchant App   │     │  Admin Panel    │
│   (Flutter)     │     │   (Flutter)     │     │    (React)      │
└────────┬────────┘     └────────┬────────┘     └────────┬────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
                        ┌────────▼────────┐
                        │   API Gateway   │
                        │     (Nginx)     │
                        └────────┬────────┘
                                 │
                 ┌───────────────┴───────────────┐
                 │                               │
         ┌───────▼────────┐            ┌────────▼─────────┐
         │  Payment        │◄──────────►│   Biometric     │
         │  Service        │            │   Service       │
         │  (Spring Boot)  │            │   (FastAPI)     │
         └────────┬────────┘            └────────┬────────┘
                  │                              │
         ┌────────▼────────┐            ┌────────▼────────┐
         │   PostgreSQL    │            │    MongoDB      │
         └─────────────────┘            └─────────────────┘
```

## 📁 Project Structure

```
bio_pay_system/
├── backend/
│   ├── biometric-service/    # Face recognition service (Python/FastAPI)
│   ├── payment-service/       # Payment processing (Java/Spring Boot)
│   ├── api-gateway/           # API Gateway (Nginx)
│   └── docker-compose.yml     # Local development setup
├── bio_pay_client/            # User mobile app (Flutter)
├── bio_pay_merchant/          # Merchant mobile app (Flutter)
├── bio_pay_admin/             # Admin web panel (React)
├── infrastructure/            # Deployment configs (K8s, Terraform)
├── .github/workflows/         # CI/CD pipelines
└── docs/                      # Documentation
```

## 🚀 Getting Started

### Prerequisites

- **Backend:**
  - Python 3.11+ (for Biometric Service)
  - Java 17+ (for Payment Service)
  - Docker & Docker Compose
  - PostgreSQL 15+
  - MongoDB 7+

- **Frontend:**
  - Flutter SDK 3.x
  - Node.js 18+ (for Admin Panel)
  - Android Studio / Xcode (for mobile development)

### Quick Start with Docker

1. Clone the repository:
```bash
git clone <repository-url>
cd bio_pay_system
```

2. Start all services:
```bash
cd backend
docker-compose up -d
```

3. Access services:
- Payment Service: http://localhost:8080
- Biometric Service: http://localhost:8001
- API Gateway: http://localhost:80

### Development Setup

#### Backend Services

**Biometric Service:**
```bash
cd backend/biometric-service
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8001
```

**Payment Service:**
```bash
cd backend/payment-service
mvn clean install
mvn spring-boot:run
```

#### Mobile Apps

**User App:**
```bash
cd bio_pay_client
flutter pub get
flutter run
```

**Merchant App:**
```bash
cd bio_pay_merchant
flutter pub get
flutter run
```

#### Admin Panel

```bash
cd bio_pay_admin
npm install
npm run dev
```

## 🧪 Testing

### Backend Tests
```bash
# Biometric Service
cd backend/biometric-service
pytest tests/ -v --cov=app

# Payment Service
cd backend/payment-service
mvn test
```

### Mobile Tests
```bash
# Flutter apps
cd bio_pay_client
flutter test

cd bio_pay_merchant
flutter test
```

## 📚 Documentation

- [API Documentation](docs/api-docs/)
- [Architecture Guide](docs/architecture.md)
- [Deployment Guide](docs/deployment-guide.md)
- [Development Guidelines](docs/development-guidelines.md)

## 🔐 Security

- JWT-based authentication
- Face data stored as embeddings (not raw images)
- HTTPS everywhere in production
- Rate limiting on API Gateway
- Database encryption at rest
- Secure card tokenization

## 🤝 Contributing

Please read [CONTRIBUTING.md](docs/CONTRIBUTING.md) for our code of conduct and development process.

### Git Workflow

We use a modified GitFlow strategy:

- `main` - Production-ready code
- `develop` - Integration branch
- `feature/*` - New features
- `bugfix/*` - Bug fixes
- `hotfix/*` - Critical production fixes

### Commit Convention

```
<type>(<scope>): <subject>

Example:
feat(biometric): add face verification API
fix(payment): resolve duplicate transaction issue
docs(readme): update installation instructions
```

## 📊 Project Status

- [x] Project initialization
- [ ] Biometric Service core implementation
- [ ] Payment Service core implementation
- [ ] User mobile app development
- [ ] Merchant mobile app development
- [ ] Admin panel development
- [ ] Integration testing
- [ ] Production deployment

## 👥 Team

- **Backend Team:** Microservices development
- **Mobile Team:** Flutter app development
- **Frontend Team:** Admin panel development
- **DevOps Team:** Infrastructure & deployment

## 📄 License

Proprietary - BioPay System © 2025

## 📞 Contact

For questions or support, please contact the development team.

---

**Built with ❤️ by BioPay Team**
