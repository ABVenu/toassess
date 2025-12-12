
## **Fleet Management System – Evaluation Rubric (100 Marks Total)**

Each category = **10 marks**, based on technical completeness, correctness, best practices.

---

## **1. JavaScript (10 Marks)**

Evaluate based on use of modern JS features and code quality.

| Criteria                                                                                       | Marks |
| ---------------------------------------------------------------------------------------------- | ----- |
| Proper use of **arrow functions**, `const`/`let`                                               | 2     |
| Usage of **ES6+ features** (spread, destructuring, template literals, optional chaining, etc.) | 2     |
| Clean **modularization** of code (helpers, utils, separate files)                              | 2     |
| Proper asynchronous handling (`async/await`)                                                   | 2     |
| Code readability, naming conventions, clean patterns                                           | 2     |

---

## **2. HTML / CSS (10 Marks)**

Across both Next.js and React apps.

| Criteria                                         | Marks |
| ------------------------------------------------ | ----- |
| Clean and semantic **HTML structure**            | 2     |
| Correct usage of relevant tags & layout patterns | 2     |
| Proper usage of **Tailwind CSS** for styling     | 3     |
| Correct usage of **shadcn components**           | 3     |

---

## **3. React (10 Marks)**

Evaluated within the Admin Portal.

| Criteria                                                                                             | Marks |
| ---------------------------------------------------------------------------------------------------- | ----- |
| Proper React project setup and package installation                                                  | 1     |
| Correct routing setup                                                                                | 1     |
| Usage of **Redux Toolkit** for global state                                                          | 2     |
| Clean component structure with props used properly                                                   | 2     |
| Usage of **optimization techniques** (`React.memo`, `useMemo`, `useCallback`, lazy load, pagination) | 2     |
| Correct usage of Tailwind + shadcn                                                                   | 2     |

---

## **4. Next.js (10 Marks)**

Evaluated within the User Portal.

| Criteria                                                      | Marks |
| ------------------------------------------------------------- | ----- |
| Correct Next.js project setup (App Router)                    | 2     |
| Implementation of **SSG pages** (Landing, Login, Signup)      | 2     |
| Implementation of **SSR/ISR dashboard**                       | 2     |
| Integration of **NextAuth** with proper role-based protection | 2     |
| Tailwind + shadcn usage                                       | 2     |

---

## **5. Node.js (10 Marks)**

Backend structure and modularity.

| Criteria                                                           | Marks |
| ------------------------------------------------------------------ | ----- |
| Clean project setup and structure                                  | 2     |
| Proper usage of **ESM Modules**                                    | 1     |
| Correct folder organization (controllers, services, utils, config) | 2     |
| Integration of **Express**, Redis, Nodemailer (or equivalent)      | 3     |
| Proper helper/utility functions                                    | 2     |

---

## **6. Express.js (10 Marks)**

API correctness and structure.

| Criteria                                                       | Marks |
| -------------------------------------------------------------- | ----- |
| Proper creation of REST routes                                 | 2     |
| Clean controllers with good separation of concerns             | 2     |
| Correct **status codes**, JSON responses, error handling       | 2     |
| Usage of middlewares (auth, validation, logging, rate limiter) | 2     |
| Routing structure (index routes, modular routes)               | 2     |

---

## **7. MongoDB (10 Marks)**

Database modeling & usage breakdown.

| Criteria                                                  | Marks |
| --------------------------------------------------------- | ----- |
| Schema design aligned with requirements                   | 2     |
| Proper **validation rules** in schema                     | 2     |
| Correct **relationships** (Users ↔ Vehicles ↔ Trips etc.) | 2     |
| Usage of **Mongo Aggregations** for analytics             | 2     |
| Usage of **MongoDB Atlas** as the cloud DB                | 2     |

---

## **8. Docker (10 Marks)**

Backend containerization evaluation.

| Criteria                                                                | Marks |
| ----------------------------------------------------------------------- | ----- |
| Proper Dockerfile setup                                                 | 2     |
| Docker image includes **Node + Redis in a single container** (required) | 3     |
| Runs correctly using the configured processes                           | 2     |
| Docker ignore, clean build context, efficiency                          | 1     |
| Docker image tested locally                                             | 2     |

---

## **9. AWS Deployment (10 Marks)**

Full deployment covering FE, BE, policies, and permissions.

| Criteria                                                     | Marks |
| ------------------------------------------------------------ | ----- |
| Creation of AWS IAM users, roles, permissions, policies      | 2     |
| Correct setup of S3 buckets (Next.js & React builds)         | 2     |
| Seamless FE ↔ BE integration using ECS backend URL           | 2     |
| Pushing backend image to **ECR**                             | 2     |
| Manual deployment of backend onto **ECS** using latest image | 2     |

---

## **10. CI/CD (10 Marks)**

GitHub Actions workflow correctness.

| Criteria                                   | Marks |
| ------------------------------------------ | ----- |
| Proper GitHub Actions workflow `.yml` file | 2     |
| Workflow builds Docker backend image       | 2     |
| Workflow pushes image to **AWS ECR**       | 2     |
| Proper use of GitHub Secrets for AWS auth  | 2     |
| Workflow runs successfully without errors  | 2     |

---

## **Total: 100 Marks**


