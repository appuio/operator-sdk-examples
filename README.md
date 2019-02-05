# Operator-sdk-examples

1) Context:
Kubernetes has become an omnipresent platform to host cloud-native applications. As a rather low-level platform, it is often made developer-friendly by wrapping it into higher-level platforms, such as OpenShift (OKD), and by turning it into a managed service platform, such as APPUiO, which can be deployed to any cloud infrastructure. Application engineers interact with Kubernetes mostly by authoring appropriate deployment descriptors and by pushing their code which triggers deployments. Due to ongoing feature additions, not so much is known about useful combinations of annotations on Kubernetes deployments (and other declaratively described objects), Kubernetes operators (a kind of hooks) and custom resources definitions. In this blog post, we share some of the experience we have gained while researching how to trigger actions upon certain updates to the descriptors, as a precursor to dynamic and autonomous feedback loops which can self-manage application deployments.
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

#2) Operators, Operator Framework, and Operators SDK:
Operators  are Kubernetes native applications that facilitate the management of complex stateful applications on top of Kubernetes. The main practical and development problem is that writing an operator can be very difficult because of challenges such as using (i) low level APIs and (ii) a lack of modularity which leads to duplication, inconsistencies, and unexpected behaviors.
The Operator Framework is an open source toolkit to manage Operators, in an effective, automated, and scalable way, which is composed by several low-level APIs.The Operator-SDK is a toolkit, built on top of the Operator Framework, that provides the tools to build, test and package Operators. Initially, the SDK facilitated the marriage of an application’s business logic (for example, how to scale, upgrade, or backup) with the Kubernetes API to execute those operations. Over time, the SDK can allow engineers to make applications smarter and have the user experience of cloud services. Leading practices and code patterns that are shared across Operators are included in the SDK to help prevent reinventing the wheel.

#2-a) Operators SDK
From a developer perspective, the entry point is the Operator SDK, originating from CoreOS, which is offered as part of the Operator Framework that is, according to its self-description, "an open source toolkit to manage Kubernetes native applications, called Operators, in an effective, automated, and scalable way". The SDK specifically targets Go developers. Support for other programming languages (E.G., Java, C, etc.) is currently lacking, but an ongoing direction.
The Operator SDK is a framework that uses the controller-runtime library to make writing operators easier by providing:
High level APIs and abstractions to write the operational logic more intuitively
Tools for scaffolding and code generation to bootstrap a new project fast
Extensions to cover common operator use cases
The Operator SDK

#2-b)Operators SDK Versions (Old v.s. Recent one)
The Operator SDK is a toolkit that is continuing evolving over the time (e.g., its code,  structure, and logic is changing).
In particular, as reported in the main Github page of the operator SDK, the libraries and tools are labeled with "Project Status: pre-alpha", thus and "are expected breaking changes to the API in the upcoming releases".
The project started almost 7 months ago and we started monitoring it intensively from October 2018.
     
# 2-c) Supported Operator SDK Workflows

The SDK provides workflows to develop operators in Go, Ansible, or Helm.

--------------------

The following workflow is for a new Go operator:

Create a new operator project using the SDK Command Line Interface(CLI)

Define new resource APIs by adding Custom Resource Definitions(CRD)

Define Controllers to watch and reconcile resources

Write the reconciling logic for your Controller using the SDK and controller-runtime APIs

Use the SDK CLI to build and generate the operator deployment manifests

--------------------

The following workflow is for a new Ansible operator:

Create a new operator project using the SDK Command Line Interface(CLI)

Write the reconciling logic for your object using ansible playbooks and roles

Use the SDK CLI to build and generate the operator deployment manifests

Optionally add additional CRD's using the SDK CLI and repeat steps 2 and 3

--------------------

The following workflow is for a new Helm operator:

Create a new operator project using the SDK Command Line Interface(CLI)

Create a new (or add your existing) Helm chart for use by the operator's reconciling logic

Use the SDK CLI to build and generate the operator deployment manifests

Optionally add additional CRD's using the SDK CLI and repeat steps 2 and 3





