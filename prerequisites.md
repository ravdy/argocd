# Setup Guide for ArgoCD on EKS

To set up ArgoCD on Amazon EKS, follow the steps below:

1. Install **eksctl**
2. Install **kubectl**
3. Install and configure **AWS CLI**
4. Create IAM Role for EKS
5. Configure AWS CLI

---

## 🔹 Install eksctl on Windows
1. Open **PowerShell** as Administrator.
2. Download the latest eksctl binary:
   ```powershell
   Invoke-WebRequest -Uri "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_windows_amd64.zip" -OutFile "eksctl.zip"
3. Extract the ZIP file:
   ```powershell
   Expand-Archive -Path "eksctl.zip" -DestinationPath "C:\eksctl" -Force
   ```
4. Add eksctl to PATH:
   ```powershell
   [System.Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\eksctl", [System.EnvironmentVariableTarget]::Machine)
   ```
 5. Open a new terminal and verify:
    ```powershell
    eksctl version
    ```

## 🔹 Install kubectl on Windows
1. Download the latest stable kubectl binary:
   ```powershell
   curl -LO "https://dl.k8s.io/release/v1.32.0/bin/windows/amd64/kubectl.exe"
   ```
1. Move the binary to a directory in your system PATH:
   ```powershell
   move .\kubectl.exe C:\Windows\System32\
   ```
1. Verify installation:
   ```powershell
   kubectl version --client
   ```

## 🔹 Install AWS CLI on Windows
1. Follow the official AWS documentation:
   👉 Install AWS CLI on Windows [https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html]

# For Linux Environments
1. Install eksctl on Linux
   ```bash
   # Download latest release
   curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz"

   # Extract
   tar -xzf eksctl_$(uname -s)_amd64.tar.gz

   # Move to /usr/local/bin
   sudo mv eksctl /usr/local/bin/

   # Verify
   eksctl version
   ```
2. Install kubectl on Linux
   ```bash
   # Download the latest stable kubectl binary
   curl -LO "https://dl.k8s.io/release/$(curl -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

   # Make it executable and move to PATH
   chmod +x kubectl
   sudo mv kubectl /usr/local/bin/

   # Verify installation
   kubectl version --client
   ```
3. Install AWS CLI on Linux
   ```bash
   # Download the installer
   curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

   # Unzip and run the installer
   unzip awscliv2.zip
   sudo ./aws/install

   # Verify
   aws --version
   ```
4. Configure AWS CLI
   ```bash
   aws configure
   ```
   - AWS Access Key ID
   - AWS Secret Access Key
   - Default region name (e.g., us-east-1)
   - Default output format (e.g., json)

5. Create IAM Role or user for AWS
