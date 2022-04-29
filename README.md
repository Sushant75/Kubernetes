# Kubernetes

<p>
Kubernetes is a portable, extensible, open source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation. It has a large, rapidly growing ecosystem.</p>
<br>

## Kubernetes Components Overview

<p>Kubernetes has several core components that make the wheels of the machine turn. They are as follows:</p>
<br>
<ul>
<li>API server</li>
<li>etcd</li>
<li>Controller manager</li>
<li>Scheduler</li>
<li>Kubelet</li>
</ul>
<br>

## Etcd

<p>Kubernetes uses etcd as the backend key-value database to persist the API objects during the life cycle of a Kubernetes cluster. It is important to note that nothing (internal cluster resources or external clients) is allowed to talk to etcd without going through the API server. Any updates to or requests from etcd are made only via calls to the API server.</p>
<br>

## API Server

<p>The API server allows standard APIs to access Kubernetes API objects. It is the only component that talks to backend storage (etcd).
Additionally, by leveraging the fact that it is the single point of contact for communicating to etcd, it provides a convenient interface for clients to "watch" any API objects that they may be interested in. Once the API object has been created, updated, or deleted, the client that is "watching" will get instant notifications so they can act upon those changes. The "watching" client is also known as the "controller", which has become a very popular entity that's used in both built-in Kubernetes objects and Kubernetes extensions.
</p>
<br>

## Scheduler

<p>The scheduler is responsible for distributing the incoming workloads to the most suitable node. The decision regarding distribution is made by the scheduler's understanding of the whole cluster, as well as a series of scheduling algorithms.</p>
<br>

## Controller Manager

<p>The controller manager acts as a typical subscriber and watches the only API objects that it is interested in, and then attempts to make appropriate changes to move the current state toward the desired state described in the object.
For example, if it gets an update from the API server saying that an application claims two replicas, but right now there is only one living in the cluster, it will create the second one to make the application adhere to its desired replica number. The reconciliation process keeps running across the controller manager's life cycle to ensure that all applications stay in their expected state.
</p>
<br>

## Kubelet
<p>The kubelet is deployed on each worker machine. The kubelet primarily aims at talking to the underlying container runtime (for example, Docker, containerd, or cri-o) to bring up the containers and ensure that the containers are running as expected. Also, it's responsible for sending the status update back to the API server.</p>