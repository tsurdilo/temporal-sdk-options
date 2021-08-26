## Go SDK Options

### SessionOptions

* Options used to specify metadata for a session

| Option | Description | Type |
| --- | --- | --- |
| ExecutionTimeout | Specifies the maximum amount of time the session can run | time.Duration |
| CreationTimeout | Specifies how long session creation can take before returning an error | time.Duration |
| HeartbeatTimeout | Specifies the heartbeat timeout | time.Duration |

### RegisterActivityOptions

* Options for registering an activity

| Option | Description | Type |
| --- | --- | --- |
| Name | Sets the activity name (if other than function name needs to be set) | string |
| DisableAlreadyRegisteredCheck | Sets if already registered check should be disabled | bool |
| SkipInvalidStructFunctions | Sets to panic or skip when registering struct with activities and are not valid | bool |

### ClientOptions

* Options for client creation

| Option | Description | Type |
| --- | --- | --- |
| HostPort | Set the host:port for this client to connect to | string |
| Namespace | Set the namespace name for this client to work with | string |
| Logger | Sets the logger framework | log.Logger |
| MetricsScope | Sets the metric scope, which metrics should be reported | tally.Scope |
| Identity | Sets an identify that can be used to track this host for debugging | string |
| DataConverter | Sets DataConverter to customize serialization/deserialization of arguments in Temporal | converter.DataConverter |
| Tracer | Sets opentracing Tracer that is to be used to emit tracing information | opentracing.Tracer |
| ContextPropagators | Sets ContextPropagators that allows users to control the context information passed through a workflow | []ContextPropagator |
| ConnectionOptions | Sets options for server connection that allow users to control features of connections such as TLS settings | ConnectionOptions |
| HeadersProvider | Sets custom request headers | HeadersProvider |
| TrafficController | Set to induce artificial failures in test scenarios | TrafficController |

### ConnectionOptions

* Options to control optional connection params

| Option | Description | Type |
| --- | --- | --- |
| TLS | Configures connection level security credentials | tls.Config |
| Authority | Set the value to be used as the :authority pseudo-header | string |
| DisableHealthCheck | Disable health check | bool |
| HealthCheckAttemptTimeout | Specify how to long to wait for service response on each health check attempt | time.Duration |
| HealthCheckTimeout | Set the default health check timeout | time.Duration |
| EnableKeepAliveCheck | Set enable keep alive check | bool |
| KeepAliveTime | Set the keep alive time | time.Duration |
| KeepAliveTimeout | Set the keep alive timeout | time.Duration |
| KeepAlivePermitWithoutStream | Set if client sends keepalive pings even with no active RPCs | bool |

### StartWorkflowOptions

### WorkflowOptions

### ExecuteActivityOptions

### ExecuteLocalActivityOptions

### WorkerOptions

### ActivityOptions

### LocalActivityOptions

### ChildWorkflowOptions

### RegisterWorkflowOptions

