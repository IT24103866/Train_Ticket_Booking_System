# 🚂 Train Booking System

<p align="center">
  <img src="https://via.placeholder.com/150?text=Train+Booking" alt="Train Booking System Logo">
  <br>
  A comprehensive train ticket reservation system that allows users to search, book, and manage train tickets online.
</p>

<p align="center">
  <a href="#features">Features</a> •
  <a href="#demo">Demo</a> •
  <a href="#technologies">Technologies</a> •
  <a href="#installation">Installation</a> •
  <a href="#usage">Usage</a> •
  <a href="#api-documentation">API Documentation</a> •
  <a href="#architecture">Architecture</a> •
  <a href="#contributing">Contributing</a> •
  <a href="#license">License</a>
</p>

## 📋 Overview

This Train Booking System provides a modern, intuitive platform for railway reservations. The application connects passengers with available train services, offering a seamless booking experience with secure payment processing, seat selection, and ticket management.

## ✨ Features <a name="features"></a>

### For Passengers
- **User Account Management**
  - Secure registration and login
  - Profile customization
  - Booking history and saved preferences
  - Multi-factor authentication

- **Search & Discovery**
  - Real-time train availability
  - Advanced filtering (price, duration, train type)
  - Interactive route maps
  - Fare comparison

- **Booking Process**
  - Interactive seat selection with visual coach layout
  - Multi-passenger booking with different fare types
  - Special accommodation requests
  - Luggage and special service add-ons

- **Payment & Ticketing**
  - Multiple payment options (credit/debit cards, digital wallets)
  - Secure transaction processing
  - E-tickets with QR codes
  - Auto-generated receipts and invoices

- **Trip Management**
  - Booking modifications and cancellations
  - Refund processing
  - Journey reminders and notifications
  - Travel disruption alerts

### For Administrators
- **System Management**
  - Route and schedule configuration
  - Dynamic pricing and fare management
  - Seat availability control
  - System-wide announcements

- **Analytics Dashboard**
  - Revenue tracking and reporting
  - Booking patterns and trends
  - Occupancy rates
  - Performance metrics

- **Customer Support Tools**
  - Ticket issue resolution
  - Passenger communication system
  - Refund and compensation management

## 🎬 Demo <a name="demo"></a>

