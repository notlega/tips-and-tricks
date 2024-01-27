# Vercel GitHub Actions

This document will cover a method of connecting your Vercel project with GitHub Actions

## Prerequisites

- A Vercel Account
- A GitHub Account
- A Vercel Project
- A GitHub Repository

## Steps

### Vercel

Navigate to your Vercel project and click on the **Settings** tab

Navigate to the **Git** section and click on **Import Git Repository**

Select the GitHub repository you wish to connect to the Vercel project

Click on the **Import** button

#### Environment Variables

Navigate to your Vercel project and click on the **Settings** tab

Navigate to the **Environment Variables** section

Enter all the environment variables you wish to use in your project or click on the **Import** button to import them from a `.env` file

#### Secret Keys

##### Vercel Token

Navigate to your Vercel account settings and click on the **Tokens** tab

Enter a name for the token, select full scope, set the expiry to never and click on the **Create** button

Copy the token for later use

##### Vercel Organisation ID

Navigate to your Vercel account settings and click on the **General** tab

Scroll down to the **Vercel ID** section and copy the ID for later use

##### Vercel Project ID

Navigate to your Vercel project settings and click on the **General** tab

Scroll down to the **Project ID** section and copy the ID for later use

### GitHub

Navigate to your GitHub repository and click on the **Actions** tab

If you have not set up a workflow yet, click on the **Set up a workflow yourself** button

Else, click on the **New workflow** button

A new file will be created, name it `vercel-preview.yml`

Copy the following code into the file (this is for yarn)

```yml
name: Vercel Preview Deployment

env:
  VERCEL_ORG_ID: ${{ secrets.VERCEL_ORG_ID }}
  VERCEL_PROJECT_ID: ${{ secrets.VERCEL_PROJECT_ID }}

on:
  push:
    branches-ignore:
      - main # Change this to your main branch name

jobs:
  Deploy-Preview:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      - name: Install Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 18

      - name: Install Yarn
        run: npm install --global yarn@latest

      - name: Install Vercel CLI
        run: yarn global add vercel@latest

      - name: Pull Vercel Environment Information
        run: vercel pull --yes --environment=preview --token={{ secrets.VERCEL_TOKEN }}

      - name: Build Project Artifacts
        run: vercel build --token=${{ secrets.VERCEL_TOKEN }}

      - name: Deploy Project Artifacts to Vercel
        run: vercel deploy --prebuilt --token=${{ secrets.VERCEL_TOKEN }}
```

Click on the **Commit changes...** button to save the file

Repeat the above steps for the `vercel-production.yml`

Copy the following code into the file (this is for yarn)

```yml
name: Vercel Production Deployment

env:
  VERCEL_ORG_ID: ${{ secrets.VERCEL_ORG_ID }}
  VERCEL_PROJECT_ID: ${{ secrets.VERCEL_PROJECT_ID }}

on:
  push:
    branches:
      - main # Change this to the branch you want to deploy to production

jobs:
  Deploy-Production:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      - name: Install Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 18

      - name: Install Yarn
        run: npm install --global yarn@latest

      - name: Install Vercel CLI
        run: yarn global add vercel@latest

      - name: Pull Vercel Environment Information
        run: vercel pull --yes --environment=production --token=${{ secrets.VERCEL_TOKEN }}

      - name: Build Project Artifacts
        run: vercel build --prod --token=${{ secrets.VERCEL_TOKEN }}

      - name: Deploy Project Artifacts to Vercel
        run: vercel deploy --prebuilt --prod --token=${{ secrets.VERCEL_TOKEN }}
```

Click on the **Commit changes...** button to save the file

#### Environment Variables

Navigate to your GitHub repository and click on the **Settings** tab

Click on the **Secrets and variables** tab to expand it and click on the **Actions** tab

Click on the **New repository secret** button

Enter the name `VERCEL_TOKEN` and paste the token you copied earlier into the value field

Click on the **Add secret** button

Repeat the above steps for the `VERCEL_ORG_ID` and `VERCEL_PROJECT_ID` secrets
