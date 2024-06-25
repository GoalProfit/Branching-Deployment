# SD - Branching, Development and Deployment
When collaborating with a team on this project, please adhere to the following guidelines to ensure smooth branching and deployment processes and maintain synchronization:


| Branches   | Usage       | Description                                                                      |
|:------------|:-------------|:----------------------------------------------------------------------------------|
| master     | Production  | This branch should have no edits other than `merging prerelease`.                  |
| prerelease | Pre-Prod    | Quality assurance (QA).<br>All changes to be pushed to production.<br>PRs to prerelease require some acceptance from at least one team member to merge. |
| staging | UAT | User Acceptance Testing (UAT). |


As a matter of convention, branch names should include the ticket number to simplify tracking and get clarity based on ticket numbers.
**e.g.** `7366-my-branch-name` *or* `feature/7366-my-branch-name`.

* Commit messages should also be preceded with the ticket number that the work is being done for
    * **e.g.** `[7366] Your message here`
- it would be much simpler to review and track changes if you make it like
	- 1st commit: “fix: exeption error”
	- 2nd commit: “fix: unused variable”
- it would be easier to debug and revert a breaking commit if you split your code changes into separate commits.


## Normal development flow

1. **Create a Branch**: 
   - Create a branch from **prerelease**, including the ticket ID in the branch name.

2. **Start Working**:
   - Begin work on the ticket.

3. **Local Testing**:
   - Once done, test your changes locally.

4. **Make Commits**:
   - After local testing, make commits. Include the ticket ID in commit messages, e.g., "[FR-1] awesome change".

5. **Push Your Branch**:
   - Push your branch to the remote repository.

6. **Create a Draft PR**:
   - Create a draft pull request (PR) to **prerelease** from your local branch.

7. **Add Labels**:
   - Add relevant labels that describe the type of update, such as 'new feature' or 'bug fix'.

8. **Assign for Review**:
   - Assign a team member to review your code changes.
   - **Note**: Do not merge your local branch into **prerelease** without testing it in the staging environment.

9. **Notify for Review**:
   - Notify the engineering group about your PR so that any team member can review and approve it.

10. **Merge into Staging**:
    - Once your PR is approved, merge your branch into **staging** locally, and test your changes in the staging branch.

11. **Local Merge**:
    - You don't need to create a PR when merging your local branch into the **staging** branch. Just merge your branch locally and push it to **staging**.

12. **Final Merge to Prerelease**:
    - If your changes work in the **staging** branch, remove the draft status from your PR, and merge it into the **prerelease** branch.

13. **Test in Prerelease**:
    - Test your changes in the **prerelease** branch.

14. **Label and QA**:
    - When deployed to **prerelease**, add the "in prerelease" label to the PR. This indicates that the changes can be tested in **prerelease** without needing to check your branch locally.
    - Assign the ticket to QA.

15. **Review Iterations**:
    - Be prepared for multiple iterations of "review -> reject -> review -> approve" and "QA -> reject -> QA -> approve". Additional team members may be requested to check the changes.

16. **Urgent Hotfix**:
    - For urgent hotfixes, streamline the process as much as possible, skipping unnecessary steps. However, such cases should be rare.

17. **Deploy to Production**:
    - When ready to deploy changes to production, merge the **prerelease** branch into the **master** branch, ensuring it only contains your commits.
    - If other developers' commits are present, cherry-pick your commit from **prerelease** to **master**.

---
