# Zero-Knowledge Voto Digital

## Project Overview :page_facing_up:

-  **Brief Description:**

  The project aims to develop a zero-knowledge proof infrastructure solution for enhancing Costa Rica's digital identity system. Our goal is to strengthen citizen privacy by minimizing data collection, enabling individuals to access a wide range of valuable services without disclosing sensitive information. For this we plan to use Circom and the Polygon Blockchain network.

  We already have developed an initial Proof-of-concept you can find here: [zk-firma-digital](https://github.com/kuronosec/zk-firma-digital) . The project is Open Source under the Apache-2.0 license. As a next step for our project we want to show the capabilities of our approach by allowing Costa Rican citizens to participate in voting proposals in an anonymous way while keeping the ability to authenticate their identities and therefore proving that they are enabled to vote, all by using blockchain technologies.

-  **Core Idea:**

  The Costa Rican government offers an advanced digital identity system (Firma Digital) that allows residents or entities to sign documents with a digital identity validated by the central bank as CA and authenticate themselves on various public or private websites and services. However, there is a significant privacy concern related to sensitive data in Costa Rica. A small amount of identity information, such as a national ID number or car plate number, can lead to extensive data collection. Private companies can use this kind of data to harvest citizen data, for instance, by calling and offering them products or services without any previous request or permission. This fact is exceptionally relevant now that big corporations harvest indiscriminate user data to train AI models. Even worse, criminals are collecting this same data to perform identity theft and fraud, sometimes even making fraudulent calls from the jails.

  Our project aims to address these privacy issues by developing a zero-knowledge proof infrastructure using Polygon blockchain technology and ZK Circom circuits. This solution enables citizens to verify their identity and provide specific information without revealing actual personal details. By minimizing the distribution of sensitive data across various institutions and companies, we can significantly reduce the risk of data theft. Additionally, this system can authenticate users for diverse services, ensuring they are real individuals and not bots, without requiring sensitive information such as email addresses or phone numbers.

**Core Components and Architecture:**

- **Data Extraction and Validation**:
  - **Libraries and Applications**: Develop libraries in Javascript and Python to extract data from the Firma Digital certificate and validate signatures issued by the Certification Authority (CA).

  - **Certificate Validation:** Ensure that the certificate information and signature are authentic and belong to a Costa Rican resident and citizen.

- **Zero-Knowledge Proof Generation**:
  - **Data Extraction for ZK Proofs**: Extract necessary information from Firma Digital certificates to generate zero-knowledge proofs for identity.
  - **Off-Chain Management**: Manage identity validation off-chain (via web interfaces).

- **User Interfaces**:
  - **Graphical Interfaces**: Develop intuitive graphical interfaces for users and administrators to interact with the system seamlessly.
- **Allow users to anonymously participate in voting proposals**.
- **Integration with Polygon Blockchain**.

**Technology Stack:** The project employs a diverse and robust technology stack to achieve its objectives. Key technologies include:
  - **Javascript**: For developing front-end interfaces and certain back-end functionalities.
  - **Python**: For data extraction, validation, and interaction with the Firma Digital certificate system.
  - **Circom (ZK Proofs)**: To enable privacy-preserving identity verification and voting.
  - **Firma Digital**: Costa Rica’s digital identity infrastructure, providing the basis for identity verification.
  - **Polygon Blockchain**: To ensure secure, decentralized handling of identity and voting data.
  - **Solidity**: For creating smart contracts to manage identity validation and voting proposals on the Polygon blockchain. 

**Design Mockups/Prototypes:**

[authentication.png](https://github.com/kuronosec/zk-firma-digital/blob/main/images/authentication.png).

[signature.png](https://github.com/kuronosec/zk-firma-digital/blob/main/images/signature.png).

## Ecosystem Fit

**Projects from which we have taken inspiration:**

- **Circom**: A compiler allowing developers to create ZK circuits with its programming language intuitively.
- **Anon Aadhaar**: The Anon Aadhaar libraries, a project built for the Indian citizen Identity using the Circom utilities, share common goals and specifications with our current project. As the website describes, "Anon Aadhaar is a protocol for proving ownership of an Aadhaar identity (Indian Residence ID) in a privacy-preserving manner. It lets users generate a ZK proof of their identity by only revealing the information they want to share (to an application)." This definition aligns perfectly with our commitment to privacy and security, making it an ideal foundation for our proposed project.
- **Polygon ID Verifier**: An infrastructure we have set up based on Polygon ID to authenticate users with digital credentials while maintaining privacy, utilizing zero-knowledge proofs to reveal only necessary information [polygon-id-verifier](https://github.com/edenia/polygon-id-verifier).

**How is the idea of this project different or better?**

We were inspired both by Anon Aadhaar and ZK Passport to create our ZK Firma Digital project. However, those projects only allow users to validate government digital signatures by QR codes and X509 certificates, while ours allow users to use their ID smart cards to also sign arbitrary data. This makes our approach even more powerful and flexible allowing different people and entities to create their own type of authenticated data taking advantage of already built PKI infrastructures. It can be extended to other countries with similar technologies other than Costa Rica.

There is still no system like this in the Circom ecosystem. In addition, we want to provide an integration for Verifiable Credentials and Decentralized Identities using existing PKI infrastructure, while taking advantage of the ZKP capabilities to keep sensitive information private.

## Development Roadmap :open_book:

### Milestone 1 — Allow users to participate in voting proposals 

**Description:**
  - **Verifiable Credential Signature**: Enable users to sign voting data formatted as VC (JSON).
  - **Signature Validation**: Validate the signed voting data and citizen’s signature to confirm authenticity and eligibility.
  - **Circom vote privacy**: add circuits to validate the user ability to emit votes in a proposal and then allow them to vote in an anonymous way.
    - Validate type of certificate: resident, citizen, organization.

### Milestone 2 — Integration with Polygon Blockchain 

**Description:** 
  - **Smart Contracts**: Develop required smart contracts for user anonymous identity verification and vote proposal administration, such as counting and publication of results.
  - **Front End for voting process**: Create front-end interfaces for users to interact with the voting system and see a list of proposals, options, and results. This front-end should be usable from a mobile phone. If possible, the ZK proof creation will also be made on the phone or via Web.
  - **Record video of actual users using our solution**: Organize a small mockup election with real users trying our ZK solution and record a professional video of the event. This way, we can showcase and share our project's achievements and, at the same time, help detect and fix potential bugs.

## Extended Scope 

**Future Plans:**

We plan to extend the functionality of our proof-of-concept system to allow several use cases such as: 
- Anonymous proof of humanity
- Health data privacy
- Know Your Customer
- Privacy-Preserving Verification
- Anti-Sybil Mechanisms
- DAO Governance
- Quadratic Funding (QF)
- Wallet Recovery
- And more

Also we want to extend the usage of ID smart cards to other countries. For instance, the EU has similar kinds of IDs for their residents.

# How to run it locally

To install the necessary packages etc, run `yarn install`. 

The circuit-specific files are provided to the react frontend through express. 

To run the example, start the express server in `file-server` and the react application:
```
# Run fileserver:
cd src/file-server
node index.js

# Start react
yarn start
```

The circuit and related files are located in the folder `src/zkproof`. 

## See it working
When you generate a Zk credential from your Firma Digital, which is a JSON file, you can test it by authenticating in this PoC website:

* http://app.sakundi.io:8080/

You can find the source code here: https://github.com/kuronosec/zk-firma-web

Also you can find an example of the built verifiable credential here: https://github.com/kuronosec/zk-firma-digital/blob/main/src/examples/residence-credential.json



