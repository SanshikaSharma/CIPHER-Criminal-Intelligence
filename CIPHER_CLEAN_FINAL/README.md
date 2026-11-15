# CIPHER — Criminal Intelligence & Pattern Heuristic Engine

CIPHER is an AI-powered criminal intelligence and investigation platform designed to analyze fragmented evidence, discover hidden relationships, and visualize complex criminal networks through artificial intelligence, graph analytics, geospatial intelligence, and face analysis.

---

# 1. Project Overview

CIPHER helps investigators analyze information from different sources and connect related entities such as:

- Individuals and suspects
- Organizations and criminal groups
- Locations and addresses
- Events and incidents
- Phone call records (CDRs)
- Financial transactions
- Evidence and investigation records

The platform aims to transform disconnected information into meaningful intelligence through relationship analysis, visualizations, and AI-assisted investigation.

# 2. Core Features

## 2.1 Case Data Management
- Upload and process CSV-based case datasets.
- Organize investigation-related information.
- Connect people, events, locations, and transactions.
- Maintain structured case information.

## 2.2 Criminal Network Analysis
- Identify relationships between connected entities.
- Represent relationships through interactive graph visualization.
- Explore connections between individuals and organizations.
- Analyze possible patterns in criminal networks.

## 2.3 GIS and Location Intelligence
- Visualize investigation-related locations.
- Connect addresses and geographical information.
- Support location-based investigation and analysis.

## 2.4 OSIRIS 3D Visualization
- Integrated OSIRIS 3D visualization module.
- Accessible through CIPHER's `/osiris/` same-origin route.
- Runs privately behind the main CIPHER application.

## 2.5 Face Analysis
- ArcFace-based face analysis integration.
- Support for face-related investigation workflows.
- Connect face analysis results with investigation entities where supported.

## 2.6 AI Integration
- Google Gemini API integration.
- AI-assisted investigation capabilities.
- Support for intelligent analysis workflows.

# 3. Technology Stack

| Component | Technology |
|---|---|
| Frontend | Next.js |
| Backend | Python |
| API Framework | FastAPI |
| Graph Database | Neo4j Aura |
| Database | Supabase |
| AI Integration | Google Gemini |
| Face Analysis | ArcFace |
| 3D Visualization | OSIRIS |
| Containerization | Docker |
| Deployment | Render |
| Version Control | Git and GitHub |

# 4. System Architecture

CIPHER uses a frontend, backend, database, and AI integration architecture.

### Frontend
Provides the user interface, case management, dashboards, GIS views, and graph visualization.

### Backend
Processes uploaded information, manages application logic, handles API requests, and coordinates integrations.

### Database Layer
Supabase supports structured application data and storage workflows. Neo4j supports graph-based relationship analysis.

### AI Layer
Google Gemini supports AI-assisted analysis, while ArcFace provides face-analysis capabilities.

### Visualization Layer
Graph visualization, GIS, and OSIRIS 3D provide visual investigation interfaces.

# 5. Local Windows Setup

Use only:

- `Start_Cipher.bat` — start the complete application.
- `Stop_Cipher.bat` — stop the complete application.

## Start

1. Double-click `Start_Cipher.bat`.
2. Wait for **CIPHER IS READY**.
3. The application automatically opens:

   `http://127.0.0.1:8000/`

Then navigate:

**Login → GIS → OSIRIS 3D**

Do not open `127.0.0.1:3001` manually. OSIRIS runs privately behind CIPHER's `/osiris/` same-origin route.

## First Start

The first start can take several minutes because:

- Python dependencies may need to be installed.
- OSIRIS Node dependencies may need to be installed.
- The OSIRIS production build may need to be created.

## If OSIRIS Does Not Start

`Start_Cipher.bat` waits for OSIRIS `/api/health` before starting CIPHER.

If OSIRIS cannot start, the launcher prints the OSIRIS log and stops instead of leaving a misleading CIPHER-only startup with `/osiris/` returning HTTP 503.

## Stop

Double-click:

`Stop_Cipher.bat`

This stops the complete application.

# 6. Deployment

For Docker/Render deployment, use:

- Root `Dockerfile`
- `render.yaml`

OSIRIS is built into the same container and remains private on loopback. Only CIPHER's public HTTP port is exposed.

## Deployment Services

### GitHub
Repository:

`https://github.com/SanshikaSharma/CIPHER-Criminal-Intelligence.git`

GitHub is used for source-code version control and deployment integration.

### Render
Render is used to host the application using Docker.

### Supabase
Supabase provides the database and storage infrastructure.

### Neo4j Aura
Neo4j Aura provides graph database connectivity.

