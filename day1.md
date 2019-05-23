## Kubecon Day one
### Keynotes
Why kubernetes survived:
- works well
- vendor neutral open source
- people

2.66 million contributions to cncf projects
56k contributers

### Byran Liles Senior staff VMware  CNCF oroject updates
#### Staging projects
- OpenEBS enables container attached storage using kubernetes for the substrate of storage management

#### Incubating
- linkerd: zero config mTLS, traffic shifting
- HELM: client side only, push charts to OCI REGISTRY, RELEASE NAMES SCOPED TO NAMESPACE
    - declare dependencies in Chart.yaml
    - HELM 3 alpha available
    - validate chart values
- Harbor: 1.8 released with support for OIDC, robot accounts and Replicatiib enhancements
- Rook: 1.0 release, csi support and new features in many of the operators
- cri-o 
- OpenCensus and OpenTracing: 
    - observability is how well you understand a system given only the telemetry data that escapes
    - telemtry must become a build in feature
    - OpenCensus and Opentracing are merging into OpenTelemetry
    - Single set of APIs, implementations and agents
    - Backwards compatable using software bridges
#### Graduated
- fluentd: 1.5 release today
    - Forward protocol and keepalibe featyre
    - TLS extenedd to http and syslog
    - improved flexibility on multiple works
    - fluentd training available


### Vijoy Cisco
-  Network service Mesh solves L2/L3 problems for kubernetes
- per pod and workload routing
- multi cloud routing
- 

### Getting started on contributing to kubernetes
- 

## Ingress v2 and Multicluster Services - Google
- Challenges; portability, expressiveness features
- INGRESS GA adds a IngressClass object
- another model is IngressRoute is an api model that is recursive, allows you to chain multipl together
- Portability should be a user choice
- Syntax changes to support future API growth

Model:
old
- Infrastructure -> router -> backends
new
 gatewayclass -> gateway -> virtual host -> service
- Gateway Class allows you to specify deployment specific options (mergable_
- Gateway represents an actual LB or proxy, you would specify proxy config , ssl temrination etc here
- Virtual host has a match action model
- VirtualHost extensibility may require a decorator pattern (community to drive this)
- Portabilty: expanding ring of support
- core -> extended API (feature by feature extendable) -> custom (no guarantee for portability and no k8s API schema)
example usage
- Core API might have existing ingress and trafic splitting
- extended might have regex or rewrite
- unique implementation would be in customer

Future directions
- multicluster services
- cloud storage buckets

Multicluster
- be able to add and remove clusters based on load balancing requirements
- picture attached
- no multicluster deployments as they aren't trying to create an opininated way of deploying deployments across clusters
- Federation v2 is far more opinionated (makes assumptions on cross-cluster dns and SD, deployment of workloads etc.)


## Unit testing your k8s configuration using OPA - Snyk
- shift-left testing
- using conftest which uses Rego as a programming language
- portability between different k8s solutions
- Shift left testing is an approach to softwaretesting where testing is run earliet in the lifecycle
- conftest is targeting local and CI testing for kubernetes (available on github)
- conftest test <yaml> 
- warn, deny, etc.
- built in testing on opa to confirm policirs sare correctly written
- conftest will be enabled on container registry and use of conftest push and pull will allow for sharing
- 

## gRPC Microservices Authentication and Security - Google
- gRPC makes insecure options an explicit option in the API (easy to tell if it was set)
- connect level security: use secure channels
- request headers is initial metadata
- per RPC based: tokens in metadata, needs underlying secure transport
- channel level: TLS, mTLS, ALTS
- Transparent: trusted proxt rhar does encryption/auth for you
- Tokens can be sent in the initial request metadata
- sending a token with each RPC is not usually an efficiency problem: tokens are reused and HPACK header compression can be used
- 

## Istio Multi-cluster Service Mesh Patterns IBM
-  single entwork single control plane
    - remotes have smaller istio (less istio compoents)
    - internal CIDRs
    - share remote clister config
    - service defined everywhere
    - changing istio service endpoints

- single control plane seperate networks
     - remotes have smaller istio
     - seperate internal CIDRs
     - service dfined everywhere
     - gateway routing
     - split horizon EDS (configures routes based on who is calling it)
     - SNI routing
     - changing Istio gateway IPs

    Multiple COntrol planes
        - serviceEntry for remote services
        - coreDNS for rsolving ,global

## Multicluster Tool Box - admiralty
- mssing cross-cluster control loops
- cross cluster garbage collection
- declarative bootstrapping
- admirality has some source code
- modifying the sample controller to create a new multicluster workspace
- three modes of deletion: orphan dependents, cascading deletion: background, forground

## Keynotes
- Service Mesh Interface will allow service meshes to be easily switched out
- supports traffic splitting, traffic metrics, policies
- 
- 






