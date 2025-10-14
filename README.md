# Hospital Admission Database System

A **secure, role-based Hospital Admission Database** built for **AmberScope Health** in **Oracle 19c**.  
This system manages patient admissions, medical procedures, medicines, billing, and user access with auditing and security.  
It is designed to simulate a **real-world hospital environment** and demonstrate practical database management skills.

---

## 🏥 Background
AmberScope Health operates several hospitals across Australia, and managing patient information manually is both slow and risky. Hospitals need a **centralized system** to keep track of patients, surgeries, medications, and expenses while keeping sensitive data safe.  

In this project, I designed and implemented a **hospital admission database system** that reflects real-world challenges in healthcare management.  
It simulates multiple user roles, encrypted sensitive data, automated billing, and full audit trails — just like a real hospital system.

---

## 🎯 Objective
The main goals of this project were to:

1. Design a **secure and organized hospital database** that supports multiple user roles (Doctor, Nurse, Billing Clerk, Admin, Auditor).  
2. Implement **role-based access control (RBAC)** to ensure that users can only access the data relevant to their role.  
3. Protect sensitive information such as patient medicare numbers through **encryption** and password hashing.  
4. Automate key hospital processes such as **admissions, treatments, and billing** using PL/SQL procedures.  
5. Maintain **audit logs** to monitor changes to sensitive data.  
6. Ensure **robust backup and recovery** strategies to safeguard critical hospital information.

---

## 🧩 Key Features
- **Multi-role access:** Doctors, Nurses, Billing, Admins, and Auditors  
- **Encrypted sensitive data:** Protecting patient medicare numbers and personal info  
- **Password security:** Hashing with salt using `DBMS_CRYPTO`  
- **Audit logs:** Track every critical data change for accountability  
- **Role-based views & procedures:** Users can only access what they are allowed to  
- **Automated billing & discharge procedures**  
- **Backup & recovery:** Daily incremental and weekly full backups using RMAN/Data Pump  

---

## 📊 Database Architecture
The system follows a **three-tier architecture**, just like many real-world hospital systems:

1. **Presentation Layer:**  
   - The interface used by staff (Web UI or SQL Developer).  
   - Roles include doctors, nurses, billing clerks, auditors, and administrators.

2. **Application Layer:**  
   - Handles the **business logic** using PL/SQL procedures.  
   - Implements validation, authentication, encryption, and auditing.  
   - Ensures all operations follow hospital rules and security policies.

3. **Database Layer:**  
   - Oracle 19c schema stores all tables, views, triggers, and procedures.  
   - Security features like RBAC, encryption, and backup/recovery protect sensitive data.

**Diagram Placeholder:**  
![Database Architecture Diagram](docs/Architecture_Diagram.png)

---

## 🧱 Entity Relationship Diagram (ERD)
The database contains the following main entities:

- **patients** → Stores personal patient information  
- **admissions** → Tracks hospital admissions for patients  
- **wards & rooms** → Organizes the hospital layout  
- **procedures & admissions_procedures** → Records medical procedures performed  
- **medicines & admissions_medicines** → Tracks administered medicines  
- **bills** → Manages billing for each admission  
- **hospital_users** → Stores system users and their roles  
- **audit_log** → Logs all sensitive changes and user activities

**Diagram Placeholder:**  
![ERD Diagram](docs/ERD_Diagram.png)

---

## 🧾 SQL Scripts
All SQL and PL/SQL scripts are organized to **reproduce the database** and demonstrate its functionality:

| File | Purpose |
|------|---------|
| `00_create_user_roles.sql` | Create users and assign roles |
| `01_create_tables.sql` | Create all tables for patients, admissions, wards, rooms, etc. |
| `02_crypto_functions.sql` | Implement password hashing and encryption |
| `03_procedures.sql` | Business logic procedures (admissions, treatments, etc.) |
| `04_audit_triggers.sql` | Triggers for auditing sensitive actions |
| `05_views.sql` | Role-based views for restricted data access |
| `06_grants.sql` | Grant privileges to different roles |
| `07_sample_data.sql` | Sample data for testing and demo |
| `08_discharge_billing_proc.sql` | Automated billing and discharge process |
| `test_cases.sql` | Real-world scenarios to test the system |

---

## 💡 Real-World Impact
Completing this project helped me demonstrate that **hospital data can be securely managed** while maintaining usability for staff:

- **Secure access control:** Each role can only see and modify relevant data  
- **Auditability:** All sensitive operations are logged for accountability  
- **Operational efficiency:** Automated admissions, treatments, and billing reduce manual errors  
- **Data protection:** Sensitive patient information is encrypted and backed up regularly  
- **Business continuity:** Backup & recovery ensures the hospital can recover from failures

This project mirrors **real hospital systems**, showing practical skills that are directly transferable to **database, SQL, and data analysis roles**.

---

## 📈 Outcome
- Successfully designed and implemented a **full hospital admission database system**  
- Demonstrated **SQL & PL/SQL expertise, database design, encryption, auditing, and backup strategies**  
- Developed a **portfolio-ready project** that clearly shows real-world database management skills to recruiters

---

## 👨‍💻 Author
**Ahsanul Haque Milon**  
Bangladesh | Aspiring Data Analyst / Database Developer  
[LinkedIn](#) | [Portfolio](#)
