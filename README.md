# Dynamic Azure Infrastructure Deployment with Terraform

This repository contains a **Terraform-based automation project** designed to deploy scalable Azure infrastructure. The configuration dynamically provisions a user-defined number of Virtual Networks (VNets) and Virtual Machines, along with a centralized Azure Bastion host for secure access.

---

## 🚀 Project Features
* **Dynamic Scaling:** Uses Terraform variables to deploy `n` number of VNets and associated Workload VMs based on input.
* **Modular Networking:** Automates the creation of Subnets, Network Security Groups (NSGs), and Security Rules.
* **Secure Access:** Provisions a single **Azure Bastion** host within the infrastructure to allow secure RDP/SSH connectivity without exposing public IPs.
* **Resource Standardization:** Implements consistent naming conventions and tagging for all cloud resources.

---

## 🏗️ Architecture Components
* **Cloud Provider:** Microsoft Azure
* **IaC Tool:** Terraform ($>= 1.0.0$)
* **Core Resources:**
    * `azurerm_resource_group`
    * `azurerm_virtual_network` (Count-based deployment)
    * `azurerm_subnet` (Workload & Gateway subnets)
    * `azurerm_linux_virtual_machine` (One per VNet)
    * `azurerm_bastion_host` (Centralized management)

---

## 🛠️ Prerequisites
Before running this configuration, ensure you have the following:
1.  An active **Azure Subscription**.
2.  **Terraform CLI** installed on your local machine.
3.  **Azure CLI** installed and authenticated (`az login`).

---

## 📖 How to Use

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/nivedmohan77/Azure-resource-auto-deployment.git
    cd your-repo-name
    ```

2.  **Initialize the Directory:**
    ```bash
    terraform init
    ```

3.  **Review the Plan:**
    ```bash
    terraform plan
    ```

4.  **Deploy the Infrastructure:**
    When prompted for the `vnet_count`, enter the number of environments you wish to deploy (e.g., `3`).
    ```bash
    terraform apply
    ```

5.  **Clean Up:**
    To avoid unnecessary Azure costs, destroy the resources once finished:
    ```bash
    terraform destroy
    ```

---

## 🔧 Technical Implementation Details
This project demonstrates proficiency in several key DevOps/SRE concepts:
* **Infrastructure as Code (IaC):** Version-controlled infrastructure management.
* **Terraform Meta-arguments:** Utilizing the `count` parameter for resource scaling.
* **Input/Output Variables:** Creating a flexible, reusable configuration instead of hard-coded values.
* **Network Security:** Implementing a "Jumpbox" pattern via Azure Bastion for hardened security posture.

---

## 📈 Future Roadmap
Will be updating the repro in case of any bugs.
- [ ] Implement Remote State Management using **Azure Blob Storage**.
- [ ] Integrate with **GitHub Actions** for automated CI/CD linting and deployment.
- [ ] Add support for **Load Balancers** to distribute traffic across deployed VMs.
