# 🏥 Elder Care Management System - LINE Bot AI Agent

A comprehensive healthcare management system built on LINE Bot platform with AI-powered assistance for elderly care services.

## 🎯 Overview

The Elder Care Management System is designed to facilitate seamless communication and coordination between four key user types:

- **👨‍👩‍👧 นายจ้าง (Employers)** - Family members seeking care services
- **👩‍⚕️ พนักงานผู้ดูแล (Caregivers)** - Professional healthcare providers
- **🤝 นายหน้า (Agents)** - Service coordinators and job matchers
- **🩺 พยาบาลเวร (Head Nurses)** - Medical supervisors and emergency responders

## 🚀 Features

### 💰 Financial Management
- **Fixed Rate System**: ฿1,600/day for employers
- **Variable Caregiver Pay**: ฿900-1,200 based on performance
- **Real-time Payment Calculation**: Based on actual check-in/out times
- **Advance Payment Support**: 50% advance payment available

### 🤖 AI-Powered Intelligence
- **Smart Job Matching**: AI-driven caregiver assignment
- **Predictive Analytics**: Anticipate care needs
- **Natural Language Processing**: Thai language support
- **Emergency Detection**: Automatic incident recognition

### 📊 Real-time Monitoring
- **GPS Tracking**: Location-based check-in/out
- **Health Monitoring**: Vital signs and medication tracking
- **Daily Reports**: Comprehensive care documentation
- **Performance Analytics**: KPI tracking and insights

### 🚨 Emergency Response
- **3-Level Alert System**: From mild to critical incidents
- **24/7 Monitoring**: Round-the-clock healthcare supervision
- **Automatic Notifications**: Instant emergency team alerts
- **Hospital Integration**: Direct medical facility coordination

## 🏗️ Architecture

### Technology Stack
```
Frontend: LINE Bot Interface with Rich Menus
Backend: Node.js with Express
Database: Supabase (PostgreSQL)
Cache: Redis
AI: Google Gemini
Sheets: Google Sheets API
Monitoring: Winston + Custom Health Checks
```

### System Architecture
```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   LINE OA       │    │  MCP Server     │    │ Business Logic  │
│   Interface     │────│     Layer       │────│     Layer       │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         │                       │                       │
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Rich Menus    │    │ User Detection  │    │ Check-in/out    │
│   (4 Types)     │    │ Role-Based      │    │ Payment Calc    │
│                 │    │ Access Control  │    │ Job Matching    │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## 📁 Project Structure

```
line-bot-sdk-nodejs/
├── src/                          # Main application source
│   ├── app.js                   # Application entry point
│   ├── controllers/             # Request handlers
│   ├── middleware/              # Express middleware
│   ├── routes/                  # API routes
│   └── models/                  # Data models
├── config/                      # Configuration files
│   ├── database/
│   │   └── supabase.js         # Database configuration
│   ├── linebot/
│   │   └── config.js           # LINE Bot settings
│   └── ai/                     # AI service configs
├── services/                    # Business logic services
│   ├── linebot/
│   │   └── bot-service.js      # LINE Bot service
│   ├── supabase/               # Database services
│   ├── gemini/                 # AI services
│   ├── sheets/                 # Google Sheets integration
│   └── redis/                  # Cache services
├── utils/                       # Utility functions
│   ├── logger/
│   │   └── winston.js          # Logging configuration
│   ├── validators/             # Data validation
│   └── helpers/                # Helper functions
├── monitoring/                  # Health checks and metrics
│   └── health-check.js         # System health monitoring
├── deploy/                      # Deployment scripts
│   └── deploy.sh               # Deployment automation
├── .env.example                 # Environment variables template
└── package.json                 # Dependencies and scripts
```

## 🚀 Quick Start

### Prerequisites
- Node.js 20+
- Redis server
- Supabase account
- Google Cloud Platform account (for AI and Sheets)
- LINE Developer account

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd line-bot-sdk-nodejs
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment setup**
   ```bash
   cp .env.example .env
   # Edit .env with your actual configuration values
   ```

4. **Database setup**
   - Create a Supabase project
   - Run the SQL schema (see `/database/schema.sql`)
   - Configure Row Level Security policies

5. **Start the application**
   ```bash
   # Development mode
   npm run elder-care:dev

   # Production mode
   npm run elder-care:start
   ```

### Development Scripts

```bash
# Start development server
npm run elder-care:dev

