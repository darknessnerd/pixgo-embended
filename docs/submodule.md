# Git submodules

A Git submodule is a repository embedded inside another Git repository. It allows you to keep a Git repository as a
subdirectory of another Git repository. This is useful for including libraries or other dependencies in your project 
while keeping their histories separate.

## Adding a Submodule

To add a submodule to your repository, use the following command:
```bash
git submodule add <repository-url> <path>
```
Replace `<repository-url>` with the URL of the repository you want to add as a submodule
and `<path>` with the directory where you want to place the submodule.
For example:
```bash
git submodule add https://github.com/lvgl/lvgl.git lvgl
```
This command will clone the `lvgl` repository into a directory named `lvgl` in your project.
## Cloning a Repository with Submodules

When you clone a repository that contains submodules, you need to initialize and update the submodules using:
```bash
git clone <repository-url>
cd <repository-directory>
git submodule update --init --recursive
```
This will clone the main repository and initialize and update all submodules recursively.
### Use a specific version of the submodule
By default, when you add a submodule, it points to the latest commit on the default branch of the submodule repository. 
If you want to use a specific version (commit, tag, etc... ) of the submodule, you can navigate to the submodule directory
after adding it and checkout the desired version:
```bash
cd <submodule-path>
git checkout <commit-hash-or-tag>
```
Then, go back to the main repository and commit the change:
```bash
cd ..
git add <submodule-path>
git commit -m "Set submodule <submodule-path> to specific version"
```
## Updating Submodules
To update a submodule to the latest commit from its remote repository, navigate to the submodule directory and run:
```bash
cd <submodule-path>
git pull origin <branch>
```
Replace `<submodule-path>` with the path to your submodule and `<branch>` with the branch you want to pull from (usually `main` or `master`).
After updating the submodule, you need to commit the changes in the main repository:
```bash
cd ..
git add <submodule-path>
git commit -m "Updated submodule <submodule-path>"
```
## Removing a Submodule
To remove a submodule, follow these steps:
1. Delete the submodule entry from the `.gitmodules` file:
   ```bash
   git config -f .gitmodules --remove-section submodule.<submodule-path>
   ```
2. Remove the submodule from the index:
   ```bash
   git rm --cached <submodule-path>
   ```
3. Delete the submodule directory:
   ```bash
   rm -rf <submodule-path>
   ```
4. Commit the changes:
   ```bash
   git commit -m "Removed submodule <submodule-path>"
   ```
5. Optionally, remove the submodule's entry from the `.git/config` file:
   ```bash
   git config -f .git/config --remove-section submodule.<submodule-path>
   ```
## Summary
Git submodules are a powerful way to include external repositories within your own project while keeping their histories
 separate. By following the steps outlined above, you can easily add, update, and remove submodules
as needed.