### Google Gemini
Gemini API provides AI integration.

## Deployment Progress

The following setup work has been completed:

- Supabase project created.
- Supabase project URL and secret configured in Render.
- Database connection string configured in Render.
- Neo4j Aura instance created and running.
- Neo4j connection URL and credentials configured in Render.
- Google Gemini API key created and configured in Render.
- Render service connected to the GitHub repository.
- Docker-based deployment configuration prepared.

### Current Pending Deployment Tasks

- Push the latest project code to GitHub.
- Resolve the Render deployment failure (exit status 128).
- Verify successful Docker image build.
- Verify backend startup and health endpoint.
- Verify Supabase database connectivity.
- Apply required Supabase SQL migrations.
- Create and configure the `cipher-evidence` storage bucket.
- Verify Neo4j graph connectivity.
- Test Gemini API integration.
- Test all application modules on the deployed application.
- Verify the final public deployment URL.

**Deployment status:** In progress. A successful production deployment has not yet been confirmed.

# 7. Database and Environment Configuration

The project uses environment variables for external service connections.

Required deployment variables include:

- `DATABASE_URL`
- `SECRET_KEY`
- `SUPABASE_URL`
- `SUPABASE_SERVICE_ROLE_KEY`
- `NEO4J_URI`
- `NEO4J_USERNAME`
- `NEO4J_PASSWORD`
- `GEMINI_API_KEY`

Never commit actual passwords, API keys, or secret values to GitHub.

Use Render Environment Variables for production credentials and a protected local environment file for local development.

# 8. Data Processing Workflow

The intended investigation workflow is:

1. Upload case-related CSV data.
2. Validate and process the uploaded information.
3. Identify entities such as people, events, locations, and transactions.
4. Establish relationships between relevant entities.
5. Store and retrieve structured and graph data.
6. Analyze relationships and possible patterns.
7. Visualize investigation networks and geographical connections.
8. Use AI-assisted analysis where supported.
9. Present relevant information through the investigation interface.

# 9. Future Development Plans

The following are planned improvements and should not be considered completed features until implemented and tested.

## AI and Intelligence
- AI Investigation Copilot.
- Automated evidence correlation.
- Hidden relationship detection improvements.
- Evidence Gap Detector.
- Intelligent investigation summaries.

## Graph Analytics
- Advanced relationship discovery.
- Improved graph filtering and exploration.
- Better detection of interconnected entities.
- Enhanced investigation timelines.

## Evidence Management
- Improved evidence upload and organization.
- Evidence metadata and traceability.
- Better cross-source evidence correlation.
- Improved investigation record management.

## Face Analysis
- Improve face-analysis workflows.
- Improve matching and entity association.
- Better integration with investigation records.

## GIS and Visualization
- Advanced geographical analysis.
- Improved location-based relationship visualization.
- Better OSIRIS 3D integration.
- More interactive investigation dashboards.

## Security and Reliability
- Authentication and role-based access control improvements.
- Secure evidence access.
- Database security and access-policy improvements.
- Performance optimization.
- Deployment monitoring and error handling.

# 10. Development and Maintenance Guidelines

- Preserve existing working functionality when modifying code.
- Review the existing project structure before changing files.
- Keep frontend and backend integrations consistent.
- Never expose API keys, passwords, or private credentials.
- Test important changes before deployment.
- Keep deployment configuration synchronized with application requirements.
- Clearly distinguish completed, in-progress, pending, and planned features.
- Record significant bugs, fixes, and configuration changes.
- Avoid unnecessary changes to working modules.

# 11. Project Development Status

| Area | Current Status |
|---|---|
| Core application | Existing implementation |
| CSV case processing | Implemented workflow |
| Graph visualization | Existing implementation |
| GIS integration | Existing implementation |
| OSIRIS 3D | Integrated |
| ArcFace | Integrated |
| Gemini API configuration | Configured |
| Supabase project | Created and configured |
| Neo4j Aura | Instance running and configured |
| GitHub | Repository connected; latest push pending |
| Render deployment | Troubleshooting in progress |
| Production testing | Pending |
| Future AI improvements | Planned |

# 12. Project Summary

CIPHER brings together case data processing, graph-based criminal network analysis, geographical intelligence, face analysis, AI integration, and 3D visualization in one investigation platform.

Its development focuses on improving how fragmented investigation information can be organized, connected, analyzed, and presented.

The project will continue evolving through improved intelligence capabilities, evidence management, visualization, security, and deployment reliability.

---

**CIPHER — Connect Evidence. Discover Relationships. Build Intelligence.**