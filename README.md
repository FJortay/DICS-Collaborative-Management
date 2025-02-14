# DICS
Co-management system, on decentralized network, with IA

- [1. Summary](summary)
- [2. Global Platform Architecture](global-platform-architecture)
- [3. Interaction Between Modules and Instances](interactionbetweenmodules-and-instances)
- [4. Detailed Technical Specifications](detailed-technical-specifications)
- [5. AI-Powered Module Design](ai--powered-module-design)
- [6. Security and Decentralization](security-and-ecentralization)
- [7. User Experience (UX)](user-experience-(ux))
- [8. Backend Development Tools](backend-development-tools)
- [9. Conclusion](conclusion)

### 1. Summary
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

​Here is the updated architecture design for the DICS platform, with links to the respective software tools:

---

### 2. Global Architecture of the Platform

#### a. Modular and Service-Oriented Architecture

- Containerization:
  - [Docker](https://www.docker.com/): To package microservices in a standardized way.

- *Decentralized Orchestration:*
  - [Docker Swarm](https://docs.docker.com/engine/swarm/): Integrated within a decentralized network (via DIOS) or adapting the DIOS solution itself to coordinate nodes, avoiding traditional centralized orchestrators.

#### **b. Decentralized Infrastructure**

- **P2P Infrastructure:**
  - [DIOS](https://github.com/FJortay/DIOS): Enables deployment and execution of the platform on a decentralized network, ensuring service distribution without a central control point.

---

### **3. Interaction Between Modules and Instances**

#### **a. API Schemas and Communication Protocols**

- **API Design:**
  - [OpenAPI / Swagger](https://swagger.io/specification/): Defines and documents communication interfaces between microservices in a standardized way.

#### **b. Data Flow Management**

- **Decentralized Message Bus:**
  - [IPFS PubSub](https://github.com/libp2p/specs/tree/master/pubsub): IPFS’s publish/subscribe mechanism enables message exchange between nodes in a decentralized manner, without a central server.

#### **c. Service Orchestration**

- **Decentralized Coordination:**
  - Service coordination can be handled by the DIOS protocol, distributing tasks among participating nodes, eliminating the need for a central orchestrator.

---

### **4. Detailed Technical Specifications**

#### **a. Data Modeling**

- **Decentralized File Storage:**
  - [IPFS (InterPlanetary File System)](https://ipfs.io/): For distributed hosting and sharing of documents, files, and collaborative data.

- **Decentralized Database:**
  - [OrbitDB](https://orbitdb.org/): A decentralized NoSQL database running on IPFS, suited for storing histories, messages, and collaborative contributions.

- **Distributed Ledger (if needed):**
  - [BigchainDB](https://www.bigchaindb.com/): Registers votes and modifications in an immutable ledger, leveraging decentralized infrastructure.

#### **b. Interfaces and Protocols**

- **Documentation and Standardization:**
  - [OpenAPI/Swagger](https://swagger.io/specification/): Ensures API interoperability between microservices.

---

### **5. AI-Powered Module Design**

#### **a. Discussion Forum**

- **Content Moderation and Analysis:**
  - [spaCy](https://spacy.io/): Open-source NLP library for analyzing messages and automatically detecting inappropriate content.
  - [Hugging Face Transformers](https://huggingface.co/transformers/): Implements classification models, sentiment analysis, and automatic discussion summarization.

#### **b. Collaborative Writing**

- **Real-Time Editing:**
  - [Etherpad](https://etherpad.org/): An open-source collaborative editor that can be containerized and deployed on each DIOS node, ensuring decentralized editing.
  - [CodiMD](https://github.com/hackmdio/codimd): Another open-source collaborative tool suitable for decentralized editing.

- **Writing Assistance:**
  - [LanguageTool](https://languagetool.org/): Provides real-time grammar and style corrections, integrated via API into the editor.

#### **c. Voting System**

- **Decentralized and Secure Voting:**
  - [Helios Voting](https://heliosvoting.org/): An open-source electronic voting system that, when adapted and deployed on DIOS, offers transparency and verifiability in a distributed environment.
  - Complementary algorithms (developed in Python or Node.js) can be added to detect anomalies or suspicious behavior in the voting process.

---

### **6. Security and Decentralization**

#### **a. Authentication and Authorization**

- **Decentralized Identity Management:**
  - [Hyperledger Indy](https://www.hyperledger.org/use/hyperledger-indy): Provides a decentralized identity solution using DIDs (Decentralized Identifiers), allowing users to control their authentication data without a central server.

#### **b. Data Encryption**

- **Encryption Libraries:**
  - [OpenSSL](https://www.openssl.org/): Used in each microservice to encrypt data in transit and at rest, ensuring security even in a distributed environment.
  - [Libsodium](https://libsodium.gitbook.io/doc/): Another library for encryption, suitable for securing data in decentralized applications.

#### **c. Resilience and Availability**

- **Decentralized Fault Tolerance:**
  - [IPFS](https://ipfs.io/) & [OrbitDB](https://orbitdb.org/): Data redundancy is naturally ensured through the decentralized network.

- **Distributed Monitoring:**
  - While tools like [Prometheus](https://prometheus.io/) and [Grafana](https://grafana.com/) are typically used in centralized setups, they can be deployed in a federated mode on DIOS to collect and visualize metrics from multiple nodes without centralization.

---

### **7. User Experience (UX)**

- **Interactive Guides:**
  - [Intro.js](https://introjs.com/): Creates interactive tutorials embedded within the web application.

- **Feedback Collection:**
  - [LimeSurvey](https://www.limesurvey.org/): A self-hosted survey tool for collecting user feedback.
  - [Matrix](https://matrix.org/): A decentralized communication protocol that can be used for asynchronous communications, allowing feedback collection and analysis in a decentralized framework.

---

### **8. Backend Development Tools**

  - [Node.js](https://nodejs.org/): With [Express](https://expressjs.com/) for API and microservices development, containerized and deployed on DIOS.
  - [Python](https://www.python.org/): With [Flask](https://flask.palletsprojects.com/) or [Django](https://www.djangoproject.com/) for developing backend services in a decentralized environment.

---

### **9. Conclusion**  

By combining these open-source tools designed for a 100% decentralized environment, the **DICS** platform can be deployed on **DIOS**, ensuring modularity, security, and resilience necessary for **direct democracy governance**. Each component, from microservice orchestration to identity management, is carefully selected to uphold decentralization principles, guaranteeing system autonomy and transparency.
