# Getting Started with GitOps

<figure><img src="../.gitbook/assets/Git.png" alt=""><figcaption></figcaption></figure>

GitOps is a set of best practices that uses Git as the single source of truth for managing cloud-native application configurations and infrastructure deployments. Which means everything we manage using Git including application manifests, configurations, secrets and infrastructure.

## Key principles of GitOps <a href="#a8bd" id="a8bd"></a>

* The entire system is described declaratively.
* The desired state of the system is versioned in Git.
* Automatically pulls the state from Git and matches the platform state.
* Continuously monitor the actual system state and attempt to apply the desired state.

## GitOps Agent <a href="#ce1d" id="ce1d"></a>

A GitOps agent, such as ArgoCD or FluxCD, is responsible for monitoring Git repositories for changes and automatically deploying those changes to the target environment. The agent is typically deployed in the target environment and is configured to watch for changes in the Git repository.

When a change is detected, the agent retrieves the updated configuration files from the repository and uses them to deploy the application or update the infrastructure. It also keeps track of the current state of the environment and compares it with the desired state defined in the git repository, continuously working to reconcile the two.

## Use Cases <a href="#d62a" id="d62a"></a>

The most popular use case is Kubernetes deployments. Let’s check it out.

<figure><img src="../.gitbook/assets/CI_CD Pipeline.png" alt=""><figcaption></figcaption></figure>

In this scenario, there are two Git repositories. The first one is for application code and the second one is for application manifests. Also, the GitOps agent is deployed within the Kubernetes cluster.

1. Developer commits changes to the code repo.
2. CI pipeline will automatically build, test and push the image to the container registry.
3. CI pipeline also updates the Kubernetes manifests which are stored in the manifest repo.
4. GitOps agent will automatically detect the manifest repo changes and deploy the new changes to the cluster.

## Benefits <a href="#1d71" id="1d71"></a>

* GitOps agent detects and minimizes configuration drift.
* The cluster can be private because nobody needs direct access to it.
* All changes are recorded and tracked in Git, making it easy to understand what changes were made, when they were made, and by whom.

## Drawbacks <a href="#01c2" id="01c2"></a>

* Only handles deployments. We need to take care of the CI pipeline separately.
* All changes to the cluster need to be committed.
* Not easy to troubleshoot in a live environment because we need to do everything through Git or we need to disable the agent temporarily.



Hope you got a good idea about GitOps! See you in another article 🫡

Thank you!
