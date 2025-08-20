# Oracle21C-express-edition
I am Md Abdullah Rajeeb student of university of scholars 14th batch CSE. I am struggling to install the oracle 21c express edition on the ubuntu (Linux). I found the way to make it work. So, i am sharing the method. 🌠

Got it 👍 You want the same **installation guide** but with **Tousif Tasrik’s name and credits removed**, making it a clean, neutral tutorial.

Here’s the updated version 👇

---

# 🚀 Install Oracle 21C Express Edition on Ubuntu 22.04+ using Docker 🐳

📢 Education must be free.

🛠️ Requirements
🔹 A system with Ubuntu installed
🔹 Docker installed (`docker.io`)

---

## ⚙️ Installation Steps

✅ **Step 1: Update your packages**

```bash
sudo apt update
```

✅ **Step 2: Install Docker**

```bash
sudo apt install docker.io
```

✅ **Step 3: Enable & Start Docker**

```bash
sudo systemctl enable docker --now
```

✅ **Step 4: Pull the Oracle 21c Docker Image**

```bash
sudo docker pull gvenzl/oracle-xe:21-slim
```

✅ **Step 5: Run the container with initial password setup**

```bash
sudo docker run -d \
  --name oracle-xe \
  -p 1521:1521 -p 5500:5500 \
  -e ORACLE_PASSWORD=<your-default-password> \
  gvenzl/oracle-xe:21-slim
```

**Connection Details:**

* **Host:** localhost
* **Port:** 1521
* **Service Name:** XEPDB1
* **User:** system
* **Password:** YourPassword123

🧠 Replace with a secure password and remember it!

---

## 🧪 Check if Oracle 21c XE is Running

```bash
sudo docker ps -a
```

This will show the running container details.

---

## ▶️ Starting & Stopping the Database

**Start Oracle 21c XE**

```bash
sudo docker start oracle-xe
```

**Stop Oracle 21c XE**

```bash
sudo docker stop oracle-xe
```

---

## 💻 Connect via SQL\*Plus

```bash
sudo docker exec -it oracle-xe sqlplus system/<your-password>@localhost/XEPDB1
```

---

## 👤 Creating a New User

You can create a new user without needing the `C##` prefix:

```sql
CREATE USER myuser IDENTIFIED BY mypassword;
GRANT dba TO myuser;
```

Then reconnect:

```sql
disconnect;
connect myuser/mypassword@localhost/XEPDB1;
```

---

✨ Done! Now you have **Oracle 21c XE** running inside Docker on Ubuntu 22.04+.

