---------------Elastic Runtime Architecture
--Elastic Runtime Subsystems
  - Diego
  - Loggregator
  - Cloud Controller API
  - Routing

-- Key Sequence FLows thought the ER

- Diego: Schedules task and Long-runtime Processes (LRPs).
- Diego: Is gurantedd to run at most once e.g: stage an application.
- LRPs can have multiple instances.
- Diego: Container: An application instances is run within an immutable Container.
- Diego: Cell: Container are run within a cell.
- Diego: Represents the cell in the BBS(bulleten board system)/auctions.
- Diego: Auction: is held to bid on executing a task or an LRP
- Diego: Executor: Manages container allocations on the cell.
- Diego: Metron: Forwards logs to the Loggregator subsystem.
- Diego: BBS(Bulletin Board System) is the API to access the Diego database for tasks and LRPS.
- Diego: Brain: is composed of two components.

- Loggregator: Forwards logs to the Loggregator subsystem.
- Loggregator: Droppler: Gathers logs from Metron.
- Loggregator: Firehose: websocket endpoints that exposes app logs, container metrics and ER components metrics.
- Loggregator: Nozzles: Consume the firehouse output.

- Cloud Controller API: exposes an API for using and managing the Elastoc Runtime.
- Cloud Controller API: Cloud Controller Database: persists Org/Space/App data in the Cloud Controller Database.
- Cloud Controller API: Blob Store: Cloud Controller persists app packages and droplets to the blob store.
- Cloud Controller API: CC-Bridge: translates app specific messages into the generic language of tasks and LRPs. Cloud Controller Bridge

- Router: routes traffic to appropriate component.

Stage and Run Request Flow:

Cloud controller passes requests to run and stage applications to the CC-Bridge.
CC-Bridge translates stage and run requests into tasks and LRPs.
BBS submits tasks and LRPs to the Auctioneer (Brain).
Auctioneer assigns the task or LRP to a cell.The Executor creates a Garden container in the cell. The Task or LRP runs in the container.







