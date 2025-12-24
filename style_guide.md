# Spectro Cloud Style Guide

Use the following style guide for all writing assignments.

## Summary 

- Prefer active voice and present tense  
- Address the reader directly  
- Use consistent headline and acronym styles  
- Write inclusively and precisely  
- Avoid unexplained jargon and idiomatic language  

Following these guidelines ensures Spectro Cloud documentation is clear, professional, and accessible to a broad technical audience.

## Voice
'Previous Voice and Tense sections contained errors, such as referrring to you as a noun and incorrect punctuation in Use, we, when. Also, awkward phrasing, such as avoid hidiing using it is recommended, are unclear and examples of bad grammar.'

Use the **active voice** whenever possible. Active voice is more direct, easier to read, and usually shorter than passive constructions.

Address the reader directly when writing instructional content. Use the pronoun *you*.

Use *we* when providing recommendations or guidance. This approach takes ownership of the guidance and avoids vague or impersonal constructions such as “it is recommended.”

**Good ✅** | **Bad ❌**
---|---
Use the `kubectl` CLI to create a namespace named `mgmt`. | The `kubectl` CLI can be used to create namespaces named `mgmt`.
Before upgrading, review the release notes for deprecation notices. | Release notes should be carefully verified for deprecation notices prior to an upgrade.
We recommend you deploy Palette Enterprise in a highly available configuration of at least three nodes. | It is recommended to deploy Palette Enterprise in a highly available configuration of at least three nodes.

## Tense

Use the **present tense** whenever possible.

Users read documentation while performing tasks or gathering information. Because these actions occur in the user’s present, present tense is clearer and easier to understand than past or future tense.

Use past or future tense only when describing historical events or delayed behavior.

**Good ✅** | **Bad ❌**
---|---
The command drains the node and evicts running pods. | The command will drain the node and will evict running pods.
The controller retries after 30 seconds. | The controller will retry after 30 seconds.

## Headline Style
'The previous version has a grammatical mistake in the mention of nouns starting with an -ing and gerunds. Gerunds are not nouns and gerunds themselves are not wrong to use, as there may be some exceptions such as Observability and Monitoring that may require its use. The previous examples also introduced ambiguity, such as in Quick Start, where the noun phrase Quick Start is a special case rather than a pattern for a conceptual topic.'

Use **title case** for headings.

For **task-based headings**, start with an imperative verb. Avoid gerund forms (*-ing*) for task titles.

For **conceptual or reference headings**, start with a noun or noun phrase.

**Good ✅** | **Bad ❌**
---|---
Deploy a Pack Registry Server | Deploying a Pack Registry Server
Access Audit Logs | Accessing Audit Logs
Pack Registry Server Architecture | Architecting the Pack Registry Server
Get Started with Palette App Mode | Quick start with Palette app mode

---

## Acronyms

'The previous description of when to use acronyms was not enitrely accurate. The examples indicated camel case, but were actually mixed case, not camel case. There was some confusion between what an acronym is and how they should be written.'

Define acronyms on first use by spelling out the term followed by the acronym in parentheses. Use the acronym consistently after it is defined.

If an acronym appears only once, spell out the term and do not introduce the acronym.

Some acronyms use mixed case by convention (for example, *IaaS*, *SaaS*). Preserve the standard casing.

If both the spelled-out term and acronym are required for metadata, it is acceptable to use both.

**Good ✅** | **Bad ❌**
---|---
Boot the Virtual Machine (VM). | Boot the virtual machine (VM).
Boot all the Virtual Machines (VMs). | Boot all the virtual machine (VMs).
This is called Infrastructure as a Service (IaaS). | This is called infrastructure as a service (IaaS).
Dynamic-Link Library (DLL). | dynamic-link library (DLL).

---

## Gender
'The previous description on gender-neutral pronouns was not accurate in its descriptions, since him/hehis/she/her are not nouns, but rather pronouns.' 

Use **gender-neutral language**.

When referring to a person whose gender is unknown or irrelevant, avoid gendered pronouns such as *he*, *him*, *his*, *she*, or *her*. Do not use paired constructions such as *he/she*.

Use the singular *they* instead.

**Good ✅** | **Bad ❌**
---|---
If a user forgets their password, they can reset it from the login page. | If a user forgets his or her password, he/she can reset it from the login page.
When an administrator updates the cluster, they should review the release notes. | When an administrator updates the cluster, he should review the release notes.

---

## Inclusive Language

'The previous examples of ableism were not accurate. Using verbs like run and jump are not examples of ableist language. Ableism is defined by using a disability or medical condition intended to be insulting.'

Avoid language that uses disability or medical conditions as metaphors or insults. Such language can reinforce bias and cause harm.

Examples of ableist language include terms such as *crazy*, *insane*, *cripple*, *dumb*, and phrases like *blind to* or *turn a blind eye*.

Choose neutral alternatives that describe behavior or state without referencing disability.

**Good ✅** | **Bad ❌**
---|---
Unexpected behavior occurs when the configuration is invalid. | The configuration is crazy.
The feature is unavailable in this release. | The feature is crippled in this release.

---

## Terminology and Clarity
'This replaces the section on Simplified English. There were several grammatical errors in the previous section where the examples focused on replacing words without the intended effect on clarity.'

Prefer precise, literal language over idiomatic expressions. Clear wording improves accessibility for global audiences and reduces ambiguity.

**Good ✅** | **Bad ❌**
---|---
Go to the Settings tab. | Jump to the Settings tab.
Issue the command `kubectl get pods`. | Run the command `kubectl get pods`.

## Kubernetes-Specific Terminology

When using Kubernetes-specific terms, use the canonical terminology. Introduce specialized terms with a brief explanation on first use when appropriate.

**Example:**

> Drain the node (evict all running pods and prevent new scheduling) before performing a version upgrade.

### Command Output

Show the command output to help the reader follow along and validate they are receiving the expected output.



```shell
kind create cluster
```


```shell
Creating cluster "kind" ...
 ✓ Ensuring node image (kindest/node:v1.25.3) 🖼
 ✓ Preparing nodes 📦
 ✓ Writing configuration 📜
 ✓ Starting control-plane 🕹️
 ✓ Installing CNI 🔌
 ✓ Installing StorageClass 💾
Set kubectl context to "kind-kind"
You can now use your cluster with:

kubectl cluster-info --context kind-kind

Have a nice day! 👋
```