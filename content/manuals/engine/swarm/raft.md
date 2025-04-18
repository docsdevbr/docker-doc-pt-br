---
# Copyright (c) 2016 Docker, Inc.
# Docker and the Docker logo are trademarks or registered trademarks of Docker,
# Inc. in the United States and/or other countries.
# Docker, Inc. and other parties may also have trademark rights in other terms
# used herein.
#
# Documentation licensed under the Apache License, Version 2.0.
# The original work was translated from English into Brazilian Portuguese.
# https://github.com/docker/docs/blob/main/LICENSE

description: Raft consensus algorithm in swarm mode
keywords: docker, container, cluster, swarm, raft
title: Raft consensus in swarm mode
---
When Docker Engine runs in Swarm mode, manager nodes implement the
[Raft Consensus Algorithm](http://thesecretlivesofdata.com/raft/) to manage the global cluster state.

The reason why Swarm mode is using a consensus algorithm is to make sure that
all the manager nodes that are in charge of managing and scheduling tasks in the cluster
are storing the same consistent state.

Having the same consistent state across the cluster means that in case of a failure,
any Manager node can pick up the tasks and restore the services to a stable state.
For example, if the Leader Manager which is responsible for scheduling tasks in the
cluster dies unexpectedly, any other Manager can pick up the task of scheduling and
re-balance tasks to match the desired state.

Systems using consensus algorithms to replicate logs in a distributed systems
do require special care. They ensure that the cluster state stays consistent
in the presence of failures by requiring a majority of nodes to agree on values.

Raft tolerates up to `(N-1)/2` failures and requires a majority or quorum of
`(N/2)+1` members to agree on values proposed to the cluster. This means that in
a cluster of 5 Managers running Raft, if 3 nodes are unavailable, the system
cannot process any more requests to schedule additional tasks. The existing
tasks keep running but the scheduler cannot rebalance tasks to
cope with failures if the manager set is not healthy.

The implementation of the consensus algorithm in Swarm mode means it features
the properties inherent to distributed systems:

- Agreement on values in a fault tolerant system. (Refer to [FLP impossibility theorem](https://www.the-paper-trail.org/post/2008-08-13-a-brief-tour-of-flp-impossibility/)
 and the [Raft Consensus Algorithm paper](https://www.usenix.org/system/files/conference/atc14/atc14-paper-ongaro.pdf))
- Mutual exclusion through the leader election process
- Cluster membership management
- Globally consistent object sequencing and CAS (compare-and-swap) primitives
