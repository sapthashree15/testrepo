
<div align="center">

## Introduction to Containers, Kubernetes, and OpenShift
### Module 4 Glossary: The Kubernetes Ecosystem
</div>


<table>
<tr>
<th width="20%">Term</th>  <th>Definition</th>
</tr>

<tr>
<td width="20%"valign="top">Build</td>
<td width="20%">

<code>The process of transforming inputs into a resultant object.</code>
<td width="20%">
</tr>


<tr>
<td width="20%"valign="top">BuildConfig</td>
<td width="20%">
<code>An OpenShift-specific object that defines the process 
for a build to follow. The BuildConfig is the
blueprint, and the build is an instance of that
blueprint put into action.</code>
</td>

</tr>

<tr>
<td width="20%"valign="top">Configuration Change</td>
<td width="20%">
<code>A trigger that causes a new build to run when a new 
BuildConfig resource is created.
</code>
</td>
</tr>

<tr>
<td width="20%"valign="top">CRDs </td>
<td width="20%">
<code>“Custom Resource Definitions” in addition to built-in 
resources like Deployments and Pods. Additional 
resources can be created to extend the Kubernetes API. 
CRDs are new endpoints in the Kubernetes API that store 
a collection of API objects.
</code>
</td>
</tr>

<tr>
<td width="20%"valign="top">Image Change</td>
<td width="20%">
<code>A trigger to build when a new version of an image when 
it is available. For example, if an application is 
built using a Node.js base image, that image will
be updated as security fixes are released and other 
updates occur. When base images are updated so that the 
code always contains the latest security fixes, the 
image change trigger automates a build to rebuild 
containerized applications. 
</code>
</td>
</tr>

<tr>
<td width="20%"valign="top">ImageStream</td>
<td width="20%">
<code>An abstraction for referencing images within OpenShift.
Each image contains an ID, or digest, that identifies 
it. ImageStreams do not contain image data but rather
are pointers to image digests.
</code>
</td>
</tr>

<tr>
<td width="20%"valign="top">Istio</td>
<td width="20%">
<code>A commonly used service mesh. Istio secures services 
through authentication, authorization, and encryption.
Istio provides control by defining policies that can be 
enforced across an entire fleet. With Istio, you can 
observe traffic flow in your mesh so you can trace call 
flows,dependencies, and you can view metrics such as 
latency and errors.
</code>
</td>
</tr>

<tr>
<td width="20%"valign="top">OpenShift </td>
<td width="20%">
<code>A hybrid cloud, enterprise Kubernetes application
platform.
</code>
</td>
</tr>

<tr>
<td width="20%" valign="top">Operator Pattern</td>
<td width="20%">
<code>Combining custom resources and custom controllers that
give a declarative API like Pods possess.
</code>
</td>
</tr>

<tr>
<td width="20%" valign="top">Operators</td>
<td width="20%">
<code>Powerful patterns used within Kubernetes to automate 
many tasks within a cluster. OpenShift provides a way 
to easily install and use them. A way to package, 
deploy, and manage a Kubernetes native applications
is an application that is deployed on and managed by 
Kubernetes.
</code>
</td>
</tr>

<tr>
<td width="20%" valign="top">Service Mesh</td>
<td width="20%">
<code>A dedicated layer for making service-to-service 
communication secure and reliable. It provides traffic 
management to control the flow of traffic between 
services, security to encrypt traffic between services, 
and observability of service behavior; so, you can 
troubleshoot and optimize applications.
</code>
</td>
</tr>
<tr>
<td width="20%" valign="top">Source-to-Image</td>
<td width="20%">
<code>A tool for building reproducible container
images. Also abbreviated S2i, it injects application 
source code into a container image to produce a ready-to-run image.
</code>
</td>
</tr>

<tr>
<td width="20%" valign="top">Webhook</td>
<td width="20%">
<code>A trigger that sends a request to an OpenShift 
Container Platform API endpoint. Often this will be a 
GitHub webhook, though it can also be a generic 
webhook. If a GitHub webhook is utilized, GitHub can 
send the request to OpenShift when there is a new 
commit on a certain branch, when a pull request is 
merged, as well as under many more circumstances.
Webhooks are a great way to automate development flows 
so that builds can occur automatically as new code is 
developed
</code>
</td>
</tr>
</table>


