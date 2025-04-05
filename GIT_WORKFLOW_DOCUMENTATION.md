# Git Workflow Simulation: Tom & Jerry Website Collaboration

## GitHub Repository URL

https://github.com/SylvesterOgaOgaji/tom_jerry_website_project_simulation_using_git_github

## Project Overview

This project demonstrates a collaborative Git workflow simulation where two developers (Tom and Jerry) work on different parts of the same website simultaneously. Through this simulation, I demonstrate how Git functions as a distributed version control system (VCS) to manage code changes from multiple contributors without conflicts.

## Git Commands Execution Evidence

### Initial Setup: Git Configuration

![Git Configuration](./screenshots/1.%20Configure%20Git%20with%20your%20name%20and%20email.jpg)

The image shows the setup of Git with personal identification information:
```bash
git config user.name "SylvesterOgaOgaji"
git config user.email "slyokoh@gmail.com"
```

I also used `git config --list` to verify all configuration settings in the environment.

### Creating the Central Repository

![Central Repository Creation](./screenshots/2.%20Create%20a%20central%20repository.jpg)

I created a central bare repository to simulate a remote server:
```bash
mkdir central_repo
cd central_repo
git init --bare
```

The terminal shows successful initialization with the message: "Initialized empty Git repository in C:/Users/Sylvester/Documents/central_repo/" with "(BARE:master)" indicating a bare repository.

### Cloning the Repository for Developers

![Repository Cloning](./screenshots/3.%20Clone%20the%20repository%20as%20Tom%20and%20Jerry.jpg)

I created local working copies for both developers:
```bash
git clone central_repo tom-repo
git clone central_repo jerry-repo
```

The terminal shows warnings about cloning empty repositories, which is expected at this stage.

### Creating and Adding Initial HTML File

![Creating HTML File](./screenshots/4.%20Tom%20create%20the%20file%20with%20a%20text%20editor%20using%20nano.jpg)

In Tom's repository, I created the initial index.html file:
```bash
cd tom-repo
nano index.html
```

### Adding and Committing the Initial File

![Initial Commit](./screenshots/5.%20Git%20add%20and%20commit%20by%20Tom.jpg)

After creating the HTML file, I added and committed it to the repository:
```bash
git add index.html
git commit -m "Initial commit of html structure by Tom"
```

The terminal shows the successful commit with details: "1 file changed, 20 insertions(+)"

### Pushing Initial Content to Central Repository

![First Push](./screenshots/6.%20Tom%20push%20to%20master.jpg)

After initially encountering an error with branch naming, I successfully pushed to the central repository:
```bash
git branch  # Verified branch name is "master"
git push origin master
```

The output shows successful push with enumeration of objects and compression statistics.

### Pulling Updates in Jerry's Repository

![Jerry Pulling](./screenshots/7.%20Switched%20to%20Jerry%20Repo%20and%20Pulled%20the%20changes.jpg)

In Jerry's repository, I pulled the latest changes from the central repository:
```bash
cd ../jerry-repo
git pull
```

The terminal shows objects being received and unpacked, confirming successful synchronization.

### Creating Feature Branches

![Creating Feature Branches](./screenshots/8.%20change%20to%20tom%20repo%20and%20switched%20branch.jpg)

I created separate feature branches for both developers:
```bash
# In Tom's repository
cd ../tom-repo
git checkout -b update_navigation

# In Jerry's repository
cd ../jerry-repo
git checkout -b add_contact_info
```

Each command shows confirmation with "Switched to a new branch" message.

### Tom's Changes: Navigation Update

![Tom Editing Navigation](./screenshots/9.%20Jerry%20branched%20to%20add_contact_info.jpg)

In Tom's branch, I modified the navigation section of index.html:
```bash
nano index.html
```

### Tom Committing and Pushing Changes

![Tom Commit and Push](./screenshots/11.%20Tom%20added,%20committed%20and%20pushed%20to%20update_navigation.jpg)

After making changes to the navigation, I committed and pushed the changes:
```bash
git add index.html
git commit -m "Updated navigation with additional links"
git push origin update_navigation
```

