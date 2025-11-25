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
## 🧪 Test Cases / Sample Run

This section demonstrates **real-world scenarios** of the Hospital Admission Database System.  
All SQL commands are shown along with **example outputs** to understand the project outcomes.

---

**Scenario2 :** Check the contents of all core tables to ensure setup is correct.

```sql
SELECT * FROM wards;
SELECT * FROM rooms;
SELECT * FROM patients;
SELECT * FROM admissions;
SELECT * FROM procedures_master;
SELECT * FROM medicines_master;
SELECT * FROM admissions_procedures;
SELECT * FROM admissions_medicines;
SELECT * FROM bills;
```
**Sample Output**

**Scenario 2:** Display all procedures and medicines administered for a specific admission.

```sql
SELECT p.first_name, p.last_name, pr.description AS procedure_done, m.name AS medicine_given, am.quantity
FROM admissions a
JOIN patients p ON a.patient_id = p.patient_id
LEFT JOIN admissions_procedures ap ON a.admission_id = ap.admission_id
LEFT JOIN procedures_master pr ON ap.procedure_id = pr.procedure_id
LEFT JOIN admissions_medicines am ON a.admission_id = am.admission_id
LEFT JOIN medicines_master m ON am.medicine_id = m.medicine_id
WHERE a.admission_id = 1;
```
**Sample Output**

**Scenario 3:** Check existing bills before discharging a patient.

```sql
SELECT * FROM bills;
SELECT * FROM admissions WHERE admission_id = 2;
SELECT * FROM bills WHERE admission_id = 2;
```
**Sample Output**

**Scenario 4:** Discharge patient and generate final bill automatically.

```sql
EXEC discharge_patient(1);

SELECT * FROM admissions WHERE admission_id = 1;
SELECT * FROM bills WHERE admission_id = 1;
```
**Sample Output**

**Scenario 5:** Ensure all insert/update/delete actions are logged.(Veirfy Audit Log)

```sql
SELECT * FROM audit_log ORDER BY changed_at DESC;
```
**Sample Output**

**Scenario 6:** Create users with roles and verify authentication.

```sql
EXEC hospital_user_create('dr_brown', 'Doc#2025', 'role_doctor');
EXEC hospital_user_create('nurse_emma', 'Nurse#2025', 'role_nurse');
EXEC hospital_user_create('bill_tony', 'Bill#2025', 'role_billing');
EXEC hospital_user_create('aud_jane', 'Audit#2025', 'role_auditor');
COMMIT;
SELECT * FROM hospital_users;

SELECT hospital_user_authenticate('nurse_emma', 'Nurse#2025') AS role FROM dual;
SELECT hospital_user_authenticate('dr_brown', 'Doc#2025') AS role FROM dual;
```
**Sample Output**

**Scenario 7:** Verify different views for Doctors, Nurses, Billing, and Auditors.

```sql
-- Doctor view
SELECT * FROM v_patients_doctor;
-- Nurse view
SELECT * FROM v_patients_nurse;
-- Billing view
SELECT * FROM v_bills_financial;
-- Auditor view
SELECT * FROM v_audit_read;
```
**Sample Output**

## 👨‍💻 Author
**Ahsanul Haque Milon**  
Data Analyst | Data Scientist | Machine Learning Engineer
[LinkedIn](https://www.linkedin.com/in/milon48/) | [Portfolio](https://ahosanulhuqmilon.com/)
