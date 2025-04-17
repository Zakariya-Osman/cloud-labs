# ☁️ cloud-labs/lab1

A hands-on beginner project to launch an Ubuntu EC2 instance on AWS and connect via SSH using **Windows CMD**.

---

## 🚀 Step 1: Launch EC2 Instance on AWS

1. **Log in** to the [AWS Console](https://console.aws.amazon.com/).
2. Navigate to **EC2 > Launch Instance**.
3. Fill in the following:
   - **Name**: `ubuntu-lab`
   - **AMI**: Ubuntu Server 24.04 LTS (Free Tier eligible)
   - **Instance type**: `t2.micro`
   - **Key pair**: Create a new one (e.g., `ubuntu-key.pem`) and download the `.pem` file.
   - **Firewall/Security Group**: Allow **SSH (port 22)** from **your IP only**.
4. Click **Launch Instance**.
5. Wait for your instance to enter the **running** state.
6. Note your **Public IPv4 address** (you’ll need it for SSH).

---

## 🔑 Step 2: SSH into EC2 from Windows CMD

### ✅ Prerequisites:

- Move your downloaded `ubuntu-key.pem` file to your working directory:

  ```
  C:\Users\Synchro\Documents\GitHub\cloud-labs
  ```

- Make sure your SSH key is read-only:
  1. Right-click the `ubuntu-key.pem` file.
  2. Go to **Properties > Security > Edit**.
  3. Select your user, uncheck **Write**, and apply the changes.

### 🔐 Connect via CMD:

Open Command Prompt and run:

```cmd
cd C:\Users\Synchro\Documents\GitHub\cloud-labs
ssh -i ubuntu-key.pem ubuntu@<your-ec2-ip>
```

Example:

```cmd
ssh -i ubuntu-key.pem ubuntu@52.15.134.111
```

- You will see:

```
The authenticity of host '52.15.134.111' can't be established...
Are you sure you want to continue connecting (yes/no)? yes
```

Type `yes` to continue. You’re now inside your Ubuntu server 🎉

---

## 🛠️ Basic Commands to Try

Inside your EC2 server:

```bash
sudo apt update
sudo apt install nginx -y
```

Then open your EC2 Public IP in a browser — you should see the **Nginx Welcome Page**.

---

## 📘 Notes

- Never share your `.pem` file. Keep it safe.
- You can **stop**, **start**, or **terminate** your EC2 instance anytime from the AWS Console.
- If the instance stops, the public IP may change — check and update it before reconnecting.

---

## ✅ Project Structure

```
cloud-labs/
│
├── ubuntu-key.pem         # Your SSH private key (never push this to GitHub)
├── README.md              # This guide
```

> 🚫 **Important**: Add `ubuntu-key.pem` to your `.gitignore` file before pushing to GitHub!

---

## ✨ Next Steps

- Install basic packages
- Try hosting a simple static website
- Explore AWS CLI or S3 integrations

---

Built with 💻 by Zakariya, learning to become a **Cloud Support Associate**.
