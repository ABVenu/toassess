# 🚘 **Fleet Management System**

You are required to build a **Fleet Management System** consisting of:

1. A **Next.js User Application**
2. A **React Admin Portal**
3. A **Node + Express + MongoDB + Redis Backend**
4. Backend Dockerization + CI/CD → AWS ECR
5. Manual ECS deployment
6. S3-hosted static frontends

The system must support role-based dashboards, bookings, trip workflows, analytics, and proper validations and optimizations.

---

# ---------------------------------------------------

# **Part 1 — Next.js User Application**



This application serves **three user roles**:

* **Vehicle Owner**
* **Driver**
* **Customer**

## **1. Authentication**

* Must use **NextAuth** with **JWT strategy**.
* Protected pages must redirect to login when unauthorized.
* Role-based access is mandatory.

---

## **2. Static Pages (SSG)**

The following pages must be statically generated:

### **Landing Page**

* Public page showcasing the product with CTAs.

### **Signup Page**

* SSG page with role selection (owner / driver / customer).
* Form validation required.

### **Login Page**

* SSG page that integrates with NextAuth.
* Form validation required.

---

## **3. Dashboard (SSR or ISR)**

After login, users land on a **role-based dashboard**.
Dashboard must use:

* **SSR (Server-Side Rendering)** OR
* **ISR (Incremental Static Regeneration)**

### **Dashboard Layout Requirements**

All dashboards must share a common layout:

* **Top navigation bar**
* **Sidebar menu**
* **Main content area**

---

## **4. Dashboard Feature Requirements**

### **A. Vehicle Owner**

Owners must be able to:

* Create/manage vehicles.
* View all owned vehicles in **card layout**.
* View trip insights:

  * Total revenue generated
  * Total bookings
  * Total cancellations
  * Trip history

---

### **B. Driver**

Drivers must be able to:

* View list of vehicles they can register to drive.
* Register themselves as a driver for selected vehicles.
* View assigned trips.
* Update the status of trips (ongoing, completed, etc.).

---

### **C. Customer**

Customers must be able to:

* Browse available vehicles with filters.
* Book vehicles.
* View booking history with status info.

---

## **5. UI Requirements (Next.js)**

### **Form Validation**

All forms in the Next.js user application must use a **validation library**, such as:

* `react-hook-form`
* `zod`
* `yup`
* `formik`

Validation must cover:

* Required fields
* Data type rules
* Email formats
* Password rules
* Booking inputs
* Vehicle creation inputs
* Driver registration inputs

Validation must provide real-time user feedback and prevent invalid submissions.

---

# ---------------------------------------------------

# **🧩 Part 2 — React Admin Portal**



The admin portal is a **separate React application**.

## **Admin Capabilities**

### **CRUD Management**

Admins can manage:

* Vehicles
* Drivers
* Trips

Soft delete must be supported.
Cascade behavior must apply appropriately.

---

## **Admin Dashboard**

Admins must see analytics including:

* Total vehicles
* Total drivers
* Total trips
* Revenue generated
* Cancelled trips

---

## **UI Requirements (React Admin)**

### **Component Optimization**

The React Admin Portal must showcase **proper optimization techniques**, including:

* `React.memo` for pure components
* `useMemo` for expensive calculations
* `useCallback` for handler functions
* Lazy loading & dynamic imports
* Pagination for large tables
* Splitting heavy UI into smaller memoized components

These optimizations must be applied especially to:

* Vehicle lists
* Driver lists
* Trip tables
* Admin dashboard components

---

# ---------------------------------------------------

# **🧩 Part 3 — Backend (Node + Express + MongoDB + Redis)**



The backend must power **all functionality of both frontends**.

### **Schema & Relationship Design Requirement**

You must **design and fix all database schemas, validations, and entity relationships** appropriately, based on:

* Role behavior
* Booking & trip workflows
* Trip lifecycle
* Analytics needs
* Soft delete behavior

Schemas must be structured to support efficient queries and aggregation-based analytics.

---

## **Backend Functional Requirements**

### **Authentication & Security**

* Password hashing
* JWT auth with:

  * Access token expiry
  * Refresh tokens
  * Token blacklist for revoked tokens
* Role-based authorization middleware

---

### **Business Logic Requirements**

#### **Vehicle Management**

* Create, update, list vehicles
* Soft delete
* Cascade trip/archive behavior

#### **Driver Management**

* Register drivers
* Driver ↔ vehicle assignments
* Trip view for drivers

#### **Customer Features**

* Vehicle search
* Booking creation
* Booking history

#### **Trip Management**

* Trip lifecycle updates
* Cancellations
* Revenue calculations
* Insights for dashboards

---

### **Email Notifications**

Trigger emails using **Nodemailer** on:

* Booking confirmation
* Trip completion
* Trip cancellation

---

## **Redis Requirements**

Redis must be used for:

* Caching
* Rate limiting
* Any additional performance improvements

### **Mandatory Clarification**

➡ **Use only LOCAL Redis. No Redis Cloud, no managed Redis service.**

Redis must run either:

* On the developer’s machine
  OR
* Inside the same Docker container as the backend

---

# ---------------------------------------------------

# **Part 4 — AWS Deployment Requirements**

## **1. Next.js User Application Deployment**

* Build the Next.js app into static assets.
* Deploy the **build output** to an AWS S3 bucket.
* The deployed frontend must use the ECS backend API URL.

---

## **2. React Admin Portal Deployment**

* Build the React admin application into static assets.
* Deploy the **build output** to a separate AWS S3 bucket.
* The deployed admin frontend must integrate the ECS backend API URL and communicate with it smoothly.

---

## **3. Backend Deployment (Node + Express API)**

### **A. Dockerization**

* The backend must be containerized as a **single Docker image** that includes:

  * Node.js backend
  * Redis server
* This Dockerized backend code must be pushed to GitHub.

---

### **B. CI/CD Requirement (GitHub Actions)**

Your CI/CD pipeline must:

1. **Build the backend Docker image**
2. **Push the Docker image to AWS ECR**

➡ CI/CD **must NOT** automatically deploy to ECS.
ECS deployment must be **done manually**.

---

### **C. Manual ECS Deployment**

* After CI/CD pushes the latest image to ECR,
  **you must manually update the ECS task/service to use the new image**.

---

## **4. Connectivity Requirement**

Both S3-hosted frontend applications must:

* **Integrate the ECS backend API URL** (or Load Balancer URL) into their environment/config.
* After deployment, the FE must **seamlessly communicate** with the ECS backend for all API requests.

In simple terms:

👉 **Configure FE → BE connection using the ECS backend URL, then deploy FE to S3 so it works perfectly with ECS backend after deployment.**

---

## **5. AWS Access, Permissions & Secrets**

You must:

* Create and configure the **necessary AWS permissions, roles, and policies** required for:

  * Pushing images to ECR
  * Accessing S3 buckets for deployment
  * Authenticating GitHub Actions with AWS IAM
* Provide the required IAM credentials and configuration in **GitHub Secrets**, such as:

  * `AWS_ACCESS_KEY_ID`
  * `AWS_SECRET_ACCESS_KEY`
  * `AWS_REGION`
  * Any required ECR/S3 identifiers

➡ These permissions must be configured correctly so that **GitHub Actions can authenticate to AWS and push the Docker image to ECR** without failures.

---

