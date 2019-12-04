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
