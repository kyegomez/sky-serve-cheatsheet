# sky-serve-cheatsheet
A simple Cheat Sheet for Sky Serve!

```markdown
| Command                                         | Description                                               |
|-------------------------------------------------|-----------------------------------------------------------|
| `sky serve status <service-name> [--endpoint]`  | Show detailed info about the service.                     |
| `sky serve down <service-name>`                 | Teardown the specified service.                           |
| `sky serve logs <service-name> [REPLICA_ID]`    | Show logs for a specific replica of the service.          |
| `sky serve logs --load-balancer <service-name>` | Show logs for the load balancer of the service.           |
| `sky serve logs --controller <service-name>`    | Show logs for the controller of the service.              |
| `watch -n10 sky serve status <service-name>`    | Monitor the status of the service, updating every 10 sec. |
| `curl -L <endpoint URL>`                        | Send a test request to the service's endpoint.            |
| `sky serve up`                                  | Launch a SkyServe service.                                |
| `sky serve update`                              | Update a SkyServe service.                                |
| `sky serve status`                              | Show statuses of SkyServe services.                       |
| `sky serve down`                                | Teardown service(s).                                      |
| `sky serve logs`                                | Tail the log of a service.                                |
```
