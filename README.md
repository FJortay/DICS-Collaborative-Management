# DICS
Co-management system, on decentralized network, with IA

- [Summary](summary)
- [Global Platform Architecture](global-platform-architecture)
- [Detailed Technical Specifications](detailed-technical-specifications)

## Summary
We want to design a decentralized and intelligent co-management platform, usable by any type of organization (small local association, company, municipality, State) operating according to a direct democracy model.

The three main application modules of this platform are:

1. discussion forum;
2. collective writing (in particular of voting statements);
3. voting system.

The four instances of this system (each using the three modules) are:

- control (are the internal regulations correctly applied?);
- audit (improvement of the internal regulations);
- projects (development of the organization);
- operational (daily management).

Software and hardware environment:

- software: the system should be modular (in order to facilitate technological evolution) and composed exclusively of free software (in the sense of fsf.org) and decentralized (therefore both client and server). The integration of existing solutions should be preferred to the development of existing modules.

- hardware: this platform would be intended to run on the DIOS network (project), which would be smart, P2P and wireless (see https://github.com/FJortay/DIOS). On the other hand, each member of the organization is supposed to use two types of open source terminals: a desktop computer and an IPV card (a smart card-type device, not yet in existence, with a touch screen and virtual keyboard, dedicated to identification, payments and voting). The system cannot rely on the use of a smartphone (for reasons of mental health and computer security).

### **1. Global Architecture of the Platform**  

#### **a. Modular and Service-Oriented Architecture**  
- **Containerization:**  
  - **Docker**: To package microservices in a standardized way.  
- **Decentralized Orchestration:**  
  - **Docker Swarm** integrated within a decentralized network (via DIOS) or adapting the DIOS solution itself to coordinate nodes, avoiding traditional centralized orchestrators.

#### **b. Decentralized Infrastructure**  
- **P2P Infrastructure:**  
  - **DIOS** (https://github.com/FJortay/DIOS): Enables deployment and execution of the platform on a decentralized network, ensuring service distribution without a central control point.

---

### **2. Interaction Between Modules and Instances**  

#### **a. API Schemas and Communication Protocols**  
- **API Design:**  
  - **OpenAPI / Swagger**: Defines and documents communication interfaces between microservices in a standardized way.

#### **b. Data Flow Management**  
- **Decentralized Message Bus:**  
  - **IPFS PubSub**: IPFS’s publish/subscribe mechanism enables message exchange between nodes in a decentralized manner, without a central server.

#### **c. Service Orchestration**  
- **Decentralized Coordination:**  
  - Service coordination can be handled by the DIOS protocol, distributing tasks among participating nodes, eliminating the need for a central orchestrator.

---

### **3. Detailed Technical Specifications**  

#### **a. Data Modeling**  
- **Decentralized File Storage:**  
  - **IPFS (InterPlanetary File System)**: For distributed hosting and sharing of documents, files, and collaborative data.  
- **Decentralized Database:**  
  - **OrbitDB**: A decentralized NoSQL database running on IPFS, suited for storing histories, messages, and collaborative contributions.  
- **Distributed Ledger (if needed):**  
  - **BigchainDB**: Registers votes and modifications in an immutable ledger, leveraging decentralized infrastructure.

#### **b. Interfaces and Protocols**  
- **Documentation and Standardization:**  
  - **OpenAPI/Swagger** (as mentioned) ensures API interoperability between microservices.

---

### **4. AI-Powered Module Design**  

#### **a. Discussion Forum**  
- **Content Moderation and Analysis:**  
  - **spaCy**: Open-source NLP library for analyzing messages and automatically detecting inappropriate content.  
  - **Hugging Face Transformers**: Implements classification models, sentiment analysis, and automatic discussion summarization.

#### **b. Collaborative Writing**  
- **Real-Time Editing:**  
  - **Etherpad** or **CodiMD/HackMD**: These open-source collaborative tools can be containerized and deployed on each DIOS node, ensuring decentralized editing.  
- **Writing Assistance:**  
  - **LanguageTool**: Provides real-time grammar and style corrections, integrated via API into the editor.

#### **c. Voting System**  
- **Decentralized and Secure Voting:**  
  - **Helios Voting**: An open-source electronic voting system that, when adapted and deployed on DIOS, offers transparency and verifiability in a distributed environment.  
  - Complementary algorithms (developed in Python or Node.js) can be added to detect anomalies or suspicious behavior in the voting process.

---

### **5. Security and Decentralization**  

#### **a. Authentication and Authorization**  
- **Decentralized Identity Management:**  
  - **Hyperledger Indy** (and associated tools like **Aries**) provides a decentralized identity solution using **DIDs (Decentralized Identifiers)**, allowing users to control their authentication data without a central server.

#### **b. Data Encryption**  
- **Encryption Libraries:**  
  - **OpenSSL** and **Libsodium**: Used in each microservice to encrypt data in transit and at rest, ensuring security even in a distributed environment.

#### **c. Resilience and Availability**  
- **Decentralized Fault Tolerance:**  
  - **IPFS & OrbitDB**: Data redundancy is naturally ensured through the decentralized network.  
- **Distributed Monitoring:**  
  - While tools like **Prometheus** and **Grafana** are typically used in centralized setups, they can be deployed in a federated mode on DIOS to collect and visualize metrics from multiple nodes without centralization.

---

### **6. UX/UI Design and Accessibility**  

#### **a. User Interface Design**  
- **Frontend Frameworks:**  
  - **React**, **Vue.js**, or **Angular**: For developing interactive and responsive web interfaces hosted on decentralized network nodes.  
- **UI & Accessibility Libraries:**  
  - **Bootstrap** or **Material-UI** (for React): To create modern, accessible interfaces deployable in a decentralized, self-hosted environment.

#### **b. User Experience (UX)**  
- **Interactive Guides:**  
  - **Intro.js**: Creates interactive tutorials embedded within the web application.  
- **Feedback Collection:**  
  - **LimeSurvey** (self-hosted) or **Matrix-based solutions** for asynchronous communications, allowing feedback collection and analysis in a decentralized framework.

---

### **7. Integration of Development Tools and Technologies**  

#### **a. Backend & Frontend Development Tools**  
- **Backend:**  
  - **Node.js** with **Express** or **Python** with **Flask/Django**: API and microservices development, containerized and deployed on DIOS.  
- **Frontend:**  
  - **React**, **Vue.js**, or **Angular**: For building dynamic interfaces, integrated into the decentralized ecosystem.

#### **b. Version Control and CI/CD Tools**  
- **Versioning:**  
  - **Git**: A naturally distributed version control system, ideal for 100% decentralized development.  
- **Continuous Integration / Continuous Deployment (CI/CD):**  
  - Self-hosted CI/CD solutions like **Drone CI**, or pipelines deployed on DIOS, enabling automated testing and deployment without relying on a central service.

#### **c. Documentation and Communication**  
- **Technical Documentation:**  
  - **MkDocs** or **Sphinx**: For creating decentralized-hosted documentation, e.g., on IPFS or via DIOS nodes.  
- **Decentralized Communication:**  
  - **Matrix/Element**: An open-source, decentralized communication network, allowing teams to collaborate without a central server.

---

### **Conclusion**  

By combining these open-source tools designed for a 100% decentralized environment, the **DICS** platform can be deployed on **DIOS**, ensuring modularity, security, and resilience necessary for **direct democracy governance**. Each component, from microservice orchestration to identity management, is carefully selected to uphold decentralization principles, guaranteeing system autonomy and transparency.
