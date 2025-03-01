# DICS Collaborating System  
Design of a collaborative decision making system, on decentralized network, enhanced by AI

- [Summary](#summary)
- [1. How AI can streamline DICS](#1-how-ai-can-streamline-dics)
- [2. Front Office Modules](#2-front-office-modules)
- [3. Interaction Between Modules](#3-interaction-between-modules)
- [4. Security](#4-security)
- [5. User Experience (UX)](#5-user-experience-ux)
- [6. Global Architecture](#6-global-architecture)
- [7. Backend Development Tools](#7-backend-development-tools)
- [8. Resources](#8-resources)
- [9. Project Phases](#9-project-phases)
- [10. How To Participate](#10-how-to-participate)
- [11. Conclusion](#11-conclusion)

---

## Summary

DICS is (a project for) an intelligent, decentralized web system for collaborative decision making, tailored for organizations of all types and sizes. The platform integrates three sequential modules:

1. Discussion forum  
2. Collective drafting (to formulate voting statements)  
3. Voting system

**Software and Hardware Environment:**

- ***Software.*** DICS is designed to be ***decentralized*** (with modules acting as both client and server), ***modular*** (to accommodate future technological advancements), and entirely composed of ***free software*** (per [fsf.org](https://fsf.org)).

- ***Hardware.*** DICS operates on the [DIOS network](https://github.com/FJortay/DIOS-Operating-System), which is P2P, wireless, and AI-enhanced. Each organization member is expected to use two types of [open source terminals](https://www.gnu.org/philosophy/free-hardware-designs.en.html): a desktop computer and an IPV card—a forthcoming smart card-like device equipped with a touchscreen and virtual keyboard for secure identification, payments, and voting. Notably, the system intentionally avoids smartphone dependency to address concerns over mental health and security.

In the following sections (3 to 8), open-source solutions are proposed for each component. These modules must be designed for standardized integration to facilitate system evolvability. Given that many software packages predate today’s conversational AI advancements, certain elements of DICS may need to be developed from scratch or adapted through integration with existing tools.

*DICS Collaborative Management, alongside [DIOS Operating System](https://github.com/FJortay/DIOS-Operating-System), forms part of the [DISCO Collective Intelligence](https://github.com/FJortay/DISCO-Collective-Intelligence) project.*

---

## 1. How AI can streamline DICS

### 1.1. **Discussion Forum**

- ***Automated Moderation:***  
  Leveraging natural language processing (NLP), AI monitors discussions in real time to filter out inappropriate content and maintain a constructive debate environment. It can also serve as an expert participant, enriching discussions with contextual insights.

- ***Discussion Summarization:***  
  AI-driven tools distill long threads into concise summaries, enabling users to quickly grasp key discussion points.

### 1.2. **Collective Drafting**

- ***Writing Assistance:***  
  Integrated AI offers real-time grammar and style enhancements, ensuring that voting statements and collaborative texts are clear and coherent.
  
- ***Intelligent Version Management:***  
  When multiple contributors are involved, AI algorithms merge different document versions, detect inconsistencies, and propose a unified draft.

### 1.3. **Voting System**

- ***Impact Simulation and Forecasting:***  
  Predictive models simulate the potential consequences of proposed decisions, enabling voters to make more informed choices before finalizing votes.
  
- ***Vote Security and Verification:***  
  AI monitors voting behavior and leverages cryptographic techniques to detect anomalies or potential fraud in real time.

---

## 2. Front Office Modules

### 2.1. Discussion Forum

- ***Content Moderation and Analysis:***
  - *[spaCy](https://spacy.io/):* A robust open source NLP library that analyzes messages and flags inappropriate content.
  - *[Hugging Face Transformers](https://huggingface.co/transformers/):* Provides sentiment analysis, classification, and automatic summarization capabilities.

### 2.2. Collaborative Writing

- ***Real-Time Editing:***
  - *[Etherpad](https://etherpad.org/):* A containerizable, open source editor deployed on each [DIOS](https://github.com/FJortay/DIOS-Operating-System) node to support decentralized collaboration.
  - *[CodiMD](https://github.com/hackmdio/codimd):* An alternative open source tool optimized for collaborative editing.
  
- ***Writing Assistance:***
  - *[LanguageTool](https://languagetool.org/):* Offers real-time corrections for grammar and style via an API integration.

### 2.3. Voting System

- *[Helios](https://heliosvoting.org/)* and *[Belenios](https://www.belenios.org/)* are tailored for electoral processes, although they may require adaptation for referendum-style and large-scale voting scenarios.
- *[Loomio](https://www.loomio.com/)* unifies the three decision-making phases but is based on a client-server model. Ongoing efforts aim to decentralize its processes, scale up for mass participation, and integrate AI-based anomaly detection.

---

## 3. Interaction Between Modules

### *API*
- *[OpenAPI / Swagger](https://swagger.io/specification/):*  
  Standardizes and documents the interfaces between microservices, ensuring smooth and reliable communication.

### *Decentralized Message Bus*
- *[IPFS PubSub](https://github.com/libp2p/specs/tree/master/pubsub):*  
  Employs IPFS’s publish/subscribe mechanism to enable decentralized message exchange among nodes.

### *Data Modeling*
- *Decentralized File Storage:*  
  - *[IPFS (InterPlanetary File System)](https://ipfs.io/):* Facilitates distributed hosting and sharing of files and collaborative data.
- *Decentralized Database:*  
  - *[OrbitDB](https://orbitdb.org/):* A NoSQL database that operates on IPFS, ideal for maintaining histories and collaborative contributions.
- *Distributed Ledger (if needed):*  
  - *[BigchainDB](https://www.bigchaindb.com/):* Provides an immutable ledger for recording votes and document modifications.

---

## 4. Security

### *Decentralized Identity Management*
- *[Hyperledger Indy](https://www.hyperledger.org/use/hyperledger-indy):*  
  Delivers decentralized identity management using DIDs, granting users control over their own authentication data.

### *Encryption Libraries*
- *[OpenSSL](https://www.openssl.org/):*  
  Ensures that all data in transit and at rest is securely encrypted.
- *[Libsodium](https://libsodium.gitbook.io/doc/):*  
  Offers comprehensive encryption support tailored for decentralized applications.

### *Decentralized Fault Tolerance*
- *[IPFS](https://ipfs.io/)* & *[OrbitDB](https://orbitdb.org/):*  
  Built-in data redundancy across the network significantly enhances fault tolerance.

### *Distributed Monitoring*
- Tools like *[Prometheus](https://prometheus.io/)* and *[Grafana](https://grafana.com/)*—adaptable to federated modes within [DIOS](https://github.com/FJortay/DIOS-Operating-System)—collect and visualize metrics across nodes without centralizing control.

---

## 5. User Experience (UX)

### *Interactive Guides:*
  - *[Intro.js](https://introjs.com/):*  
    Provides step-by-step interactive tutorials to familiarize users with the platform.
  
### *Feedback Collection:*
  - *[LimeSurvey](https://www.limesurvey.org/):*  
    A self-hosted survey tool for collecting user feedback.
  - *[Matrix](https://matrix.org/):*  
    A decentralized communication protocol that supports asynchronous feedback collection and analysis.

---

## 6. Global Architecture

### *Containerization*
- *[Docker](https://www.docker.com/):*  
  Encapsulates microservices in a standardized format, simplifying deployment and scalability.

### *Decentralized Orchestration*
- *[Docker Swarm](https://docs.docker.com/engine/swarm/):*  
  Adaptable for decentralized environments (or integrated with [DIOS](https://github.com/FJortay/DIOS-Operating-System)) to coordinate nodes without a centralized controller.

### *P2P Infrastructure*
- *[DIOS](https://github.com/FJortay/DIOS-Operating-System):*  
  Forms the underlying decentralized network, enabling distributed service deployment in a simplified [OSI model](https://en.wikipedia.org/wiki/OSI_model) where DICS acts as the upper layer.

---

## 7. Backend Development Tools

- *[Node.js](https://nodejs.org/)* with *[Express](https://expressjs.com/):*  
  Ideal for developing APIs and microservices, containerized for deployment on [DIOS](https://github.com/FJortay/DIOS-Operating-System).
- *[Python](https://www.python.org/)* with *[Flask](https://flask.palletsprojects.com/)* or *[Django](https://www.djangoproject.com/):*  
  Suitable for building backend services specifically optimized for decentralized environments.

---

## 8. Resources

### *Co-management:*
- *Global:* [democratiedirecte.net/definition](https://democratiedirecte.net/definition)
- *Local:* [democratiedirecte.net/association](https://democratiedirecte.net/association)

---

## 9. Project Phases

1. Improve this README (deadline: t+1Y).
   
2. Integration of existing free software, on a client-server WAN (deadline: t+3Y).
   
3. Migration of the system on a P2P LAN (deadline: t+6Y).
   
4. Migration of the system on a P2P WAN (deadline: t+8Y).
   
5. Based on the information collected during the previous phases:
   
   - Detail missing features;
     
   - Define standards for systemic scalability of DICS modular components (deadline: t+9Y). 

---

## 10. How To Participate

We are at phase 1. Help improve this README.

---

## 11. Conclusion

What once appeared unattainable—building a decentralized system for collaborative decision making like "DICS on [DIOS](https://github.com/FJortay/DIOS-Operating-System)" (forming the basis of [DISCO](https://github.com/FJortay/DISCO-Collective-Intelligence))—is now possible. Advances in AI empower us to create collective intelligence systems with capabilities that were unimaginable just a few years ago. While challenges persist, the potential for innovation, enhanced security, and deeper democratic engagement is truly inspiring.
