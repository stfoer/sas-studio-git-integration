

# 1. SAS Studio - Git Integration Setup with SSH

<br>

## Exercise Description
In this exercise, you will setup the integration between a GITHub repository and SAS Studio using SSH.

<br>

## Create New SSH Keys
1. On your course environment Windows desktop, click the Windows button, select **Git** and *click* the **Git Bash** icon.
   
   ![](img/GitBash.png)

2. In the git bash window, run the command **ssh-keygen -t ed25519 -C "your_email@example.com"**.
   >Make sure to replace the sample email with your real github email address.

3. You should see the similar output as shown below.  Hit **Enter** for each question the program asks.
   
    ![](img/SSHKeygen.png)

4. The ssh-keygen program creates two files, a public key named **id_ed2519.pub**, and a private key named **id_ed2519** with no extension.

## Copy the SSH Keys to your SAS Server

1. In SAS Studio, *Right Click* the **SAS Server->Home->gelcontent->keys** directory in the Explorer ![](img/ExplorerICon.png) and select **Upload Files**.
   ![](img/UploadKeys.png)
1. Select the plus sign ![](img/AddIcon.png).
2. Navigate to the **C:\Users\Student\.ssh** directory and select the **id_ed2519.pub** and **id_ed2519** files.
3. Click **Upload**.

## Copy the Public SSH Key to your GitHub Account

1. In *Google Chrome*, navigate to **https://github.com**.
   
2. Click **Sign in** to sign in with your *GitHub* credentials.
   > &#9755; GitHub may send you a confirmation email.  Please make sure you have access to the email account you are using.
   
     > &#9755; If you do not already have *GitHub* credentials, then click **Sign Up** and follow the instructions to create them.

3. Select your account picture **&#10132; Settings**.
    ![](img/GitHub_SignIn.png)

4. Select **SSH and GPG key** on the left.
5. Push the **New SSH Key** button.
6. Name your SSH Key, **myGitHubSSHKey** and copy in the contents of your **public** ssh key.
   >You can copy the contents of your public ssh key to the clipboard by returning to the git bash terminal and running **clip < ~/.ssh/id_ed25519.pub**.

   ![](img/AddSSHKey.png)

7. Click **Add SSH Key**.

## Create a Fork of a GitHub Repository

1. In *Google Chrome*, navigate to **https://github.com**.
   
2. Click **Sign in** to sign in with your *GitHub* credentials.
   > &#9755; GitHub may send you a confirmation email.  Please make sure you have access to the email account you are using.
   
     > &#9755; If you do not already have *GitHub* credentials, then click **Sign Up** and follow the instructions to create them.
1. Enter **SASExplore2023/UsingGitInSASStudio** in the *Search* area.
    ![](img/GitHub_Search.png)

2. Press **Enter** key to perform the search.
   
3. Select the hyperlink for the **SASExplore2023/UsingGitInSASStudio** repository.
   
4. Select **Fork &#10132; Create a new fork**.
   ![](img/CreateNewFork.png)

5. Keep the default settings and click **Create fork**.
   ![](img/CreateFork.png)
   > &#9998; This process can take a few minutes depending upon the size of the repository.

6. Once the creation of the fork is complete, then select **Code**.
   ![](img/CodeButton.png)

7. On the *Local* tab, make sure **SSH** is selected, and then select ![](img/Copy.png) to copy the path to *clone* this fork of the repository.
   ![](img/sshLink.png)

8. Paste the URL in the *Notepad++* session to use later.
    ![](img/sshNotepad.png)

<br>
<br>

## Create a Git Profile in SAS Studio
1. Open the **Google Chrome** browser on your Windows RACE Image.
   
2. Select the **SAS Viya** bookmark.
   
3. Enter the following:
   - User ID: **student**
   - Password: **Metadata0**


2. Click **Sign In**.
   
3. Select ![Viya Menu Selector](img/HamburgerMenu.png) **&#10132; Develop Code and Flows** to open *SAS Studio*.
    ![](img/SASStudio.png)

4. Select **Options &#10132; Manage Git Connections**.
   
5. On the *Manage Git Connections* window, select the **Profiles** tab.
   
6. Select ![](img/AddIcon.png) to add a profile.
   
   ![](img/AddGITProfile.png)

7. Select **SSH** tab and enter the following information:
   - Profile name: **MyGitHubProfile**
   - User name: ***&lt;your GitHub user name&gt;***
    - Email: ***&lt;your GitHub primary email address&gt;***
    - Password: *&lt;Leave Blank>*
    - Public SSH file path:  **&lt;/gelcontent/keys/id_ed25519.pub>**
    - Private SSH file path:  **&lt;/gelcontent/keys/id_ed25519>**
        

    ![](img/sshprofile.png)

8. Click **OK** to create the profile.
    ![](img/SavedGitProfile.png)

9.  Click **Close**.


<br>
<br>

## Create a Folder for the Local Copy of the Repository
1. Select ![](img/ExplorerIcon.png) to view the **Explorer** tab in *SAS Studio*.
   ![](img/ExplorerTab.png)

2. Navigate to **Files &#10132; Home** and select ![](img/NewFolderIcon.png) **&#10132; Folder** .  Enter the name **MyGitClone**.
    > &#9998; The folder for a Git Repository must exist on the SAS Server and be an empty folder.

    ![](img/CreateNewFolder.png)


3. Select **OK** to create the folder.
   
4. Right-click the *MyGitClone* folder and select **Add shortcut**.
   
   ![](img/AddShortcut.png)
5. Click **OK** to create a shortcut to the folder.
   
6. Expand the **Folder Shortcuts** section to confirm the shortcut was created.
   
    ![](img/FolderShortcut.png)

<br>
<br>

## Add Repository in SAS Studio
1. Select **Options &#10132; Manage Git Connections**.
   
2. On the *Manage Git Connections* window, select the **Repositories** tab.
   
3. Select ![](img/AddIcon.png) **&#10132; Clone a repository** to add a cloned repository.
    ![](img/AddRepository.png)

4. Enter the following information:
    - Repository: ***&lt;paste saved URL for cloned (forked) Git repository&gt;***
        > &#9998; You created and saved it earlier in this exercise.
    - Server location: **/home/student/MyGitClone**
        > &#9755; Select ![](img/FileIcon.png) to navigate to **Files &#10132; Home &#10132; MyGitClone** or **Folder Shortcuts &#10132; Shortcut to MyGitClone**.

         > &#9998; This must be an empty folder location.
    - Profile: **MyGitHubProfile**.

    ![](img/CreateCloneRepository.png)

5. Click **Clone** to clone the repository in the location specified.
   
6. Click **Close**.

<br>
<br>

## Review Git Repository
1. Select ![](img/ExplorerIcon.png) to view the **Explorer** tab in *SAS Studio*.
   
2. Expand **Folder Shortcuts &#10132; Shortcut to MyGITClone** to view the contents of the cloned repository.

   ![](img/RepositoryContents.png)

3. Select ![](img/GITIcon.png) to view the **GIT Repositories** tab in *SAS Studio*.
   
4. Double-click **MyGitClone** to open it in a tab.

    ![](img/MyGitCloneTab.png)

      > &#9998; This is where you can view the staged/unstaged changes in your local repository and pull/push changes to the external Git repository.

<br>
<br>

