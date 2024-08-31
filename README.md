**NetflixGPT Setup Guide:**

1. **Create React Project:**
   - Run the command: `npx create-react-app netflix-gpt` to create a basic React project from scratch. This will install Webpack as the bundler (not Parcel) and also downloaded bunch of libraries/dependencies for us like Jest for testing.
   - Remember to navigate into the project directory: `cd netflix-gpt`.

2. **Git Setup:**
   - Download and log in to GitHub on your PC.
   - Initialize Git: 
     ```bash
     git init
     ```
   - Link the remote repository:
     ```bash
     git remote add origin repo_link.git
     ```
   - For the initial commit:
     ```bash
     git add .
     git commit -m "initial commit message"
     git branch -M main
     git push -u origin main
     ```
   - For subsequent changes:
     ```bash
     git add .
     git commit -m "another message"
     git push origin main
     ```
   - Alternatively, you can use the 3 commands provided github to push existing code to the repository.

3. **Install Tailwind CSS:**
   - Install Tailwind CSS and initialize it:
     ```bash
     npm install -D tailwindcss
     npx tailwindcss init
     ```
   - Refer to the official Tailwind CSS installation guide for more details: [Tailwind CSS Installation](https://tailwindcss.com/docs/installation).

4. **Install React Router:**
   - Install the `react-router-dom` library:
     ```bash
     npm i -D react-router-dom
     ```

5. **Form Handling:**
   - Use the Formik library for creating and validating forms, especially for handling large forms efficiently.