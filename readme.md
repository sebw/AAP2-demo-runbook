# Ansible Automation Platform [demo runbook]

## Enterprise Directory integration

UC: organisation has a central LDAP and want to give access to the platform for groups of users

Business value: the profile of the person automatically defines what access she has in AAP. Access is granted or revoked based on live interactions with the directory.

## Central logging

UC: AAP produces system and job logs and provides a basic dashboard. The events can be centralized in a logging aggregator for more advanced dashboards and alerting.

BV: integration with logging aggregator, allowing for better observability of the automation platform.

![Alt text](image.png)

![Alt text](image-1.png)


## Template launch

Use case: start a simple automation playbook

Business Value: instead of manual actions, recurring tasks are now automated in a controlled manner.

![image](https://github.com/sebw/AAP2-demo-runbook/assets/2285094/e8cb337f-076d-496e-8573-0e1cd3e9db10)


## Workflow launch

UC: we can tie multiple playbooks together (sometimes owned and maintained by different teams) in a single workflow. We can also integrate workflows inside workflows. Workflows can be made of playbooks but also approval, inventory sync or project sync.

BV: Teams collaborate together to build advanced automation.

![image](https://github.com/sebw/AAP2-demo-runbook/assets/2285094/3e4698db-8a5d-4189-bd1c-b1b4e28eb093)


## RBAC

UC: We want to apply a least privileges approach to who can run what.

BV: Risk reduction.

## Dynamic Inventories

UC: instead of managing inventories manually, an operator that is highly error prone, we configure AAP to retrieve the nodes to manage from an source of thruth inventory.

BV: We reduce the risk of running automation on the wrong machines.

## Smart Inventories

UC: we can group machines from multiple inventories in single "smart inventories" based on the properties of the machines (properties called "facts"). The smart inventories can be used for ad hoc automation tasks such as upgrades.

BV: Grouping machines together in inventories and RBAC allow to delegate automation to specific teams (e.g. allow the projectX team to run automation on the development environment of the projectX).

## Constructed inventories

UC: we can group machines from multiple inventories based on variables.

BV: same as smart inventories

https://www.ansible.com/blog/how-to-use-the-new-constructed-inventory-feature-in-aap-2.4

## API endpoints

UC: the Ansible Automation Platform can be integrated with third party tools, such as ITSM platforms (ServiceNow, Jira, etc.), CI/CD tools and others. Users do not have to learn the AAP web interface as the existing tooling of the organization can pilot AAP.

BV: integration with existing tools prevents reinventing the wheel, reduce knowledge gap and provides an even better ROI for such existing tools

## Start a workflow from ServiceNow

UC: a user order a service that is fullfiled automatically

BV: automation supports standardization, delivers services to customers faster, allowing for better SLA, less incidents, less customization and less manual/error prone work.

## Job with survey

UC: surveys allow automation engineers to create forms that can be delegated to users.

BV: when the organization doesn't have an ITSM platform, AAP can be used to create forms.

## Advanced schedules

UC: an external team (e.g.: ITSM) needs to schedule jobs in AAP, recurring or one off. We give them the opportunity to do so by using a job template with a simple survey. They can also make API calls or use the Ansible Controller collection. The appropriate workflow starts when requested and part of the workflow deletes the schedule when done.

BV: AAP can become the scheduler for everything, with possibilities to create advanced schedules (recurring with exceptions, highly dynamic, on demand).

## Integration with external vault

UC: instead of storing secrets in AAP, secrets can be managed in external vaults. External vaults can rotate passwords on a regular basis and AAP doesn't need to know when that happens. Anytime an automation runs, AAP will ask the external vault what is the password at runtime.

BV: risk mitigation and compliance

## RBAC Monitoring Level 1: restart service

UC: a monitoring team level 1 doesn't know how to restart a service from the command line. An automation team can create a job template with predefined information allowing a monitoring team to follow a simple procedure and contribute to the system engineering teams

BV: monitoring teams can help solving incidents

## RBAC Monitoring Level 2: restart server

UC: if the monitoring level 1 can't resolve a problem, the L2 team can restart the server fully.

BV: multiple level of monitoring allow for delegation in resolving incidents.

## Ansible development workflow with Gitlab

UC: automation engineers want to write Ansible codes in an efficient way and quickly see the results of their changes in a "fail fast, improve faster" approach. By leveraging Gitlab and webhooks with AAP, developers can create a very efficient development workflow.

BV: faster time to automation. New code can be tested by more engineers, taking advantage of practices such as 4 eyes principle. New code is tested and validated, increasting its reliability and achieving faster time to market.

## Automate your AAP

UC: the automation platform can be automated using infrastructure as code practices. In case of disaster, the platform can be rebuilt from scratch

BV: shorter MTTR

https://github.com/sebw/Automate-AAP2

## Soft delete

UC: AAP subscription model is based on the number of nodes it manages. When a machine is deleted or no longer automated, it can be removed from an inventory and a soft delete reclaims the subscription it used to use

BV: fair and optimized cost 

![Alt text](image-2.png)

https://www.ansible.com/blog/subscription-and-host-metric-changes-in-ansible-automation-platform-2.4



BV: easy governance around who can connect to the platform. Combined with the powerful and fine grained RBAC, this allows for proper governance around your automation. 
