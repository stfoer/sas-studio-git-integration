
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

## 1. Create a Branch

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

# 2. Merge a Branch into Main

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

# 3. Resolve a Merge Conflict

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
6. Check out **your-branch** by choosing it from the **Current branch** drop down menu.

   ![](img/checkOutHisBranch.png)
7. Open the **TopNCategories.sas file** and make the following changes:
   1. Change **%let n=25;** to **%let n=15;**.
   2. Add the following comment at the bottom of the comment box: **Per User Feedback**.
   3. Add the following comment at the top of the comment block:  **your-branch**.
   ![](img/yourBranch.png)
8. Save and close the program.
9. Move back to the Git ![](img/GITIcon.png) screen.
10. Stage and commit the changes to **your-branch**.
   ![](img/yourBranchSave.png)
11. Check out **his-branch** by choosing it form the **Current branch** drop down menu.
12. Re-open the **TopNCategories.sas** program.
      >Note that the changes you made are gone.  They were committed to **your-branch** so the working directory returned to its original state.
13. This time make the following changes to the program:
    1. Change the value of **N** to **11**.
    2. Add the comment, **Per Management** at the bottom of the comment block.
    3. Add the comment, **his-branch**, in the middle of the block.
14. ![](img/hisBranchSave.png)
      1. Save and close the program.
      2. Return to the Git ![](img/GITIcon.png) screen.
      3. Stage and commit the changes with the comment, **his-branch commit**.
15. Check out **your-branch** by choosing it from the **Current branch** drop down menu.
16. Open the **History** tab, *right-click* **his-branch** and select **Merge into your-branch > his-branch**.
    ![](img/branchMerge.png)
1. You will receive an error that there was a conflict.
  ![](img/gitConflictError.png)
2. Close the error.
3. Select the **Commit** tab and note that the program has an icon with two opposing arrows.  If you hover over the icon, it says **File has Conflict**.
4. *Right-click* the file and select **Edit**.
   ![](img/conflictFile.png)
5. Note that the file includes both your-branch and his-branch changes.
6. If there is a conflict, you'll see both branches' content identified by branch.
   ![](img/conflictEdit.png)
7. Delete the **your-branch** and **his-branch** comments as well as **Per Management** one.  
8. Remove the **<<<<**, **>>>>**  and **====** lines.
9. Remove the **n=11** line.
   ![](img/deConflictedFile.png)
10. Save and close the file.
11. Stage and Commit with the comment, **Conflict Resolved**.
12. Check the History tab to see the merge visual is complete.
    ![](img/mergeComplete.png)

# 4. Reset a Branch

1. Be sure to do the previous steps so that your repository is in a modified state and you have a known state (commit), you can reset to.
2. Open the Git ![](img/GITIcon.png) and select the **History** tab.
3. Check out **your-branch** by selecting it from the **Current branch** drop down menu.
4. *Right click* the **main origin/main bug fixes** commit and select **Reset**.
   >This action takes **your-branch** back to its state at that particular commit.
![](img/resetCommand.png)
5. You'll see dialog box asking which reset type you would like to perform.
   >**Soft** = Only reset the repository.  Leave the changes in the staging area and the working directory.

   >**Mixed** = Reset the repository and the staging area.  Leave the changes in the working directory.

   >**Hard** = Reset the repository, the staging area, and the working directory.  Completely erase the changes.
   ![](img/resetChoices.png)
6. Select a **Hard** reset and push **OK**.
7. After the reset, you'll see **your-branch** has been returned to the commit you selected.
   >Note that **his-branch** has not been affected.
8. With **your-branch** checked out, confirm that the changes to your working directory files have been erased.
9. Check out **his-branch** and reset it to the same commit as well.


# 4. Rebase a Branch with Another

1. Check out **his-branch** and add the following code to **TopNCategories.sas** after the **footnote** statement:

        /* his-branch: add merror option */
        options merror;

   ![](img/hisBranchSave.png)
2. Close the **TopNCategories.sas** file.
3. Return to the Git ![](img/GITIcon.png) page, stage and commit the change with the message, **merror**.
4. Check out **your-branch** and add the following code to **TopNCategories.sas** in the **%let** statement block:

        /* your-branch: Added q macro variable */
        %let q=16;

![](img/qMacro.png)

5. Save the file, stage and commit the change with the comment, **q macro**.
6. Select the **History** tab.
7. Right click the latest commit, **his-branch merror** and select **Rebase your-branch on > Selected Commit**
   ![](img/rebaseBranch.png)
8. You will see the following text box:
   ![](img/rebaseAlert.png)

9.  Select **OK**.
10. On the **History** tab, note that:
    >**your-branch** now includes the **his-branch merror** commit.

    >The commit illustration shows no merge.  It's as if **your-branch** was created from **his-branch**. 
    ![](img/rebaseAfter.png)
11. Open the **TopNCategories.sas** file and see that it includes the modification from **his-branch**.
    ![](img/rebaseAfterFile.png)


# 5. Stash your Work in Progress

1. Use **Git Stash** to save your work temporarily while you quickly complete a hotfix for a differnt project.  
   
2. Make the following changes to **your-branch**:
   1. Copy the **TopNCategories.sas** program by right-clicking it and selecting **Copy to** and selecting the **myGitClone** folder.  
   
   2. This will create a file named **TopNCategories_Copy1.sas**.  
   3. Right click that file and rename it **NewCategoriesReport.sas**.
   4. Rename **TopNCategories.sas** to **OldCategoriesReport.sas**.
   5. Rename **PythonSample.py** to **PythonProgram.py**.
   6. Add a note to the **Class_Export.flw** flow by opening it, right-clicking the canvas and selecting **Add a Note**. 
      ![](img/flowNote.png)
3. Return to the Git screen and **stage** your changes.  ***Do not commit them.***
   ![](img/stageStash.png)
4. Stash your changes by pushing the stash icon ![](img/gitStashIcon.png) and selecting **Stash**.
5. After the stash, note that the staged changes have disappeared.  They are now stored in the stash.
6. Return to the Explorer ![](img/ExplorerIcon.png) and look at the contents of your Git working directory.  It has reverted back to its state prior to your stashed changes.
   
   ![](img/stashDirectory.png)

7. Complete the work for your hotfix by editing the **PythonSample.py** and adding the code **import swat** as shown below.
   
   ![](img/importSwat.png)

8. Save and close the file.
9. On the git screen ![](img/GITIcon.png), **stage** and **commit** the change with the comment **hotfix #1**.
10. Open the history tab and note that **your-branch** is now one commit ahead of the stash.
11. Push the stash icon ![](img/StageIcon.png) and select **Pop stash**.
    > **Pop stash** applies the stashed changes and deletes the stash.

    > **Apply stash** applies the stashed changes but keeps the stash.

    ![](img/popStash.png)

12. After the stash is applied, note that the stashed changes are re-introduced and that the hotfix change is also maintained and applied to the renamed file.
    
    ![](img/stashApply.png) ![](img/postStashPy.png) 
