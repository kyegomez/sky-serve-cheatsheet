# sky-serve-cheatsheet
A simple Cheat Sheet for Sky Serve!

```markdown
| Command                      | Description                                                  | Example                                                |
|------------------------------|--------------------------------------------------------------|--------------------------------------------------------|
| `sky serve status`           | Show statuses of SkyServe services.                          | `sky serve status sky-service-d178`                    |
| `sky serve down`             | Teardown service(s).                                         | `sky serve down sky-service-d178`                      |
| `sky serve logs`             | Tail the log of a service.                                   | `sky serve logs sky-service-d178 [REPLICA_ID]`         |
| `sky serve logs --load-balancer` | Tail the logs of the load balancer for a service.         | `sky serve logs --load-balancer sky-service-d178`      |
| `sky serve logs --controller`| Tail the logs of the controller for a service.               | `sky serve logs --controller sky-service-d178`         |
| `watch -n10 sky serve status`| Monitor replica status with an update every 10 seconds.      | `watch -n10 sky serve status sky-service-d178`         |
| `curl -L`                    | Send a test request to the service endpoint.                 | `curl -L 44.203.140.214:30001`                         |
| `sky serve up`               | Launch a SkyServe service.                                   | `sky serve up [SERVICE_CONFIG]`                        |
| `sky serve update`           | Update a SkyServe service.                                   | `sky serve update sky-service-d178 [NEW_CONFIG]`       |
```
