# GitHub Actions Demo with React

This repository demonstrates how to use GitHub Actions with a React application.

## Project Structure

- `.github/workflows/egg.yaml`: Contains the GitHub Actions workflow configuration
- `react-app/`: Contains the React application code

## Local Development

To run the application locally:

1. Navigate to the react-app directory:
   ```bash
   cd react-app
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm start
   ```

4. Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

## GitHub Actions Workflow

The workflow will:
1. Check out the code
2. Set up Node.js
3. Install dependencies
4. Build the application
5. Run tests

The workflow is triggered on every push to the repository.


