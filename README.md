## Blog Post

:scroll: See this [blog post](https://jvdevlab.com/blog/security/saml/wso2) for more details about this project.

## Description

This [GitHub project](https://github.com/jvdevlab/saml-wso2-is-demo-apps) is using Docker to launch [WSO2 Identity Server](https://wso2.com/identity-and-access-management/) and two Service Provider apps (Dispatch and Manager) demonstrating the usage of SAML 2.0.

## Setup

- Install [Docker](https://docs.docker.com/get-docker/).
- Clone the repo.

## Demo

- To start all three apps run

```bash
docker compose up
```

- Both Service Providers (Dispatch and Manager apps) will be automatically registered with IdP during deployment.
- Note that IdP <https://localhost:9443/carbon> comes with one user provisioned - `admin/admin`. This will work on all mentioned demo apps, but it's recommended to change the admin password and [create](https://is.docs.wso2.com/en/latest/learn/configuring-users/) a new demo user.
- Log in to Dispatch app <http://localhost:9051/saml2-web-app-pickup-dispatch.com>.
- Verify SSO setup by opening the Manager app in the same browser. <http://localhost:9052/saml2-web-app-pickup-manager.com> You should _not_ be asked to log in again. Signing in to the Manger app first and then navigating to the Dispatch app will have a similar effect.
- You can use [SAML-tracer](https://chrome.google.com/webstore/detail/saml-tracer/mpdajninpobndbfcldcmbpnnbhibjmch?hl=en) Chrome extension or similar tool to inspect SAML assertions.

![](https://jvdevlab.com/img/saml-wso2-is-demo-apps/06.PNG)

## Cleanup

```bash
docker compose down
```
