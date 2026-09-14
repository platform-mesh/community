# IPCEI-CIS Hackathon @ SAP Innovation Center Potsdam

In July 2026, the Platform Mesh team joined a hackathon at the SAP Innovation Center in Potsdam,
collaborating with contributors from the [NeoNephos Foundation](https://neonephos.org) and
[ApeiroRA](https://apeirora.eu) as part of the broader [IPCEI-CIS](https://ipcei-cis.eu) initiative
to develop open-source European cloud and AI infrastructure.

We worked on three tracks: expanding Platform Mesh's access control model with group-based and
just-in-time permissions, designing a standardised IaaS API layer for provider-agnostic workload
migration, and investigating what it would take to decouple Platform Mesh from its built-in Keycloak
dependency.

## ReBAC and Expanding the Role Access Model

Platform Mesh's current access model ties permissions directly to individual identities — adequate for
simple setups, but not for production environments handling sensitive workloads or operating at
organisational scale.

We prototyped the following:

**Group and Role-Centric Access**: In public sector and defence contexts, access must span teams,
contractors, and partner institutions across borders. Binding permissions to individuals creates overhead
and risk. Our prototype moves to group- and role-centric permissions, which is how most organisations
actually manage access.

**Just-in-Time / Just-Enough Access (JIT/JEA)**: Standing privileged access is one of the most common
attack vectors in cloud infrastructure. The prototype introduces time-bound privilege elevation — access
is granted on demand, expires automatically, and leaves an audit trail.

[View repository →](https://github.com/platform-mesh/hackathon-cascading-rbac-operator)

## Standardised IaaS APIs

Without standardised IaaS APIs, Platform Mesh inherits the lock-in of whatever cloud provider it runs
on — a real problem for public sector workloads where portability and sovereignty matter.

We designed a standardised IaaS API layer for Platform Mesh and built a proof of concept covering two
scenarios: rapid workload migration when a provider becomes unavailable, and cross-border operations
where EU institutions need to move between sovereign cloud environments without rewriting integrations.

[View repository →](https://github.com/platform-mesh)

[Demo video →](https://www.youtube.com/watch?v=ZKNeE781jLI)

## IdP Streamlining

Platform Mesh ships with Keycloak as a tightly coupled identity provider. That works for greenfield
deployments but becomes a problem where an IdP already exists.

We started investigating what it would take to decouple the IdP layer. Short answer: harder than
expected. The work exposed significant architectural dependencies, and a larger refactoring effort will
be needed to move this forward.

[View repository →](https://github.com/platform-mesh/platform-mesh/tree/idp-streamlining)
