
# 1. SAS Studio - Working with GIT Branches
<br>

## Exercise Description

In this exercise, you will work with GIT branches in SAS Studio.
<br>

## Exercise Preparation

1. Open the **Google Chrome** browser on your Windows RACE Image.
1. Select the **SAS Viya** bookmark.
1. Enter the following:
   - User ID: **student**
   - Password: **Metdata0**

1. Click **Sign In**.
1. Select ![Viya Menu Selector](img/HamburgerMenu.png) **&#10132; Develop Code and Flows** to open *SAS Studio*.

## Create a Branch

1. Select ![](img/GITIcon.png) to view the **GIT** tab in *SAS Studio*.
2. *Double click* the **myGitFolder** icon.
3. Select the **History** tab.
4. *Right click* on the most recent commit row and select **Create new branch**.
   >Note:  You can create a branch on any commit.  All of the changes after the commit will be ignored.

5. Name your branch **feature/T-545-report-change**.
   >Note: This is typical branch naming convention. **feature** denotes the type of branch.  Others are **bug-fix**, **release**, **hot-fix**, etc..  **T-545** denotes a task ID from **Jira**. The suffix is a description of the feature.

6. Leave the checkboxes as they are and click **Create**.

<br>

![](img/NewBranch.png)

# Merge a Branch into Main

1. Select ![](img/ExplorerIcon.png) to view the **Explorer** tab in *SAS Studio*.
2. *Double click* the **TopNCategories.sas** file in **myGitFolder** to open it.
3. In the program editor, change the **category** macro variable from **Origin** to **Type** in both the **%let** statement as well as the report title.
4. Save the file.
   ![](img/titleChange.png)

5. Select ![](img/GITIcon.png) to view the **GIT** tab in *SAS Studio*.
6. Select the **feature/T-545-report-change** branch
7. As you did in the earlier exercises, stage and commit the changes with the comment "Report Change".
8. Select the **History** tab and note that the feature branch is ahead of the main branch with the changes you made.
9. Switch to the main branch.
10. *Right Click* feature branch commit that is ahead of the main branch and select **Merge into main** and select the feature branch.
    ![](img/MergeBranch.png)
11. Note that the main and feature branch are both on the same commit now.

# Resolve a Merge Conflict

1. Select ![](img/GitIcon.png) to view the **Git** tab in *SAS Studio*.
2. Select the **History** tab.
3. Create a branch named **your-branch**.
   1. *Right click* the latest commit and select **Create New Branch**.
   2. Name the branch, **your-branch**.
   3. *Un-check" **Checkout after create** and click **Create**.
4. Create a branch named **his-branch**.
   1. *Right click* the latest commit again and select **Create New Branch**.
   2. Name this branch, **his-branch**.
   3. *Un-check" **Checkout after create** and click **Create**.
   
   ![](img/newBranch1.png)   
5. You should now have 4 branches, **main**, **his-branch**, **your-branch**, and your feature branch from earlier.
6. Check out **his-branch** by choosing it from the **Current branch** drop down menu.

   ![](img/checkOutHisBranch.png)
7. Open the **TopNCategories.sas file** and make the following changes:
   1. Change **%let n=25;** to **%let n=15;**.
   2. Add the following comment at the bottom of the comment box: **Per User Feedback**.