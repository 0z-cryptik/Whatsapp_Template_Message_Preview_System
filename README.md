# WhatsApp Template Message Preview System

This project provides a **Template Message Preview System** with a simple frontend and backend setup. It allows users to enter a message template containing placeholders (variables), such as `"hi my name is {{name}} and I'm from {{country}}"`. The frontend dynamically generates input fields for each placeholder, captures user input, and sends it to the backend. The backend then substitutes the placeholders with the provided values and returns the fully formatted message.

## Features

- **Dynamic Form Generation**: Based on the template input, the frontend dynamically creates form fields for each variable in the template.
- **Template Parsing**: The backend processes the template by substituting placeholder variables with user-provided values.
- **Display Formatted Message**: The frontend displays the fully formatted message after receiving it from the backend.
- **Enhanced Error Handling**: Displays user-friendly messages for missing or incorrect inputs.
- **Validation**: Add input validation to ensure required variables are provided.

## Setup Instructions

### Prerequisites

- Node.js (v14 or later recommended)
- npm (usually comes with Node.js)

### Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/0z-cryptik/Whatsapp_Template_Message_Preview_System.git
   cd Whatsapp_Template_Message_Preview_System
   ```

2. **Install Dependencies**:
   ```bash
   # Initialize the submodules
   git submodule update --init --recursive
   ```

   Then, navigate to the `frontend` and `backend` directories to install the required packages.

   ```bash
   # For the backend
   cd backend
   # make sure you are on the devEnvironment branch
   git checkout devEnvironment
   npm install

   # For the frontend
   cd ../frontend
   npm install
   ```

3. **Set Up Environment Variables**:
   In the root of both `frontend` and `backend` folders, create `.env` files with the necessary environment variables.

4. **Run the Application**:

   ```bash
   # Start the backend server
   cd backend
   npx tsx index.ts

   # Start the frontend server
   cd ../frontend
   npm run dev
   ```

The application should now be running locally. You can test it by navigating to the frontend's development URL (usually `http://localhost:3000`).

## API Documentation

### Endpoint: `/server`

- **Method**: POST
- **Description**: Receives a template with user-inputted values for placeholders and returns the formatted message with placeholders substituted.
- **Request Body**: JSON

  - `template`: The template string, containing placeholders in the `{{variable}}` format.
  - `variables`: Object containing values for each placeholder.

- **Response**:

  - **Status**: 200 (OK)
  - **Body**: The formatted message as a string.

- **Example Request**:

  ```json
  {
    "template": "Hi my name is {{name}} and I'm from {{country}}",
    "variables": {
      "name": "Musa",
      "country": "Namibia"
    }
  }
  ```

- **Example Response**:

  ```json
  {
    "ok": true,
    "message": "Hi my name is Musa and I'm from Namibia"
  }
  ```

## Approach Explanation

The project consists of two main parts:

1. **Frontend**:
   - Accepts a template input from the user.
   - Extracts variables from the template and dynamically generates input fields for each placeholder.
   - Sends the template and user-provided values to the backend and displays the response message.

2. **Backend**:
   - Receives the template and variable values from the frontend.
   - Uses a regular expression to identify placeholders and replace them with the values provided.
   - Returns the formatted message back to the frontend for display.

## Future Improvements

- **Template Storage**: Save templates and past messages for user history and reuse.
- **User Authentication**: Enable user accounts to secure personal templates.
```