# OpenID Connect Workshop

This workshop was given successfully to an Azure customer on 3 December 2019 and is designed to walkthrough 
[https://github.com/julie-ng/azure-openid-connect-demo](https://github.com/julie-ng/azure-openid-connect-demo) and designed to run on local machine. 

<img src="./images/preview-aad-login.png" alt="Preview: Azure Active Directory Login" width="350">

### Requirements

To run this locally, participants only require

- Docker with Docker Compose
- Client Credentials (contact [@julie-ng](https://github.com/julie-ng/)) or create your own demo Azure Active Directory in the [free tier](https://azure.microsoft.com/en-us/pricing/details/active-directory/)

# Workshop Variations

There are 2 variations to this workshop to choose from depending on skill level of participants.

## Variation #1 - Monolithic (easy)

Additionally, the [middleware](https://github.com/julie-ng/azure-openid-connect-demo) component on the `master` branch runs as a standalone.

![Monolith Variation](./images/architecture-monolith.svg)

To run this version, please visit the repo for further details at [azure-openid-connect-demo &rarr;](https://github.com/julie-ng/azure-openid-connect-demo)


## Variation #2 - Microservice Architecture (intermediate)

If you use the submodules and `docker-compoes.yaml` in this git repository, you have a microservice-like architecture where the [frontend](https://github.com/julie-ng/openid-demo-frontend) is an independently deployable [VueJS](https://vuejs.org/) Single Page Application and separate from the backend.

Note: this version is designed to fail out of the box. If you follow the readme, however, you will get it working easily.

![Monolith Variation](./images/architecture-services.svg)

This setup is trickier.

Note: the middleware uses a `middleware-only` branch, not `master` in the submodule.


### Step 1 - Clone

Clone this repository

```
git clone https://github.com/julie-ng/aad-oidc-workshop
```

### Step 2 - Initialize Submodules

```
git submodule update --init
```

### Step 3 - Configure AAD Client

1. Copy `./oidc-demo-middleware/.env.sample` and create a `.env` file.

2. Update `.env` file with the proper configuration, including credentials below. 

| Param | Value |
|:--|:--|
| Tenant ID | `430344f7-8876-4aa6-a2bd-a0e59401cc37` | 
| Client ID | ~~`75eb4de7-46eb-469a-88de-71d0f6616e0d`~~ |
| secret 1 | ~~`.bDtmZ1pAgosjzWtu?md8WFwCYQv:?78`~~ |
| secret 2 | ~~`Lc:y=E=tjM=nl4AQO2ZqoI8K6/i3=nyw`~~ |
| secret 3 | ~~`Ii0GH@8-4v6bcE.P/E1i56Z?7fLRqHnW`~~ |
| secret 4 | ~~`D]GERQUs8KNb3Q86Xy[_qZut[cpL]7bV`~~ |
| secret 5 | ~~`B1-:=1zoIOxqua9o@N1h08vPT89aJluU`~~ |

Note: these credentials are revoked, but left here for the workshop template.

### Step 4 - Configure Cookie Encryption Keys

See the middleware `README.md` for further setup details, incl. generating cookie encryption keys.

# Demo Users

This demo uses a demo Azure AD tenant (aadoauthdemo.onmicrosoft.com), that only has fake users for testing:

| Name | Username | Password | 
|:--|:--|:--|
| Alice Samson | alice@aadoauthdemo.onmicrosoft.com | WalterGropius5 |
| Phoebe Buffay | phoebe@aadoauthdemo.onmicrosoft.com | WalterGropiusStrasse5 |
| Rachel Gabor | rachel@aadoauthdemo.onmicrosoft.com | WalterGropiusStrasse5 |
| Ross Smith | ross@aadoauthdemo.onmicrosoft.com | WalterGropiusStrasse5 |
| Joey Taylor | joey@aadoauthdemo.onmicrosoft.com | WalterGropiusStrasse5 |

If you get the app successfully running, you will be able to login with the users above and view your ID Token:

![Preview: Demo](./images/preview-demo.png)

# Workshop Outline for Trainers

This workshop was originally prepared for a closed audience and the branded presentation and custom slides cannot be shared publicly. If you are considering giving a workshop on this topic, feel free to use this outline:

## Workshop Goals

By end of this workshop (90 minutes), participants should learn fundamentals of cloud identity:

- Difference between OpenID Connect and OAuth 2.0
- Security implications with OIDC and OAuth architectures
- Hands-On implementation OpenID Flows (on local computer with Docker)

## Key Topics

- History - where did OAuth 2.0 come from?
- **Authentication (AuthN) & OpenID Connect**
	- Actors:
		1. Client App
		2. User
		3. Identity Provider
	- ID Tokens
	- Claims
	- Compare with other security mechanisms: passwords, certificates, public/private keys
- **Authorization (AuthZ) & OAuth 2.0**
	- Actors:
		1. Client App
		2. User
		3. Identity Provider
		4. _Data_
	- Scopes
	- Implicit Flow vs Authorization Code Flow
	- Security: Frontends vs Backends
	- User Principals vs Service Principals
	- One person, many roles
	- Apps can have many roles:
		- Client Role
		- Resource Server Role
	- People can span many groups

## 5 Takeaways for Participants

Participants should understand these key concepts at end of the workshop:

1. Authentication asks “who are you?”
2. Authorization asks “do you have access?”
3. “Application” is a Conceptual Term
4. Use Authorization Code Flow because backend channels are more secure
5. Interaction with protected resources may involved mixed contexts and roles.
