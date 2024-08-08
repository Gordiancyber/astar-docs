---

# Astar Network Documentation

A documentation for Astar Network, focusing on zkEVM and Parachain technologies. The documentation is built using Docusaurus, a modern static site generator.

## Description

This project aims to provide a well-structured, version-controlled, and automatically updated documentation site for Astar Network. The documentation is hosted on GitHub Pages and is automatically deployed whenever changes are merged into the main branch, using GitHub Actions.

## Table of Contents

- [Getting Started](#getting-started)
- [Forking the Project](#forking-the-project)
- [Documentation Structure](#documentation-structure)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)

## Getting Started

To get a local copy up and running, follow these steps:

### Prerequisites

- Node.js (version 14 or higher)
- npm (version 6 or higher)
- Git

### Installation

1. **Fork the repository**: Fork the Astar Network documentation repository on GitHub to your own account by clicking the "Fork" button on the repository's page.

2. **Clone your forked repository**:

    ```sh
    git clone https://github.com/<YOUR_USERNAME>/<REPO_NAME>.git
    ```

    Replace `<YOUR_USERNAME>` with your GitHub username and `<REPO_NAME>` with the name of the repository.

3. **Navigate to the project directory**:

    ```sh
    cd <REPO_NAME>
    ```

4. **Install the dependencies**:

    ```sh
    npm install
    ```

5. **Start the development server**:

    ```sh
    npm start
    ```

    This will start the local development server and open the documentation site in your default web browser.

## Forking the Project

To contribute to the Astar Network documentation, you need to fork the project. Here’s how you can do that:

1. **Fork the Repository**: Go to the Astar Network documentation repository on GitHub. Click on the "Fork" button in the top-right corner. This will create a copy of the repository under your GitHub account.

2. **Clone Your Fork**: After forking, clone the repository to your local machine:

    ```sh
    git clone https://github.com/<YOUR_USERNAME>/<REPO_NAME>.git
    ```

3. **Add Upstream Remote**: To keep your forked repository in sync with the original repository, you need to add an "upstream" remote:

    ```sh
    git remote add upstream https://github.com/<ORIGINAL_USERNAME>/<REPO_NAME>.git
    ```

4. **Fetch Upstream Changes**: Before starting any work, always fetch the latest changes from the upstream repository:

    ```sh
    git fetch upstream
    ```

5. **Create a New Branch**: Always create a new branch for your changes:

    ```sh
    git checkout -b <BRANCH_NAME>
    ```

## Documentation Structure

```
.
├── docs
│   ├── intro.md
│   ├── zkEVM
│   │   ├── overview.md
│   │   └── setup.md
│   └── parachain
│       ├── overview.md
│       └── setup.md
├── docusaurus.config.js
├── package.json
└── .github
    └── workflows
        └── deploy.yml
```

- `docs/`: Contains the markdown files for the documentation.
- `docusaurus.config.js`: Configuration file for Docusaurus.
- `.github/workflows/deploy.yml`: GitHub Actions workflow for automated deployment.

## Deployment

The documentation site is automatically deployed to GitHub Pages whenever changes are merged into the main branch. This is achieved using GitHub Actions.

### Step-by-Step Guide

1. **Configure Docusaurus for GitHub Pages**

    Update the `docusaurus.config.js` file with your GitHub Pages configuration:

    ```js
    module.exports = {
      // ... other configurations
      url: 'https://<USERNAME>.github.io',
      baseUrl: '/<REPO_NAME>/',
      // ... other configurations
    };
    ```

    Replace `<USERNAME>` with your GitHub username and `<REPO_NAME>` with your repository name.

2. **Create GitHub Actions Workflow**

    Create a new directory called `.github/workflows` in the root of your project, and inside it, create a file named `deploy.yml`.

    ```yaml
    name: Deploy Docusaurus site to GitHub Pages

    on:
      push:
        branches:
          - main  # Trigger the workflow on push to the main branch

    jobs:
      build:
        runs-on: ubuntu-latest

        steps:
          - name: Checkout repository
            uses: actions/checkout@v2

          - name: Set up Node.js
            uses: actions/setup-node@v2
            with:
              node-version: '14'

          - name: Install dependencies
            run: npm install

          - name: Build the site
            run: npm run build

          - name: Deploy to GitHub Pages
            uses: peaceiris/actions-gh-pages@v3
            with:
              github_token: ${{ secrets.GITHUB_TOKEN }}
              publish_dir: ./build
    ```

3. **Commit and Push Workflow File**

    Commit the new workflow file and push it to your repository:

    ```sh
    git add .github/workflows/deploy.yml
    git commit -m "Add GitHub Actions workflow for deploying site"
    git push origin main
    ```

4. **Merge PRs to Main Branch**

    Once the workflow is set up, any changes merged into the main branch will trigger the GitHub Actions workflow. The workflow will build your Docusaurus site and deploy it to GitHub Pages automatically.

## Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

MIT License.

---

