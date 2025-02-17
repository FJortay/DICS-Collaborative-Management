# DICS  
Co-management system on a decentralized network, enhanced by AI

- [1. Summary](#1-summary)
- [2. How AI can streamline DICS](#2-how-ai-can-streamline-dics)
- [3. AI-Powered Module](#3-ai-powered-modules)
- [4. Interaction Between Modules](#4-interaction-between-modules)
- [5. Security](#5-security)
- [6. User Experience (UX)](#6-user-experience-ux)
- [7. Global Architecture](#7-global-architecture)
- [8. Backend Development Tools](#8-backend-development-tools)
- [9. How To Participate](#9-how-to-participate)
- [10. Conclusion](#10-conclusion)

---

### 1. Summary

We want to design as an intelligent and decentralized co-management web platform for organizations (whether local associations, companies, municipalities, or states) that choose to operate under direct democracy. The decentralized platform is composed of three sequentially integrated applicative modules:

1. Discussion forum  
2. Collective writing (especially for drafting voting statements)  
3. Voting system

Together, these modules support the four main facets of organizational management:

- *Control:* Ensuring internal regulations are adhered to.
- *Audit:* Continuously refining internal regulations.
- *Projects:* Facilitating organizational development.
- *Operational:* Managing daily administrative tasks.

**Software and Hardware Environment:**

- ***Software.*** DICS is built to be ***decentralized*** (both client and server), ***modular*** (to ease future technological evolution), and entirely composed of ***free software*** (as defined by [fsf.org](https://fsf.org)).

- ***Hardware.*** DICS is intended to run on the [DIOS network](https://github.com/FJortay/DIOS), which is P2P, wireless, and AI-driven. Organization members are assumed to use two types of [open source terminals](https://www.gnu.org/philosophy/free-hardware-designs.html): a desktop computer and an IPV card (a future smart card-type device with a touchscreen and virtual keyboard for identification, payments, and voting). The system is deliberately designed without reliance on smartphones, addressing concerns regarding mental health and computer security.

In Sections 3 to 8, open source solutions are proposed for each component. However, many of these software packages were not originally developed with today’s conversational AI advances in mind. As such, significant parts of DICS may need to be built from scratch—or integrated with existing tools as a first step.

*This is a "[Building AI course project](https://buildingai.elementsofai.com/)".*

---

### 2. How AI can streamline DICS

#### 2.1. **Discussion Forum**

- ***Automated Moderation:***  
  AI analyzes messages in real time using natural language processing (NLP) to detect and filter inappropriate content, ensuring a respectful and constructive discussion environment.
  
- ***Discussion Summarization:***  
  AI-powered summarization tools generate concise overviews of extended discussions, allowing users to quickly grasp the key points and trends.

#### 2.2. **Collective Drafting**

- ***Writing Assistance:***  
  Real-time AI-driven grammar and style corrections, along with rewording suggestions, help improve clarity and coherence when drafting voting statements.
  
- ***Intelligent Version Management:***  
  When multiple contributors are involved, AI algorithms merge different versions, identify inconsistencies, and propose a coherent synthesis of collaboratively written documents.

#### 2.3. **Voting System**

- ***Vote Security and Verification:***  
  AI monitors voting behavior and leverages cryptographic techniques to detect anomalies or potential fraud in real time.
  
- ***Impact Simulation and Forecasting:***  
  Predictive models simulate the potential consequences of proposed decisions, enabling voters to make more informed choices before finalizing votes.

---

### 3. AI-Powered Modules

#### 3.1. Discussion Forum

- ***Content Moderation and Analysis:***

  - *[spaCy](https://spacy.io/):* An open source NLP library for analyzing messages and automatically detecting inappropriate content.
  
  - *[Hugging Face Transformers](https://huggingface.co/transformers/):* Implements classification models, sentiment analysis, and automatic summarization of discussions.

#### 3.2. Collaborative Writing

- ***Real-Time Editing:***

  - *[Etherpad](https://etherpad.org/):* A containerizable open source collaborative editor deployed on each DIOS node to ensure decentralized editing.
  
  - *[CodiMD](https://github.com/hackmdio/codimd):* Another open source collaborative tool well-suited for decentralized editing.
  
- ***Writing Assistance:***

  - *[LanguageTool](https://languagetool.org/):* Provides real-time grammar and style corrections that can be integrated via API into the editor.

#### 3.3. Decentralized and Secure Voting

- *[Helios](https://heliosvoting.org/)* and *[Belenios](https://www.belenios.org/)* have been designed for elections, though they may require adaptation for referendums and large-scale voting scenarios.  

- *[Loomio](https://www.loomio.com/)* integrates the three decision-making phases but relies on a client-server model.  
  **Note:** There is ongoing work to decentralize these processes, extend their capacity to handle both referendums and elections, support a large number of voters, and incorporate AI-driven detection of anomalies or suspicious behavior.

---

### 4. Interaction Between Modules

#### *API*

- *[OpenAPI / Swagger](https://swagger.io/specification/):*  
  Standardizes and documents communication interfaces between microservices, ensuring seamless API interoperability.

#### *Decentralized Message Bus*

- *[IPFS PubSub](https://github.com/libp2p/specs/tree/master/pubsub):*  
  Utilizes IPFS’s publish/subscribe mechanism to enable message exchange between nodes in a fully decentralized manner.

#### *Data Modeling*

- *Decentralized File Storage:*
  - *[IPFS (InterPlanetary File System)](https://ipfs.io/):* Provides distributed hosting and sharing of documents, files, and collaborative data.
  
- *Decentralized Database:*
  - *[OrbitDB](https://orbitdb.org/):* A decentralized NoSQL database running on IPFS, ideal for storing histories, messages, and collaborative contributions.
  
- *Distributed Ledger (if needed):*
  - *[BigchainDB](https://www.bigchaindb.com/):* Maintains an immutable ledger to record votes and modifications, leveraging decentralized infrastructure.

---

### 5. Security

#### *Decentralized Identity Management*

- *[Hyperledger Indy](https://www.hyperledger.org/use/hyperledger-indy):*  
  Offers a decentralized identity solution using Decentralized Identifiers (DIDs), empowering users to control their own authentication data.

#### *Encryption Libraries*

- *[OpenSSL](https://www.openssl.org/):*  
  Ensures that each microservice encrypts data in transit and at rest.
  
- *[Libsodium](https://libsodium.gitbook.io/doc/):*  
  Provides robust encryption support tailored for decentralized applications.

#### *Decentralized Fault Tolerance*

- *[IPFS](https://ipfs.io/)* & *[OrbitDB](https://orbitdb.org/):*  
  Built-in data redundancy across the decentralized network enhances fault tolerance.

#### *Distributed Monitoring*

- While tools like *[Prometheus](https://prometheus.io/)* and *[Grafana](https://grafana.com/)* are traditionally used in centralized environments, they can be deployed in federated modes within DIOS to collect and visualize metrics across nodes without centralization.

---

### 6. User Experience (UX)

- **Interactive Guides:**

  - *[Intro.js](https://introjs.com/):*  
    Implements interactive tutorials that guide users through the web application.
  
- **Feedback Collection:**

  - *[LimeSurvey](https://www.limesurvey.org/):*  
    A self-hosted survey tool for gathering user feedback.
    
  - *[Matrix](https://matrix.org/):*  
    A decentralized communication protocol that supports asynchronous feedback collection and analysis.

---

### 7. Global Architecture

#### *Containerization*

- *[Docker](https://www.docker.com/):*  
  Packages microservices in a standardized format, simplifying deployment.

#### *Decentralized Orchestration*

- *[Docker Swarm](https://docs.docker.com/engine/swarm/):*  
  Can be adapted for use in a decentralized network (or integrated with DIOS) to coordinate nodes without a traditional central orchestrator.

#### *P2P Infrastructure*

- *[DIOS](https://github.com/FJortay/DIOS):*  
  Provides the underlying decentralized network for deployment and execution of DICS services, ensuring service distribution without centralized control. In a simplified [OSI model](https://en.wikipedia.org/wiki/OSI_model) with only two layers, DICS functions as the upper layer while DIOS forms the lower layer.

---

### 8. Backend Development Tools

- *[Node.js](https://nodejs.org/)* with *[Express](https://expressjs.com/):*  
  For API and microservices development, containerized and deployed on DIOS.
  
- *[Python](https://www.python.org/)* with *[Flask](https://flask.palletsprojects.com/)* or *[Django](https://www.djangoproject.com/):*  
  For building backend services tailored to a decentralized environment.

---

### 9. How To Participate

Help refine this *first draft* README and contribute ideas to evolve the DICS platform. Your input is essential as we split the *"Key Software Modules"* into several sub-projects and work collaboratively towards a fully decentralized, AI-enhanced co-management system.

---

### 10. Conclusion

Before 2023, a project like the DICS/[DIOS](https://github.com/FJortay/DIOS) system might have seemed out of reach. However, advances in conversational AI now enable us to design and implement a truly collective intelligence system with capabilities that were unimaginable just a few years ago. While significant challenges lie ahead, the potential rewards—in terms of innovation, security, and democratic engagement—are vast and inspiring.
