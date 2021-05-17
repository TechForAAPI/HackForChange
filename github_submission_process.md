### GitHub submission process

- Fork official repository to personal github repository
  - Visit [HackForChange](https://github.com/TechForAAPI/HackForChange). And then fort it to your own account.

> Nota Bene :  the following commands are supposed to be done in console. [Git](https://git-scm.com/) is needed.

- Clone personal github repository to local

  - Back to your won GitHub page，find the *HackForChange* that you just forked，enter it, `clone` it to local, like :

    ```bash
    # replace the XXX with your own user name
    git clone git@github.com:XXX/HackForChange.git
    cd HackForChange
    ```

- Create a personal project folder under the local `ChallengeProject` folder, and place the submissions in the personal folder (use the name of your corresponding work). For details, refer to the following table:

| Work        | Type Submissions in Folder                                   |
| ----------- | ------------------------------------------------------------ |
| Code works  | Personal Github project link, etc. (Source code is placed in personal GitHub repository, but **not necessary**) |
| Other works | Links to works, etc. (such as Document link describing your idea and your implementation process) |

* Pull Request ：Submit your work folder to the official repository

  1. **To create a `branch`**

  > It’s not recommended to develop in the master branch unless the urgent recovery.

  According to the purpose, create a new branch and appropriately name it, run like this :

  ```bash
  git checkout -b my-fix-branch master
  ```

  2. **To modify content and submit**

  Modify the corresponding file and submit :

  ```bash
  git add .
  git commit -m "XXX"
  ```

  Pay attention to :

  * clarify in one sentence for what have been done

  If there is modification after `commit` , use the parameter `--amend`：

  ```bash
  git add .
  git commit --amend -sm "XXX"
  ```

  3. Upstream repository change synchronization

  To avoid upstream repository change synchronization ([HackForChange](https://github.com/TechForAAPI/HackForChange) )，it’s necessary to sync your local repository with the upstream：

  ```bash
  $ git remote add upstream git@github.com:TechForAAPI/HackForChange.git
  $ git fetch upstream
  ```

  If there have been changes to the upstream repo already, please run `rebase` at first :

  ```bash
  $ git rebase upstream/master
  ```

  4. To push new branch to remote repository

  ```bash
  $ git push -f origin my-fix-branch:my-fix-branch
  ```

  5. To create a `Pull Request`

  Create a `pull request` to the upstream repository. As shown:


  If the content needs to be changed after other people's `review`, modify the relevant content, and then perform the following operations, the PR will automatically synchronize the `commit`.

  ```bash
git add .
git commit --amend
git push -f origin my-fix-branch
  ```

    6. To resolve a merge conflict

  > Nota bene : if no conflict occurs, no need to do these

  -   Sync with upstream repo

  ```bash
git fetch upstream
  ```

  -   Run `rebase`:

  ```bash
git rebase upstream/master
  ```

  -   Manually resolve the conflict, then submit

  ```bash
git add my-fix-file
git rebase --continue
git push -f origin my-fix-branch
  ```

    7. After the merge, you can：

  -   Switch back to `master`：

  ```bash
git checkout master -f
  ```

  -   Keep the `master` in sync with the upstream branch：

  ```bash
git pull --ff upstream master
  ```

  -   Delete local branch (optional):

  ```bash
git branch -D my-fix-branch
  ```

  -   Delete remote branch (optional)：

  ```bash
git push origin --delete my-fix-branch
  ```

