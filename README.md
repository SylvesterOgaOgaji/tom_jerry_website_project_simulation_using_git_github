# Tom & Jerry Website Project Simulation Using Git

This repository demonstrates a collaborative Git workflow simulation where two developers (Tom and Jerry) work on different parts of the same website simultaneously.

## Project Overview

In this simulation, we've created a simple scenario where:
- Tom works on updating the navigation bar
- Jerry works on adding contact information to the footer
- Both developers work simultaneously on their features
- Changes are merged in a controlled manner

## Git Workflow Steps

### Initial Setup

1. Configure Git with user information:
   ```bash
   git config user.name "SylvesterOgaOgaji"
   git config user.email "slyokoh@gmail.com"
   ```

2. Create and initialize a central repository:
   ```bash
   mkdir central_repo
   cd central_repo
   git init --bare
   ```

3. Clone the repository for each developer:
   ```bash
   git clone central_repo tom-repo
   git clone central_repo jerry-repo
   ```

### Tom's Initial Setup

1. Navigate to Tom's repository and create the initial HTML file:
   ```bash
   cd tom-repo
   nano index.html
   ```

2. Add and commit the initial HTML structure:
   ```bash
   git add index.html
   git commit -m "Initial commit of html structure by Tom"
   ```

3. Push to the central repository:
   ```bash
   git push origin master
   ```

### Both Developers Pull Changes

1. Jerry pulls the initial changes:
   ```bash
   cd ../jerry-repo
   git pull
   ```

### Tom and Jerry Create Feature Branches

1. Tom creates a branch for navigation updates:
   ```bash
   cd ../tom-repo
   git checkout -b update_navigation
   ```

2. Jerry creates a branch for contact information:
   ```bash
   cd ../jerry-repo
   git checkout -b add_contact_info
   ```

### Making Changes

1. Tom updates the navigation in index.html:
   ```bash
   # In tom-repo
   nano index.html
   # Edit navigation section to add more links
   git add index.html
   git commit -m "Updated navigation with additional links"
   git push origin update_navigation
   ```

2. Jerry adds contact info to the footer:
   ```bash
   # In jerry-repo
   nano index.html
   # Edit footer section to add contact information
   git add index.html
   git commit -m "Add contact information to footer"
   git push origin add_contact_info
   ```

### Merging Changes

1. Merge Tom's changes first:
   ```bash
   # In tom-repo
   git checkout master
   git pull
   git merge update_navigation
   git push origin master
   ```

2. Jerry updates his branch with Tom's changes:
   ```bash
   # In jerry-repo
   git checkout master
   git pull
   git checkout add_contact_info
   git merge master
   # Resolve any conflicts if needed
   git push origin add_contact_info
   ```

3. Merge Jerry's changes into master:
   ```bash
   # In jerry-repo
   git checkout master
   git merge add_contact_info
   git push origin master
   ```

4. Both developers update their master branches:
   ```bash
   # In tom-repo
   git checkout master
   git pull

   # In jerry-repo
   git checkout master
   git pull
   ```

## Final Result

The final `index.html` file contains both Tom's navigation updates and Jerry's contact information in the footer, demonstrating successful collaboration using Git's branching and merging capabilities.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Our Website</title>
</head>
<body>
    <nav>
        <ul>
            <li><a href="index.html">Home</a></li>
            <li><a href="about.html">About</a></li>
            <li><a href="services.html">Services</a></li>
            <li><a href="contact.html">Contact</a></li>
        </ul>
    </nav>
    <main>
        <h1>Welcome to our website</h1>
    </main>
    <footer>
        <p>&copy; 2025 Our Company</p>
        <p>Contact us: info@ourcompany.com | (555) 123-4567</p>
        <p>123 Main St, Anytown, USA</p>
    </footer>
</body>
</html>
```

## Key Git Commands Used

- `git config` - Configure Git settings
- `git init --bare` - Create a central repository
- `git clone` - Create local copies of repositories
- `git checkout -b` - Create and switch to new branches
- `git add` - Stage changes
- `git commit` - Record changes to the repository
- `git push` - Upload local changes to remote repository
- `git pull` - Fetch and integrate changes from remote repository
- `git merge` - Combine changes from different branches
- `git status` - Check the status of the working directory

## Lessons Learned

This simulation demonstrates how Git enables multiple developers to work on the same codebase simultaneously without conflicts. Key benefits observed:

1. **Isolated Development**: Each developer worked in their own branch without interference
2. **Conflict Prevention**: Structured workflow prevented overwriting each other's changes
3. **History Tracking**: All changes were tracked with descriptive commit messages
4. **Seamless Integration**: Changes were merged systematically into the main codebase

