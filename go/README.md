## Go SDK Options

- [SessionOptions](#sessionoptions)
- [RegisterActivityOptions](#registeractivityoptions)
- [ClientOptions](#clientoptions)
- [ConnectionOptions](#connectionoptions)
- [StartWorkflowOptions](#startworkflowoptions)
- [ActivityOptions](#activityoptions)
- [ExecuteLocalActivityOptions](#executelocalactivityoptions)
- [WorkerOptions](#workeroptions)
- [ChildWorkflowOptions](#childworkflowoptions)
- [RegisterWorkflowOptions](#registerworkflowoptions)

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

* Options to configure parameters for starting a workflow execution

| Option | Description | Type |
| --- | --- | --- |
| ID | Set the business identifier of the workflow execution | string |
| TaskQueue | Set workflow tasks of the workflow are scheduled on the queue with this name | string |
| WorkflowExecutionTimeout | Set the timeout for duration of workflow execution | time.Duration |
| WorkflowRunTimeout | Set the timeout for duration of a single workflow run | time.Duration |
| WorkflowTaskTimeout | Set the timeout for processing workflow task from the time the worker | time.Duration |
| WorkflowIDReusePolicy | Set if server allow reuse of workflow ID | WorkflowIdReusePolicy |
| WorkflowExecutionErrorWhenAlreadyStarted | Set if Client.ExecuteWorkflow will return an error if the workflow id has already been used | bool |
| RetryPolicy | Set workflow retry policy | RetryPolicy |
| CronSchedule | Set workflow cron schedule | string |
| Memo | Set non-indexed info that will be shown in list workflow | map[string]interface{} |
| SearchAttributes | Set indexed info that can be used in query of List/Scan/Count workflow APIs | map[string]interface{} |

### ActivityOptions

* Options for executing an activity

| Option | Description | Type |
| --- | --- | --- |
| ActivityID | Set the business level activity ID | string |
| TaskQueueName | Set name of the task queue for this activity | string |
| ScheduleToCloseTimeout | Set the total time that a workflow is willing to wait for Activity to complete | time.Duration |
| ScheduleToStartTimeout | Set the time that the Activity Task can stay in the Task Queue before it is picked up by  a worker| time.Duration |
| StartToCloseTimeout | Set the maximum time of a single activity execution attempt | time.Duration |
| HeartbeatTimeout | Set if activity heartbeat interval | time.Duration |
| WaitForCancellation | Set if to wait for canceled activity to be completed | bool |
| OriginalTaskQueueName | Set workflow retry policy | string |
| RetryPolicy | Set workflow retry policy | RetryPolicy |

### ExecuteLocalActivityOptions

* Used to set local activity specific parameters that will be stored inside of a context

| Option | Description | Type |
| --- | --- | --- |
| ScheduleToCloseTimeout | Set the end to end timeout for the local activity including retries | time.Duration |
| StartToCloseTimeout | Set timeout for a single execution of the local activity | time.Duration |
| RetryPolicy | Set how to retry activity if error happens | time.Duration |

### WorkerOptions

* Used to set worker options

| Option | Description | Type |
| --- | --- | --- |
| MaxConcurrentActivityExecutionSize | Set the the maximum concurrent activity executions this worker can have | int |
| WorkerActivitiesPerSecond | Set the rate limiting on number of activities that can be executed per second per worker | float64 |
| MaxConcurrentLocalActivityExecutionSize | Set the maximum concurrent local activity executions this worker can have | int |
| WorkerLocalActivitiesPerSecond | Set the the rate limiting on number of local activities that can be executed per second per worker | float64 |
| TaskQueueActivitiesPerSecond | Set the rate limiting on number of activities that can be executed per second | float64 |
| MaxConcurrentActivityTaskPollers | Set the maximum number of goroutines that will concurrently poll | int |
| MaxConcurrentWorkflowTaskExecutionSize | Set the maximum concurrent workflow task executions this worker can have | int |
| MaxConcurrentWorkflowTaskPollers | Set the maximum number of goroutines that will concurrently poll | int |
| EnableLoggingInReplay | Set to enable logging in replay | bool |
| DisableStickyExecution | Set to disable sticky execution | bool |
| StickyScheduleToStartTimeout | Set the sticky schedule to start timeout | time.Duration |
| BackgroundActivityContext | Set the context for activity | context.Context |
| WorkflowPanicPolicy | Set  how workflow worker deals with non-deterministic history event | WorkflowPanicPolicy |
| WorkerStopTimeout | Set how worker graceful stop timeout | time.Duration |
| EnableSessionWorker | Set to enable running session workers | bool |
| MaxConcurrentSessionExecutionSize | Set the maximum number of concurrently running sessions the resource support | int |
| WorkflowInterceptorChainFactories | Set factories used to instantiate workflow interceptor chain | []WorkflowInterceptor |
| LocalActivityWorkerOnly | Set if worker would only handle workflow tasks and local activities | bool |
| Identity | Set to overwrite the client level Identify value | string |

### ChildWorkflowOptions

* Used to set all child workflow specific options 

| Option | Description | Type |
| --- | --- | --- |
| Namespace | Set the namespace of the child workflow | string |
| WorkflowID | Set the id of the child workflow to be scheduled | string |
| TaskQueue | Set task queue that the child workflow needs to be scheduled on | string |
| WorkflowExecutionTimeout | Set the end to end timeout for the child workflow execution including retries | time.Duration |
| WorkflowRunTimeout | Set the timeout for a single run of the child workflow execution | time.Duration |
| WorkflowTaskTimeout | Set the maximum execution time of a single Workflow Task | time.Duration |
| WaitForCancellation | Set to wait for canceled child workflow to be ended  | bool |
| WorkflowIDReusePolicy | Set if server allow reuse of workflow ID | WorkflowIdReusePolicy |
| RetryPolicy | Set how to retry child workflow if error happens | RetryPolicy |
| CronSchedule | Set the cron schedule for child workflow | string |
| Memo | Set non-indexed info that will be shown in list child workflow | map[string]interface{} |
| SearchAttributes | Set indexed info that can be used in query of List/Scan/Count child workflow APIs | map[string]interface{} |
| ParentClosePolicy | Set policy to decide what to do for the child | ParentClosePolicy |

### RegisterWorkflowOptions

* Used to set options for registering a workflow 

| Option | Description | Type |
| --- | --- | --- |
| Name | Set the name of the workflow | string |
| DisableAlreadyRegisteredCheck | Set to disable the already registered check | bool |
