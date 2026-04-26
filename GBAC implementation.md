# 🚀 Task 2: Group-Based Access Control (GBAC) Implementation

## 📌 Objective

Implement Group-Based Access Control (GBAC) to simplify and centralize user permissions across the Stratos Datacenter—especially for SFTP access.

This ensures:

- Easier user management
- Consistent permission handling
- Scalable access control across servers

## 🏗️ Infrastructure Context

| Component       | Details               |
|-----------------|-----------------------|
| Datacenter      | Stratos               |
| Target Servers  | stapp01, stapp02, stapp03 |
| Group Name      | nautilus_sftp_users   |
| Target User     | stark                 |
| Access Type     | SFTP                  |

## ⚙️ Implementation Steps

### 1️⃣ Create Group (Across All Servers)

To maintain consistent access control, create the group on each application server:

```bash
sudo groupadd nautilus_sftp_users
```

✔️ This group will act as a centralized permission layer for SFTP users.

### 2️⃣ User Management & Assignment

#### 🔹 Scenario A: User Does NOT Exist

Create the user and assign the group as the primary group:

```bash
sudo useradd -g nautilus_sftp_users stark
```

#### 🔹 Scenario B: User Already Exists

Add the user to the group as a secondary group:

```bash
sudo usermod -aG nautilus_sftp_users stark
```

✔️ The `-aG` flag ensures:

- `-a` → append (do NOT remove existing groups)
- `-G` → secondary group assignment

### 3️⃣ Verification

✅ Check if the group exists:
```bash
grep "nautilus_sftp_users" /etc/group
```

✅ Verify user group membership:
```bash
id stark
```

Expected output should include:

```
nautilus_sftp_users
```

## 🧠 Key Concepts

### 🔸 Primary Group (`-g`)
- Default group assigned to a user
- Used for file ownership by default
- Each user has only one primary group

### 🔸 Secondary Groups (`-G`)
- Additional groups a user belongs to
- Used for shared access (like SFTP, logs, etc.)
- A user can belong to multiple secondary groups

## ⚠️ Important Note

If you forget `-a` while using `-G`:

```bash
usermod -G group user
```

👉 This **overwrites** all existing groups, which can break permissions.

## 📊 Command Reference

| Action              | Command                                    |
|---------------------|--------------------------------------------|
| Create Group        | `groupadd nautilus_sftp_users`             |
| Create User + Group | `useradd -g nautilus_sftp_users stark`     |
| Add User to Group   | `usermod -aG nautilus_sftp_users stark`    |
| Verify Group        | `grep "nautilus_sftp_users" /etc/group`    |
| Verify Membership   | `id stark`                                 |
