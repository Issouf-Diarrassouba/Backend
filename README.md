🛠️ HouseMatch Backend
The HouseMatch backend is a scalable, secure, and modular REST API service built using Vapor (Swift) and FastAPI (Python) to support an iOS-based real estate matching application. It handles user authentication, property retrieval, geolocation filtering, and machine learning integration to deliver personalized housing recommendations.

🚀 Tech Stack
Primary Backend Framework: Vapor (Swift)

ML Service: FastAPI (Python)

Authentication & Realtime DB: Firebase

Database (Prototype): SQLite

External APIs: RapidAPI Realtor Search, Google Maps API

Deployment: AWS (EC2)

🔐 Authentication Module
User Registration & Login
Implements secure user registration and login using Firebase authentication tokens.

Session Management
Middleware validates all incoming requests and ensures authenticated access using tokens.

Password Recovery
Password reset and recovery functionalities integrated with Firebase Auth.

🏘 Property Data Integration
API Retrieval
Connects to external APIs (e.g., RapidAPI Realtor Search) to fetch real-time housing data.

Data Validation & Parsing
Cleans, verifies, and parses API responses before processing.

Backend Filtering
Supports search filtering based on:

Location

Price range

Bedrooms/Bathrooms

Property type

Database Caching (Prototype)
Stores fetched listings in a local SQLite database to reduce external API usage.

🌍 Geolocation Support
Google Maps API Integration
Translates user-provided or device-acquired locations into geospatial coordinates.

Nearby Property Search
Uses coordinates to pull and display properties within a defined radius.

Map UI Integration
Backend supports data for frontend map overlays and dynamic geolocation updates.

🤖 ML Model Integration
FastAPI Microservice
A separate Python-based FastAPI server hosts the machine learning model.

Recommendation Endpoint
Vapor backend sends user preferences and liked listings to the ML service.

Content-Based Filtering
ML recommends properties based on:

User-set preferences

Past likes/dislikes

Property features (e.g., square footage, price)

🔄 Data Flow Summary
User logs in via iOS app → Token validated via Firebase

Preferences sent to Vapor backend → Stored in Firebase or SQLite

User swipes/interacts → Preferences updated and sent to FastAPI

Property data pulled from external APIs or cache

Recommended listings served back to frontend via secure API

⚙️ Endpoints Overview
Endpoint	Method	Description
/auth/register	POST	Register new user
/auth/login	POST	Authenticate user credentials
/user/preferences	GET/POST	Fetch or update user housing preferences
/properties/search	GET	Search properties by filters (location, etc)
/properties/recommendations	GET	Fetch personalized property recommendations
/geolocation/nearby	GET	Return properties near user location

🧪 Testing & Scalability
Load tested for concurrent requests

Designed with modular components for independent scaling

ML service separated to ensure flexible deployment and performance tuning

📦 Deployment Notes
Vapor backend hosted on AWS EC2 with HTTPS and reverse proxy support

FastAPI deployed independently with CORS enabled for secure frontend access
