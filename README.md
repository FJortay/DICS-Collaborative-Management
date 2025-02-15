# DICS
Co-management system, on decentralized network, with AI

- [1. Summary](summary)
- [2. How AI can streamline DICS](how-ai-can-streamline-dics)
- [3. AI-Powered Module](ai--powered-module)
- [4. Interaction Between Modules](interactionbetweenmodules)
- [5. Security](security)
- [6. User Experience (UX)](user-experience-(ux))
- [7. Global Architecture](global-architecture)
- [8. Backend Development Tools](backend-development-tools)
- [9. How To Participate](how-to-particpate)
- [10. Conclusion](conclusion)

### 1. Summary
We want to design an intelligent and decentralized co-management web platform, intended for any type of organization (local association, company, municipality, State) wishing to operate under the rules of direct democracy.

DICS is composed of three main applicative modules, combined into a chronological series :

1. discussion forum;
2. collective writing (in particular of voting statements);
3. voting system.

This suite of three modules allows the four main activities of organization management to be operated in a decentralized manner:

- *control* : are the organisation internal regulations correctly applied?
- *audit* : internal regulations improvement;
- *projects* : organization developement;
- *operational* : daily management.

Software and hardware environment:

- ***Software.*** The system should be ***decentralized*** (therefore both client and server), ***modular*** (in order to facilitate technological evolution) and exclusively composed of ***free software*** (as defined by [fsf.org](https://fsf.org)). 

- ***Hardware.*** DICS would be intended to run on the [DIOS network](https://github.com/FJortay/DIOS) (project), which would be P2P, wireless and AI driven. Regarding organization members, these are assumed to use two kinds of [open source terminals](https://www.gnu.org/philosophy/free-hardware-designs.html) : a desktop computer and an IPV card (a not yet existing smart card-type device with touch screen and virtual keyboard, dedicated to identification, payments and voting). The system should not rely on any use of smartphone (for reasons of mental health and computer security).

Sections 3 to 8 present a open source solution for each point. However, these were not designed and developed in the current new era of conversational AI. As a result, much of DICS may need to be built from scratch.  Nevertheless, assessing what is presently available may be a good choice for a first step. And the second one may even consist in integrating them... 

*This is a "[Building AI course project](https://buildingai.elementsofai.com/)".*

---

### 2. How AI can streamline DICS

2.1. **Discussion Forum**  

   - ***Automated Moderation***  
     AI can analyze messages in real time (via natural language processing algorithms) to detect and filter inappropriate content.  
     
   - ***Discussion Summarization***  
     AI-powered tools can generate concise summaries of long discussions, helping users quickly grasp key points.  

2.2. **Collective Drafting**  

   - ***Writing Assistance***  
     AI can provide real-time grammatical and stylistic corrections, suggest rewordings, and improve text coherence—especially useful for drafting voting statements.  
     
   - ***Intelligent Version Management***  
     With multiple contributors, AI-driven algorithms can merge different versions, detect inconsistencies, and propose a coherent synthesis of collaboratively written documents. 

2.3. **Voting System**  

   - ***Vote Security and Verification***  
     By analyzing voting behavior and applying cryptographic techniques, AI can detect anomalies or fraud attempts in real time. 
      
   - ***Impact Simulation and Forecasting***  
     Before finalizing votes, predictive models can simulate the potential consequences of proposed decisions, assisting in informed decision-making.  
---

### 3. AI-Powered Modules

#### 3.1. Discussion Forum

- ***Content Moderation and Analysis***
  
  - *[spaCy](https://spacy.io/)* : Open-source NLP library for analyzing messages and automatically detecting inappropriate content.
    
  - *[Hugging Face Transformers](https://huggingface.co/transformers/)* : Implements classification models, sentiment analysis, and automatic discussion summarization.

#### 3.2. Collaborative Writing

- ***Real-Time Editing***
  
  - *[Etherpad](https://etherpad.org/)* : An open-source collaborative editor that can be containerized and deployed on each DIOS node, ensuring decentralized editing.
    
  - *[CodiMD](https://github.com/hackmdio/codimd)* : Another open-source collaborative tool suitable for decentralized editing.

- ***Writing Assistance***
  
  - *[LanguageTool](https://languagetool.org/)* : Provides real-time grammar and style corrections, integrated via API into the editor.

#### 3.3. Decentralized and Secure Voting

  - *[Helios](https://heliosvoting.org/)* and *[Belenios](https://www.belenios.org/)* are designed for elections (not realy for referendums). Loomio integrates the three phases of decision-making, but its protocols are less secure. All three are designed in client-server mode. So there is work to be done : decentralize processes, capacity to handle boths referendums and elections, large number of voters, AI detection of anomalies or suspicious behavior in the voting process,...

---

### **4. Interaction Between Modules**

#### *API*

  - *[OpenAPI / Swagger](https://swagger.io/specification/)* : Defines and documents communication interfaces between microservices in a standardized way. Ensures API interoperability between microservices.

#### *Decentralized Message Bus*

  - *[IPFS PubSub](https://github.com/libp2p/specs/tree/master/pubsub)* : IPFS’s publish/subscribe mechanism enables message exchange between nodes in a decentralized manner, without a central server.

#### *Data Modeling*

- *Decentralized File Storage*
  - *[IPFS (InterPlanetary File System)](https://ipfs.io/)* : For distributed hosting and sharing of documents, files, and collaborative data.

- *Decentralized Database*
  - *[OrbitDB](https://orbitdb.org/)* : A decentralized NoSQL database running on IPFS, suited for storing histories, messages, and collaborative contributions.

- *Distributed Ledger (if needed)*
  - *[BigchainDB](https://www.bigchaindb.com/) : Registers votes and modifications in an immutable ledger, leveraging decentralized infrastructure.

---

### 5. Security

#### *Decentralized Identity Management*

  - *[Hyperledger Indy](https://www.hyperledger.org/use/hyperledger-indy)* : Provides a decentralized identity solution using DIDs (Decentralized Identifiers), allowing users to control their authentication data without a central server.

#### *Encryption Libraries*

  - *[OpenSSL](https://www.openssl.org/)* : Used in each microservice to encrypt data in transit and at rest, ensuring security even in a distributed environment.
    
  - *[Libsodium](https://libsodium.gitbook.io/doc/)* : Another library for encryption, suitable for securing data in decentralized applications.

#### *Decentralized Fault Tolerance*
  - *[IPFS](https://ipfs.io/) & [OrbitDB](https://orbitdb.org/)* : Data redundancy is naturally ensured through the decentralized network.

#### *Distributed Monitoring*

  - While tools like *[Prometheus](https://prometheus.io/)* and *[Grafana](https://grafana.com/)* are typically used in centralized setups, they can be deployed in a federated mode on DIOS to collect and visualize metrics from multiple nodes without centralization.

---

### 6. User Experience (UX)

- **Interactive Guides:**
  
  - *[Intro.js](https://introjs.com/)* : Creates interactive tutorials embedded within the web application.

- **Feedback Collection:**
  
  - *[LimeSurvey](https://www.limesurvey.org/)* : A self-hosted survey tool for collecting user feedback.
    
  - *[Matrix](https://matrix.org/)* : A decentralized communication protocol that can be used for asynchronous communications, allowing feedback collection and analysis in a decentralized framework.

---

### 7. Global Architecture 

#### *Containerization*

  - *[Docker](https://www.docker.com/)* : Packaging microservices in a standardized way.

 #### *Decentralized Orchestration*:
 
  - *[Docker Swarm](https://docs.docker.com/engine/swarm/)* : Integrated within a decentralized network (via DIOS) or adapting the DIOS solution itself to coordinate nodes, avoiding traditional centralized orchestrators.

#### *P2P Infrastructure*

  - *[DIOS](https://github.com/FJortay/DIOS)* : Enables deployment and execution of the platform on a decentralized network, ensuring service distribution without a central control point. In a very simple [OSI model](https://en.wikipedia.org/wiki/OSI_model) with only two layers, DICS could be seen as the upper layer, and DIOS the lower one.

---

### 8. Backend Development Tools

  - *[Node.js](https://nodejs.org/)* with *[Express](https://expressjs.com/)* for API and microservices development, containerized and deployed on DIOS.
    
  - [Python](https://www.python.org/)* with *[Flask](https://flask.palletsprojects.com/)* or *[Django](https://www.djangoproject.com/)* for developing backend services in a decentralized environment.

---

### **9. How to participate**  

Help improve this *first draft* README. This is the first step of a long journey...

---

### **10. Conclusion**  

Before 2023, a project like the DICS/[DIOS](https://github.com/FJortay/DIOS) system would have seemed unfeasible for a long time to come. But since then, conversational AI has emerged. It will not only help us design this ***collective intelligence system*** but also grant it capabilities that were unimaginable just a few years ago. The challenges to overcome, or circumvent, are certainly numerous and high, but in any case, the fruits of this research will be just as numerous and enriching.
