

# Task 3 — Infrastructure as Code (IaC) with Terraform
Provision a local Docker container (nginx) using Terraform, then destroy it.
## Tools

Terraform
Docker

# Files

main.tf — Terraform configuration that pulls the nginx image and runs a container with port 8080 → 80.
logs_*.txt — execution logs from each Terraform command.

# use ec2 instance connect to mabaxterm 

<img width="1373" height="596" alt="image" src="https://github.com/user-attachments/assets/df425014-9645-4fca-8c60-6bb201b7a422" />



# Prerequisites
Docker must be installed and running.
bashdocker --version
terraform -version
docker ps
Steps to run

# bash# 1. Initialise the project (downloads the Docker provider)
terraform init

# 2. Preview the changes
terraform plan

# 3. Create the image + container
terraform apply        # type "yes" when prompted

# 4. Verify
docker ps              # shows the "terraform-nginx" container
# open http://localhost:8080 in a browser -> nginx welcome page




<img width="1371" height="689" alt="image" src="https://github.com/user-attachments/assets/eca070e2-5bc4-4e07-9477-ba88268e1f55" />


# 5. Inspect state
terraform state list
terraform state show docker_container.nginx




# 6. Tear everything down
terraform destroy      # type "yes" when prompted


Step 1 — Create an empty repo on GitHub  |
Step 2 — Add a .gitignore
cat > .gitignore << 'EOF'
.terraform/
.terraform.lock.hcl
*.tfstate
*.tfstate.*
crash.log
EOF

Step 3 — Initialise git and commit
Run these from inside your terraform-docker-task folder (where main.tf and README.md are):
bashgit init
git add .
git commit -m "Task 3: Provision local Docker container with Terraform"
git init creates a local repo, git add . stages all your files (main.tf, README.md, your log .txt files, screenshots), and commit saves the snapshot.

Step 4 — Connect to GitHub and push
bashgit branch -M main
git remote add origin https://github.com/your-username/terraform-docker-task.git
git push -u origin main
Replace the URL with your actual repo URL from Step 1. git remote add origin links your local repo to the GitHub one, and git push uploads it. The -u flag sets the upstream so future pushes are just git push.
Authentication note

When you push, GitHub will not accept your account password. If prompted for a password, you need a Personal Access Token instead:
Go to GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic) → Generate new token, tick the repo scope, and copy it. Paste that token in place of the password when prompted. (If you've set up SSH keys or the GitHub CLI before, those work too.)

Step 5 — Verify
Refresh your repo page on GitHub. You should see main.tf, README.md, your log files, and the README rendering at the bottom. That link is what you paste into the submission form.


What I learned
Terraform lets you define infrastructure declaratively in code. You describe the
desired end state (main.tf), and Terraform figures out what to create, in what
order (resource dependencies), and tracks it all in a state file
(terraform.tfstate). plan previews changes safely; apply executes them;
destroy removes them. The same code can be re-run reproducibly and torn down
cleanly — the core value of Infrastructure as Code.

<img width="976" height="619" alt="image" src="https://github.com/user-attachments/assets/ac7bd459-b662-4ba6-ba1e-6d273ed1ce87" />


 <img width="762" height="652" alt="image" src="https://github.com/user-attachments/assets/9ca8c4a5-a633-4311-b0fa-7b75df9194dc" />
 

<img width="695" height="602" alt="image" src="https://github.com/user-attachments/assets/3bc0a181-1479-4adb-8bbe-5e768a43c0b1" />


<img width="970" height="556" alt="image" src="https://github.com/user-attachments/assets/aff11d49-7d4e-46f9-9d78-088929042e4b" />


<img width="728" height="642" alt="image" src="https://github.com/user-attachments/assets/cc57746a-97fd-43e3-9d1b-2f2d9f2871ff" />


Successfully provisioned and managed a Dockerized Nginx server using Terraform and verified deployment locally via browser.

👨‍💻 Author

Harun Shaik
DevOps & Cloud Enthusiast 🚀