# Start production server
npm run elder-care:start

# Run health monitoring
npm run elder-care:monitor

# Deploy to production
npm run elder-care:deploy

# Check system status
./deploy/deploy.sh status
```

## 🔧 Configuration

### Required Environment Variables

```bash
# LINE Bot Configuration
LINE_CHANNEL_ACCESS_TOKEN=your_token
LINE_CHANNEL_SECRET=your_secret

# Database Configuration
SUPABASE_URL=your_supabase_url
SUPABASE_ANON_KEY=your_anon_key

# AI Configuration
GOOGLE_AI_API_KEY=your_gemini_key

# Redis Configuration
REDIS_URL=redis://localhost:6379

# Emergency Configuration
EMERGENCY_HOTLINE=1669
ADMIN_LINE_ID=your_admin_id
```

### Rich Menu Setup

Configure rich menus for each user type:
1. Create rich menu images (2500x1686px)
2. Upload via LINE Developers Console
3. Set menu IDs in environment variables

## 📱 User Journeys

### 👨‍👩‍👧 Employer Journey
```
Register → Find Caregiver → Monitor Care → Payment → Review
```

### 👩‍⚕️ Caregiver Journey
```
Register → Find Jobs → Apply → Check-in → Provide Care → Check-out → Payment
```

### 🤝 Agent Journey
```
Login → Job Matching → Monitor Cases → Resolve Issues → Report
```

### 🩺 Nurse Journey
```
Shift Start → Monitor Patients → Emergency Response → Guidance → Documentation
```

## 🗄️ Database Schema

### Core Tables
- `users` - User profiles and authentication
- `caregiver_profiles` - Extended caregiver information
- `patients` - Patient information and medical history
- `cases` - Care assignments and job postings
- `attendance` - Check-in/out tracking
- `daily_reports` - Care documentation
- `emergency_incidents` - Emergency event logging

### Key Features
- Row Level Security (RLS) enabled
- Real-time subscriptions for critical events
- Automated triggers for business logic
- Comprehensive audit logging

## 🚨 Emergency Protocol

### Alert Levels
1. **Level 1 (Mild)**: Minor concerns, nurse notification
2. **Level 2 (Moderate)**: Immediate nurse contact, employer alert
3. **Level 3 (Critical)**: Emergency services, all-team notification

### Emergency Keywords Detection
- Thai: ฉุกเฉิน, ช่วย, เจ็บ, หมดสติ, เลือดออก
- English: emergency, help, pain, unconscious, bleeding

## 📊 Monitoring & Analytics

### Health Checks
- Database connectivity
- Redis cache status
- AI service availability
- LINE Bot API status
- System resource usage

### Performance Metrics
- Response times
- User engagement
- Job matching success rate
- Payment processing time
- Emergency response time

## 🔐 Security & Compliance

### PDPA Compliance
- Data consent management
- Purpose limitation
- Data retention policies
- User rights management

### Security Features
- JWT authentication
- Request rate limiting
- Input validation
- SQL injection prevention
- XSS protection

## 🚀 Deployment

### Using the Deployment Script
```bash
# Deploy to production
./deploy/deploy.sh deploy

# Check status
./deploy/deploy.sh status

# Rollback if needed
./deploy/deploy.sh rollback
```

### Deployment Features
- Zero-downtime deployment
- Automatic health checks
- Rollback capability
- Backup management
- Log rotation

## 📈 Performance Optimization

### Caching Strategy
- User profiles cached for 1 hour
- Job listings cached for 5 minutes
- Health check results cached for 30 seconds

### Database Optimization
- Proper indexing on frequently queried columns
- Connection pooling
- Query optimization
- Stored procedures for complex operations

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

### Code Standards
- ES6+ JavaScript
- Comprehensive error handling
- Extensive logging
- Unit tests for critical functions

## 📞 Support

### Emergency Contacts
- **System Admin**: [Your contact info]
- **Technical Support**: [Your contact info]
- **Medical Emergency**: 1669

### Documentation
- [API Documentation](docs/api.md)
- [Database Schema](docs/database.md)
- [Deployment Guide](docs/deployment.md)

## 📄 License

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE) for details.

---

**🏥 Elder Care Management System - Caring for those who need it most** 💚