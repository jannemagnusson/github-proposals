# New Github features

## Private forks

It is hard to work with open source in a large enterprise. For example, when we want to consume or contribute to an open source project, we cannot use forks, as this leaks coroporate information publicly. We would like a process that enables us to have the fork features to keep things  in sync and to allows us to create pull-requests, but to do this privately and have this in a private review process.
A new type of "private" fork, including a new kind of legal review request that we can introduce before a PR is opened towards the upstream project. Perhaps even different kinds of reviewes, like it is possible to have different CI checks required before merge. Could possibly be controlled like CODEOWNERS or something like that.

## Resource groups

Today, Github orgs solves two problems. They create a namespace for repositories and they control access to shared resources not tied to a specific repository. For large organizations, this creates an issue, as you want to controll access to shared resousources in ways that does not match how we want to name repositotires. And most importantly, the repo name serves as an idenfier in many, many different places and changing this is very cumbersome. Which means that if we want to change how resources are distributed, we would need to change which org a repo belongs to, even if that does not necessariy controll access to the repository in question (as this is handled by teams). Using nested organizations would not solve this re-organization problem. What you would normally want to do, is to change how resources are controlled, not change the name or identity of the repository. This might even be impossible or at least very challenging to do.

What I propose is something I call a "resource group". A resource group would be named collection of resources, such as action runners, package repos, storage, secrets, apps etc. The resources group would be "owned" by a user or team that are given admin permissions to the resource group, and woudld be allowed to change or reconfigure the attached resources. Read access can then be give to either users, teams or repositories. If a repository is given access to the resource group, this means that the users, teams or actors such as github actions, is given read access to the resources attached to the RG, much in the same way as they are able to access org level resources today, but that the resources have to be referenced through the RG name insted of being implicitly picked up from the organization. So for example, if you want to use a resource, like an action runner, it would be referenced like \<rg name>.\<runner label> or a secret like \<rg name>.secrets.\<secret name>. This is particularly useful for actions, it today is very difficult to use shared resources in workflows. With this concept it is also possible to make use of resources from more than one resource group in a repository and access control of those resources can be managed separately from the repository name.
