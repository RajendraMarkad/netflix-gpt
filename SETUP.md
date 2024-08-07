NetflixGPT project setup:


### Create a basic React project from scratch:

```
npx create-react-app netflix-gpt
```

This will install Webpack as the bundler (not Parcel) and Jest for testing.

**Remember to navigate into your project directory:**

```bash
cd netflix-gpt
```

### Git Initialization

Initialize a new Git repository and set up the remote origin:

```bash
git init
git remote add origin <repo_link.git>
git add .
git commit -m "initial commit msg"
git push -u origin main
```

**For subsequent changes, use:**

```bash
git add .
git commit -m "another msg"
git push origin main
```

Alternatively, you can copy and paste the three commands given above to push your changes.

### Tailwind CSS

Install Tailwind CSS and initialize it:

```bash
npm install -D tailwindcss
npx tailwindcss init
```

For installation instructions, refer to the [Tailwind CSS Documentation](https://tailwindcss.com/docs/installation).

### React Router DOM

Install the React Router DOM library:

```bash
npm install -D react-router-dom
```

### ESLint Step-by-Step Configuration

1. **Create/Edit `.eslintrc.json` File:**

   If you don’t already have a `.eslintrc.json` file, create one in the root of your project. Add the following configuration to it:

   ```json
   {
     "env": {
       "browser": true,
       "es2021": true,
       "jest": true
     },
     "extends": [
       "plugin:react/recommended"
     ],
     "overrides": [],
     "parserOptions": {
       "ecmaVersion": "latest",
       "sourceType": "module"
     },
     "plugins": [
       "react"
     ],
     "rules": {
       "react/react-in-jsx-scope": "off",
       "semi": ["error", "always"],
       "quotes": ["error", "single"],
       "comma-dangle": ["error", "never"],
       "comma-spacing": "error",
       "no-multiple-empty-lines": ["error", { "max": 1, "maxEOF": 1 }],
       "react/no-unescaped-entities": 0
     }
   }
   ```

2. **Remove or Ignore `eslint.config.mjs`:**

   Since the `.eslintrc.json` will now hold your configuration, you can either remove the `eslint.config.mjs` file or ignore it to avoid conflicts. If you choose to keep it, ensure that your `.eslintrc.json` takes precedence.

### Explanation of `.eslintrc.json` Configuration

- **env**: Defines the environments your code runs in. This configuration includes `browser`, `es2021`, and `jest` for testing.
- **extends**: Extends the recommended configurations for React.
- **overrides**: You can add specific overrides here if needed, but it's empty for now.
- **parserOptions**: Specifies ECMAScript version and module type.
- **plugins**: Specifies the plugins used, here it’s just `react`.
- **rules**: Contains your custom rules:
  - `react/react-in-jsx-scope`: Turned off since React 17 doesn't require React to be in scope.
  - `semi`: Enforces the use of semicolons.
  - `quotes`: Enforces the use of single quotes.
  - `comma-dangle`: Disallows trailing commas.
  - `comma-spacing`: Enforces consistent spacing before and after commas.
  - `no-multiple-empty-lines`: Disallows multiple empty lines.
  - `react/no-unescaped-entities`: Turns off the rule that prevents unescaped entities in JSX.

### Usage

After setting up your `.eslintrc.json`, ensure ESLint is properly configured to read this file. You can run ESLint using:

```bash
npx eslint . --ext .js,.jsx,.ts,.tsx
```

This command will lint your JavaScript and TypeScript files in the project.

### Optional: Migrate `eslint.config.mjs` to `.eslintrc.json`

If you want to merge your existing `eslint.config.mjs` configuration into `.eslintrc.json`, you can manually combine the configurations. Here’s an example of how you might do this:

1. **Merge the Configuration:**

   ```json
   {
     "env": {
       "browser": true,
       "es2021": true,
       "jest": true
     },
     "extends": [
       "eslint:recommended",
       "plugin:react/recommended"
     ],
     "overrides": [],
     "parserOptions": {
       "ecmaVersion": "latest",
       "sourceType": "module"
     },
     "plugins": [
       "react"
     ],
     "rules": {
       "react/react-in-jsx-scope": "off",
       "semi": ["error", "always"],
       "quotes": ["error", "single"],
       "comma-dangle": ["error", "never"],
       "comma-spacing": "error",
       "no-multiple-empty-lines": ["error", { "max": 1, "maxEOF": 1 }],
       "react/no-unescaped-entities": 0
     }
   }
   ```

2. **Save and Run ESLint:**

   Ensure your `.eslintrc.json` file is saved and run ESLint as described earlier.

By following these steps, you can set up your ESLint configuration in a `.eslintrc.json` file with the rules you specified, ensuring your code adheres to the desired standards.


Here's a cheatsheet for integrating TypeScript, ESLint, and Prettier into your existing React project:

---

## TypeScript, ESLint, and Prettier Integration Cheatsheet

### Step 1: Install Required Packages

Install TypeScript, ESLint, Prettier, and necessary plugins:

```bash
npm install --save-dev typescript @types/node @types/react @types/react-dom @types/jest
npm install --save-dev eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin prettier eslint-plugin-prettier eslint-config-prettier
```

### Step 2: Create `tsconfig.json`

Initialize TypeScript configuration:

```bash
npx tsc --init
```

Update `tsconfig.json` (basic configuration):

```json
{
  "compilerOptions": {
    "target": "ES6",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "noFallthroughCasesInSwitch": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "react-jsx"
  },
  "include": ["src"],
  "exclude": ["node_modules"]
}
```

### Step 3: Rename Files

Rename your existing JavaScript files:

- `App.js` -> `App.tsx`
- `index.js` -> `index.tsx`

### Step 4: Update ESLint Configuration

Create or update `.eslintrc.json`:

```json
{
  "env": {
    "browser": true,
    "es2021": true,
    "jest": true
  },
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended",
    "plugin:@typescript-eslint/recommended",
    "prettier"
  ],
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaVersion": "latest",
    "sourceType": "module",
    "ecmaFeatures": {
      "jsx": true
    }
  },
  "plugins": [
    "react",
    "@typescript-eslint",
    "prettier"
  ],
  "rules": {
    "react/react-in-jsx-scope": "off",
    "semi": ["error", "always"],
    "quotes": ["error", "single"],
    "comma-dangle": ["error", "never"],
    "comma-spacing": "error",
    "no-multiple-empty-lines": ["error", { "max": 1, "maxEOF": 1 }],
    "react/no-unescaped-entities": "off",
    "prettier/prettier": "error",
    "@typescript-eslint/explicit-module-boundary-types": "off",
    "@typescript-eslint/no-explicit-any": "off"
  },
  "settings": {
    "react": {
      "version": "detect"
    }
  }
}
```

### Step 5: Add Prettier Configuration

Create `.prettierrc` file:

```json
{
  "singleQuote": true,
  "semi": true,
  "trailingComma": "es5",
  "tabWidth": 2,
  "printWidth": 80
}
```

### Step 6: Add Scripts to `package.json`

Update `package.json` to include linting and formatting scripts:

```json
"scripts": {
  "lint": "eslint . --ext .js,.jsx,.ts,.tsx",
  "format": "prettier --write \"src/**/*.{js,jsx,ts,tsx}\"",
  "lint:fix": "eslint . --ext .js,.jsx,.ts,.tsx --fix"
}
```

### Step 7: Test the Setup

Run ESLint to ensure everything is set up correctly:

```bash
npx eslint .
```

Run Prettier to format your code:

```bash
npm run format
```

---

This cheatsheet provides a concise guide for setting up TypeScript, ESLint, and Prettier in your existing React project, ensuring a consistent and high-quality codebase.