The terminal shows "1 file changed, 4 insertions(+), 2 deletions(-)" and successful push to the update_navigation branch.

### Jerry's Changes: Footer Update

![Jerry Editing Footer](./screenshots/9.%20Jerry%20branched%20to%20add_contact_info.jpg)

Similarly, in Jerry's branch, I modified the footer section:
```bash
cd ../jerry-repo
nano index.html
```

### Jerry Committing and Pushing Changes

![Jerry Commit and Push](./screenshots/15.%20jerry%20checkout%20merge%20add%20and%20commit.jpg)

After adding contact information to the footer, I committed and pushed the changes:
```bash
git add index.html
git commit -m "Add contact information to footer"
git push origin add_contact_info
```

The terminal confirms successful commit with "1 file changed, 4 insertions(+), 2 deletions(-)" and successful push to add_contact_info branch.

### Merging Tom's Changes First

![Merging Tom's Branch](./screenshots/13.%20merge%20and%20push%20to%20master.jpg)

In Tom's repository, I merged his navigation updates to the master branch:
```bash
git checkout master
git pull  # Ensure main branch is up to date
git merge update_navigation
git push origin master
```

The terminal shows a successful merge with "Fast-forward" and "1 file changed, 4 insertions(+), 2 deletions(-)".

### Jerry Updates His Branch with Tom's Changes

![Jerry Updates Branch](./screenshots/15.%20jerry%20checkout%20merge%20add%20and%20commit.jpg)

Jerry needs to incorporate Tom's changes before his own can be merged:
```bash
cd ../jerry-repo
git checkout master
git pull  # Get Tom's changes
git checkout add_contact_info
git merge master
```

The terminal shows successful merge of Tom's changes into Jerry's branch.

### Resolving Potential Conflicts

![Jerry Resolving Conflicts](./screenshots/14.%20change%20to%20jerry%20checkout%20and%20pull.jpg)

In this case, Git was able to automatically merge the changes since Tom and Jerry modified different sections of the file. The merge was made by the 'ort' strategy, showing "1 file changed, 4 insertions(+), 2 deletions(-)".

### Merging Jerry's Changes to Master

![Merging Jerry's Branch](./screenshots/17.%20changed%20to%20Tom%20checkout%20and%20pull.jpg)

Finally, I merged Jerry's changes into the master branch:
```bash
git checkout master
git merge add_contact_info
git push origin master
```

The terminal shows a successful merge with details about updating references.

### Verifying the Final Result

![Final HTML Content](./screenshots/18.%20This%20verifies%20the%20changes.jpg)

To verify the final state, I viewed the content of index.html:
```bash
cat index.html
```

The output shows the complete HTML file with both Tom's navigation links and Jerry's contact information in the footer.

## GitHub Integration Evidence

### GitHub Dashboard

![GitHub Dashboard](./screenshots/GitHub%20Dashbaord%20showing%20Repo.jpg)

This screenshot shows my GitHub dashboard with the tom_jerry_website_project_simulation_using_git_github repository visible, confirming successful hosting on GitHub.

### GitHub Repository with Contents

![GitHub Repository](./screenshots/GitHub%20Dashbaord%20showing%20Repo.jpg)

This screenshot displays the repository contents on GitHub, showing:
- index.html file is present at the root
- README.md documentation
- All project files are successfully pushed to GitHub

## Benefits Demonstrated Through This Simulation

1. **Concurrent Development**: Tom and Jerry worked simultaneously on different features without interfering with each other's work.
   
2. **Branch Isolation**: Each developer's changes remained isolated in their feature branches until ready for integration.
   
3. **Controlled Integration**: Changes were merged in a systematic order, with Tom's navigation changes integrated first, followed by Jerry's footer updates.
   
4. **Conflict Prevention**: By working on different sections of the same file, potential conflicts were minimized and automatically handled by Git.
   
5. **Version History Preservation**: Each commit maintained a record of who made what changes and when, creating a comprehensive project history.

