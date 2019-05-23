## Keynotes
- theme: kubernetes is a platform of platforms
- Spotify, how spotify accidently deleted all their k8s clusters with ni user impact
    - spotify uses GCP
    - 3 production clusters
    - toke 3.25 hours to restore a cluster due to bugs in the creation scripts
    - creation process wasn't resumable
    - terraform state files were overwritten during a merge, killed an entire cluster
- - IBM Lessons learned deploying 10k kube clusters
    - running tooling where developers work
    - most tools are run on slack via chat bots etc (chatOps)
    - pull based self updating clusters
- Google, WOrking with storage in k8s
    - use CSI with block/file storage
    - 

## M3 and Prometheus, uBer
- m3 scales monitoring horizontally
- distributed time series database, compatible with prometheus as remote storage
- focus on simple operability and scales to billions of metrics
- stores metrics for weeks, months or years.
- store metrics at different retention based on mapping rules
- scale by just adding nodes
- m3 co-oridinator attached to m3dbs
- hook up graphana, etc to the co-ordinator
- m3 is multi-region: zero cross-region traffic
- index backed by FST segments
- github.com/m3db/bench_multiregion

## Migration to gRPC, Spotify
- put all proto files in one repo
- prototool (uber) can help manage your t=proto files
- version on the proto package
- create new proto packages on breaking changes
- rety hedging proposal to grpc standard library (fan out requests to all backends, fastest backend replies, cancel remaining requests), speeds up tail latency
-  retry throttling and pushback in same proposal
- lookaside loadbalancing option: like client side load balancing but a seperate side loadbalancer to do some of the control plan management,
- (could be a proxyless rpc mesh using this) 


