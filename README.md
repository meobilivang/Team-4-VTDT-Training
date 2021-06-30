# `Viettel Digital Talent` :two::zero::two::one: 

### Phase 1B: *Team Project*

---

<h1 style="text-align: center"> Project Proposal </h1>

## :bulb: Topic: *`Auto-scaling application using custom metrics on Kubernetes`*

### Team :four: - *with following members*:

**Mentor**: Pham Chien

**Mentees**:

- Julian P. Nguyen (Phong D. Nguyen)
- Luong D. Tran 
- Thang V. Tran

<h2 style="text-align: center">
 <g-emoji class="g-emoji" alias="date" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/1f4c5.png">📅</g-emoji>
 Expected Schedule
</h2>

**Week 1**: *Research & set up workspace*

**Goal**: Understand implemented concepts

- Collect & reading docs/articles
- Set up `Trello` workspace

**Week 2**: *Basic Implementation*

**Goal**: Bring acquired knowledge into actions. Able to configure & apply involved components at elementary level

- Basic install of components
- Perform simple demos to understand the workflow & configurations of components.

**Week 3**: *Enhanced Development*

**Goal**: Deployments of `Autoscaling` at elevated level, able to solve real-world use cases.

- Brainstorm which real-world problem to solve
- Simulate the specific use cases & perform labs.

**Week 4**: *Final Report & Presentation Slides*

**Goal**: Prepare for Seminar

- Finish & elaborate documentations
- Build Final Report & `Powerpoint` slides

<h2 style="text-align: center">
 <g-emoji class="g-emoji" alias="fire" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/1f525.png">🔥</g-emoji>
 General Objectives 
</h2>

1. Comprehend & analyze **to-implement & related** topics. 

2. Synthesize & aply acquired knowledge through different lab scenerios. 

3. Implement project management methodology & standardize workflow. 

<h2 style="text-align: center"> 
    <g-emoji class="g-emoji" alias="hammer_and_wrench" fallback-src="https://github.githubassets.com/images/icons/emoji/unicode/1f6e0.png">🛠️</g-emoji> 
    Covered Concepts 
</h2>

### General 

The project revolves around **`Kubernetes`** - *the Container Orchestration Application*. In [Week 4](https://github.com/vietstacker/Viettel-Digital-Talent-Program-2021/tree/main/Phase-1-Practices/Week-4) of training program, we discussed the basics of this platform. 

**Team 4** holds expectation to leverage what we already learned about **`Kubernetes`** with more advanced ideas & implementations. Besides the mentioned platform, other tools/ideas involve would be taken into consideration.

### :books: Knowledge Requirements

**Kubernetes**

- Understand some fundamental topics/operations of `Kubernetes`
- Simple workflow
- Able to use `Kubernetes`'s CLI - `kubectl`

**System Administration** 

- `Operating System` 
- `Networking`
- `Containerization` *(better to know some `Docker`)*

**Progamming**: *a bit of coding involves while performing labs. Moreover, we may need to be able to debug/understand (some parts) sourcecode of the integrated frameworks/libraries/add-ons*


### Deployment Required Components

As directed by our mentor, the hands-on of this project should contain below components: 

- **Kubernetes**: *installed Cluster should be integrated with these components*

<p align="center">
    <img src="./imgs/k8s-1.png">
</p>

- **Others**: `KEDA`, `Prometheus & Grafana`

<p align="center">
    <img src="./imgs/keda-icon.png" width="200">
    &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
    <img src="./imgs/prometheus-grafana.png" width="400">
</p>

#### :book: To-read Concepts

> Here is a suggested to-read list from our team. Further topics may arise during progression. 

#### :ferris_wheel: **Kubernetes**

**Basic**

- Revise Architecture Model
- Built-in Objects
- HELM
...

**Advanced**

- Custom Resource (CR) & CRD
- Kubernetes Operator
- **Horizontal Pod Autoscaler**
- Metrics Pipeline & Monitoring Pipelines
...

**Add-ons**

- `KEDA` - *Kubernetes Event-driven Autoscaling*

- **`Helm` charts**:
    - `kube-state-metrics`
    - `prometheus-mysql-exporter`
    - `prometheus-mongodb-exporter`
    - `kube-prometheus-stack`
...

#### :thermometer: **Observability & Monitoring**

**Prometheus**

- Understand following points:
    - Architecture
    - Features: `Service Discovery`, `Target`
    - (Metrics Scraping/Fetching) Workflow

- Perform query with `PromQL`.

**Grafana**

- Basic usage:
    - Connecting to `Prometheus`
    - Visualize metrics

#### **Additional**

**RabbitMQ**

**MySQL** 

**MongoDB**

### :bookmark_tabs: Project Management

#### Platforms/Tools

### GitHub Repository


#### Contributors:

- [**Julian P. Nguyen**](https://github.com/meobilivang)
- [**Luong D. Tran**](https://github.com/ducluongtrann)
- [**Thang V. Tran**](https://github.com/tranthang2404)