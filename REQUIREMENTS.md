# Backend API Requirements - Logo Endpoints

This document outlines the requirements for implementing the Logo API endpoints. The data should be served based on the local `images.json` file.

## Data Source
The application should read from the `images.json` file located in the root directory.

**File Structure:**
```json
[
  {
    "id": 1,
    "title": "Tech Flow Logo",
    "path": "image/logos/tech_flow.png"
  },
  ...
]
```

---

## API Endpoints

### 1. Get All Logos
Returns a list of all image paths available in the system.

- **Endpoint:** `GET /api/logos/`
- **Response Type:** `application/json`
- **Success Response:**
  - **Code:** 200 OK
  - **Content:**
    ```json
    [
      "image/logos/tech_flow.png",
      "image/logos/eco_bright.png",
      "image/logos/nexus_point.png"
    ]
    ```

### 2. Get Logo by ID
Returns the full details of a specific logo entry based on its ID.

- **Endpoint:** `GET /api/logos/{id}`
- **Response Type:** `application/json`
- **Path Parameters:**
  - `id`: The unique identifier of the logo (e.g., 1).
- **Success Response:**
  - **Code:** 200 OK
  - **Content:**
    ```json
    {
      "id": 1,
      "title": "Tech Flow Logo",
      "path": "image/logos/tech_flow.png"
    }
    ```
- **Error Response:**
  - **Code:** 404 NOT FOUND
  - **Content:** `{"error": "Logo not found with ID: {id}"}`

---

## Implementation Notes
- Ensure the paths returned are relative to the root or absolute URLs if the server is hosting static assets.
- If using Spring Boot, consider creating a `Logo` DTO and a service that reads the JSON file once at startup or on every request (depending on performance requirements).