[View Live Demo](https://your-demo-link.com)

**Test Credentials:**
- **Passenger:** user@example.com / password123
- **Admin:** admin@example.com / adminpass

## 🛠️ Technologies <a name="technologies"></a>

### Backend
- **Language:** Java/Spring Boot
- **API:** RESTful architecture
- **Authentication:** JWT-based authentication
- **Database:** MySQL for persistent data storage
- **Caching:** Redis for session management and high-speed data access

### Frontend
- **Framework:** React.js with Redux for state management
- **Styling:** SCSS and Material-UI components
- **Maps:** Mapbox integration for route visualization
- **Responsive Design:** Mobile-first approach with Progressive Web App capabilities

### Payment Processing
- Stripe API integration with 3D Secure authentication
- PayPal as alternative payment option

### Deployment
- Docker containerization
- CI/CD pipeline using GitHub Actions
- Cloud hosting on AWS/Azure/GCP

## 🚀 Installation <a name="installation"></a>

### Prerequisites
- Node.js (v16+)
- Java JDK 11+
- MySQL (v8.0+)
- Redis (optional, for advanced caching)

### Step 1: Clone the repository
```bash
git clone https://github.com/Krishmal2004/Train_Booking_System.git
cd Train_Booking_System
```

### Step 2: Backend Setup
```bash
cd backend
./mvnw clean install
cp .env.example .env
# Edit the .env file with your database credentials and configuration
```

### Step 3: Database Setup
```bash
# Create database and run migrations
./mvnw flyway:migrate
# Alternatively for manual setup
mysql -u root -p < database/schema.sql
```

### Step 4: Frontend Setup
```bash
cd ../frontend
npm install
cp .env.example .env
# Edit the .env file with API endpoints and other settings
```

### Step 5: Start the application
```bash
# Start backend (from backend directory)
./mvnw spring-boot:run

# Start frontend (from frontend directory)
npm start
```

The application will be available at `http://localhost:3000`

## 📘 Usage <a name="usage"></a>

### Passenger Workflow

1. **Registration & Login**
   - Create a new account or login with existing credentials
   - Setup profile preferences and saved payment methods

2. **Search for Trains**
   - Enter origin, destination, travel date, and passenger count
   - Apply filters for departure time, train type, or class

3. **Select and Book**
   - Choose preferred train from search results
   - Select seats from the interactive coach layout
   - Add passenger details and any special requirements

4. **Payment & Confirmation**
   - Select payment method and complete transaction
   - Receive confirmation and e-ticket via email and in-app notification

5. **Trip Management**
   - View upcoming and past trips in the user dashboard
   - Modify or cancel reservations if needed
   - Download or print e-tickets

### Administrator Workflow

1. **Dashboard Access**
   - Login to the admin portal with admin credentials
   - View system overview and key metrics

2. **Train Management**
   - Configure train schedules, routes, and stops
   - Adjust seat availability and pricing
   - Manage seasonal offers and discounts

3. **Booking Management**
   - View and search all bookings
   - Process manual bookings or cancellations
   - Handle customer support requests

4. **Reporting**
   - Generate revenue reports
   - Analyze booking trends and occupancy rates
   - Export data for external processing

## 📚 API Documentation <a name="api-documentation"></a>

Our API follows RESTful principles and supports the following endpoints:

### Authentication
- `POST /api/auth/register` - Create new user account
- `POST /api/auth/login` - Authenticate user
- `GET /api/auth/profile` - Retrieve user profile

### Train Search
- `GET /api/trains` - List available trains
- `GET /api/trains/{id}` - Get specific train details
- `GET /api/stations` - List all stations

### Booking
- `POST /api/bookings` - Create new booking
- `GET /api/bookings` - List user bookings
- `GET /api/bookings/{id}` - Get booking details
- `PUT /api/bookings/{id}` - Update booking
- `DELETE /api/bookings/{id}` - Cancel booking

For complete API documentation, visit our [API Docs](https://your-api-docs-url.com) or run the application and navigate to `/swagger-ui.html`.

## 🏗️ Architecture <a name="architecture"></a>

The Train Booking System follows a microservices architecture pattern:

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│                 │     │                 │     │                 │
│  User Service   │     │  Train Service  │     │ Booking Service │
│                 │     │                 │     │                 │
└────────┬────────┘     └────────┬────────┘     └────────┬────────┘
         │                       │                       │
         └───────────┬───────────┴───────────┬───────────┘
                     │                       │
           ┌─────────▼─────────┐   ┌─────────▼─────────┐
           │                   │   │                   │
           │  API Gateway      │   │  Payment Service  │
           │                   │   │                   │
           └─────────┬─────────┘   └─────────┬─────────┘
                     │                       │
                     └───────────┬───────────┘
                                 │
                       ┌─────────▼─────────┐
                       │                   │
                       │  Frontend Client  │
                       │                   │
                       └───────────────────┘
```

## 📊 Database Schema

Our system uses a relational database with the following core tables:

```
Users          Trains         Stations       Bookings         Tickets
┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐      ┌─────────┐
│id       │    │id       │    │id       │    │id       │      │id       │
│name     │    │name     │    │name     │    │user_id  │──┐   │booking_id
│email    │    │capacity │    │location │    │train_id │──┼──┐│passenger│
│password │    │type     │    │code     │    │status   │  │  ││seat_no  │
│role     │    │amenities│    │timezone │    │date     │  │  ││coach    │
│phone    │    │schedules│───┐│services │    │total    │  │  ││price    │
└─────────┘    └─────────┘   │└─────────┘    └─────────┘  │  │└─────────┘
                             │                            │  │
                    ┌────────▼───────┐                    │  │
                    │TrainSchedules  │                    │  │
                    │id              │                    │  │
                    │train_id        │◄───────────────────┘  │
                    │origin_station  │                       │
                    │dest_station    │                       │
                    │departure_time  │                       │
                    │arrival_time    │                       │
                    │available_seats │                       │
                    │price           │◄──────────────────────┘
                    └────────────────┘
```

## 🤝 Contributing <a name="contributing"></a>

We welcome contributions to improve the Train Booking System! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Run tests to ensure quality (`npm test` for frontend, `./mvnw test` for backend)
5. Commit your changes (`git commit -m 'Add some amazing feature'`)
6. Push to the branch (`git push origin feature/amazing-feature`)
7. Open a Pull Request

Please read our [Contributing Guidelines](CONTRIBUTING.md) for more details.

### Code Style
- Backend: Follow Google Java Style Guide
- Frontend: Use ESLint and Prettier with our configuration

## 📝 License <a name="license"></a>

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Contact

- **Developer:** Byteforce
- **GitHub:** http://krishmal.qzz.io/
- **Email:** krishmaldinidu5466@gmail.com

---

<p align="center">
  Made with ❤️ by Byteforce
  <br>
  Last updated: September 30, 2025
</p>
