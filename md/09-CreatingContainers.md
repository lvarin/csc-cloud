# [Rahti] Logging in on web console

.container[
  .col[

* Navigate to [https://rahti.csc.fi:8443](https://rahti.csc.fi:8443).
* Use your CSC account to login

]

.col[
![:scale 100%, Logging page](/csc-cloud/img/logging-web-console.png)

]]

---

# [Rahti] Creating a project

.container[
  .col66[

* Click in "Create Project"
  * **Name**: Short name that will be used to reference the project
  * **Display Name**: Descriptive name that should make clear what the project is
  * **Description**: It **must** be: "csc_project: 2001316". It must be associated to a CSC project for billing purposes.
* Initial quota of 5 projects

]
.col[
![:scale 80%, Logging page](/csc-cloud/img/creatingProject.png)

]]

---

# [Rahti] How to open a terminal session

.container[
  .col66[
![:scale 100%, Terminal in a Pod](/csc-cloud/img/terminalPod.png)
  ].col[
  
* Go to the "Pods page"
  **Applications** > **Pods**
* Click in the running Pod that you one to open an interactive session with
* Click in **Terminal**

]]

---

# [Rahti] How to see application logs?

.container[
  .col66[
.center[![:scale 95%, View log GUI](/csc-cloud/img/viewLog.png)]
  ]
  .col[

* Go to the "Deployments page"
  * **Applications** > **Deployments**
* Click in "View Log"

![:scale 100%, View Log Page](/csc-cloud/img/viewLogPage.png)

]]

---

# [Rahti] Editing API objects

.container[
  .col66[
![:scale 100%, Edit Pod](/csc-cloud/img/editPod.png)
  ].col[

* Go to the objects page, in this case the "Pods page"
* Click in the object you want to edit.
* Click in **Actions** > **Edit YAML**

  ]]