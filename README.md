# RaceDayy
<img width="1904" height="1017" alt="image" src="https://github.com/user-attachments/assets/efb94577-9303-4340-bb7c-a467e00e1b12" />


# RaceDay API - Part 2: Restful API Development

## Project Overview
The RaceDay API is the backend backbone for the RaceDay event management system. Built using ASP.NET Core Web API and C#, this API handles all data operations, enforces role-based access, and manages the core business logic for events, participants, and organisers.

This project is developed as part of the Part 2 requirements, serving as the backend for the MVC front-end that will be built in Part 3.

## Tech Stack and Tools
- Framework: ASP.NET Core Web API (C#)
- Database: SQL Server
- ORM: Entity Framework Core
- Authentication: Session-based Authentication (Role-Based)
- Testing: Unit Testing (xUnit / NUnit)
- CI/CD: GitHub Actions

## Functional Requirements Implemented

### 1. Authentication and User Management
- Role-Based Registration: Users can register as either an Organiser or a Participant.
- Secure Login: Session management is implemented to maintain the user's authenticated state and role across subsequent requests.
- Security: Passwords are securely hashed before being stored in the database.
- Access Control:
  - Non-public endpoints are strictly restricted to authenticated users.
  - Strict segregation of duties: Organiser functionality is blocked for Participants and vice versa.

### 2. User Profiles
- Both Organisers and Participants can view and update their own profile information.

### 3. Events Management
- Organisers: Can Create, Read, Update, and Delete (CRUD) events.
- Participants: Can view available events.
- Event Attributes: Each event captures Name, Description, Date, Location, Distance, and Event Type (Run, Walk, Cycle).

### 4. Categories
- Organisers: Can define age or distance categories for each specific event (e.g., Under 20, Senior, 10km, 21km).
- Participants: Can view the available categories for any event.

### 5. Event Enrolments
- Participants: Can enter an event by selecting a specific category. The system accurately records the link between the Participant, the Event, and the selected Category.
- Organisers: Can view a complete list of all enrolments for the events they manage.

### 6. Results
- Organisers: Can capture and record finish times and finishing positions for Participants after an event concludes.
- Participants: Can view their own personal results.

## Getting Started

### Prerequisites
- .NET SDK (Version 8.0 or later recommended)
- SQL Server (LocalDB or full instance)
- Visual Studio 2022 or VS Code

### Installation and Setup
1. Clone the repository:
   git clone https://github.com/your-username/RaceDay-API.git
   cd RaceDay-API

2. Configure the Database:
   Open appsettings.json (or appsettings.Development.json).
   Update the ConnectionStrings:DefaultConnection with your SQL Server credentials.

3. Apply Entity Framework Migrations:
   Ensure your database schema matches the Part 1 ERD and SQL script.
   dotnet ef database update

4. Run the Application:
   dotnet run
   The API will typically be available at https://localhost:[port] and http://localhost:[port]. You can test the endpoints using Swagger (usually found at /swagger).

## Testing
Unit tests have been written for the API endpoints to ensure reliability and correct business logic.
To run the tests, use the following command in the root directory:
dotnet test

## CI/CD Pipeline
This repository is configured with GitHub Actions for automated CI/CD. Every push or pull request to the main branch will trigger an automated workflow that restores dependencies, builds the project, and runs the unit test suite.

## Project Structure
- Controllers/: API endpoints and routing.
- Models/: Entity classes mapping to the database (Users, Events, Categories, etc.).
- Data/: Entity Framework DbContext and configurations.
- Services/: Business logic (e.g., Authentication, Password Hashing).
- Tests/: Unit testing project.

---
The Independent Institute of Education (Pty) Ltd 2026. Built for educational purposes.
