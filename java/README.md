## Java SDK Options

- [External](#external)
    * [ActivityOptions](#activityoptions)
    * [ChildWorkflowOptions](#childworkflowoptions)
    * [ContinueAsNewOptions](#continueasnewoptions)
    * [LocalActivityOptions](#localactivityoptions)
    * [RetryOptions](#retryoptions)
    * [RpcRetryOptions](#rpcretryoptions)
    * [WorkerFactoryOptions](#workerfactoryoptions)
    * [WorkerOptions](#workeroptions)
    * [WorkflowClientOptions](#workflowclientoptions)
    * [WorkflowImplementationOptions](#workflowimplementationoptions)
    * [WorkflowOptions](#workflowoptions)
    * [WorkflowServiceStubsOptions](#workflowservicestubsoptions)
- [Testing](#testing)
    * [TestEnvironmentOptions](#testenvironmentoptions)
- [Internal](#internal)
    * [PollerOptions](#polleroptions)
    * [SingleWorkflowOptions](#singleworkflowoptions)
    
### External

#### ActivityOptions

* Options used to configure how an activity is invoked

| Option | Description | Type |
| --- | --- | --- |
| setScheduleToCloseTimeout | Total time that a workflow is willing to wait for Activity to complete | Duration |
| setScheduleToStartTimeout | Time that the Activity Task can stay in the Task Queue before it is picked up by a Worker | Duration |
| setStartToCloseTimeout | Maximum time of a single Activity execution attempt | Duration |
| setHeartbeatTimeout | Heartbeat interval | Duration |
| setTaskQueue | Task Queue | String |
| setRetryOptions | Retry options | RetryOptions |
| setContextPropagators | ContextPropagators help propagate the context from the workflow to the activities | List<ContextPropagator> |
| setCancellationType | Activity cancellation type | ActivityCancellationType |

#### ChildWorkflowOptions

* Options used to configure how a child workflow is invoked

| Option | Description | Type |
| --- | --- | --- |
| setNamespace | Specify namespace in which workflow should be started | String |
| setWorkflowId | Workflow id to use when starting | String |
| setWorkflowIdReusePolicy | Specifies server behavior if a completed workflow with the same id exists | WorkflowIdReusePolicy |
| setWorkflowRunTimeout | Time after which workflow run is automatically terminated by the Temporal service | Duration |
| setWorkflowExecutionTimeout | Maximum time that parent workflow is willing to wait for a child execution | Duration |
| setWorkflowTaskTimeout | Maximum execution time of a single workflow task | Duration |
| setRetryOptions | Retry options | RetryOptions |
| setCronSchedule | Cron definition | String |
| setMemo | additional non-indexed information in result of list workflow | String |
| setSearchAttributes | Additional indexed information in result of list workflow | Map<String, Object> |
| setContextPropagators | List of context propagators to use during this workflow | List<ContextPropagator> |
| setMethodRetry | Method retry option | MethodRetry |
| setCronSchedule | Cron definition | CronSchedules |

#### ContinueAsNewOptions

* Options used to configure how a continue as new run is invoked

| Option | Description | Type |
| --- | --- | --- |
| setWorkflowRunTimeout | Time after which workflow run is automatically terminated by the Temporal service | String |
| setTaskQueue | Temporal task queue | String |
| setWorkflowTaskTimeout | Workflow task timeout duration | Duration |
| setMemo | Memo to be added | String |
| setSearchAttributes | Additional indexed information in result of list workflow | Map<String, Object> |

#### LocalActivityOptions

* Options used to configure how a local activity is invoked

| Option | Description | Type |
| --- | --- | --- |
| setScheduleToCloseTimeout | Time a Workflow is willing to wait for an Activity's completion | Duration |
| setLocalRetryThreshold | Maximum time to retry locally, while keeping the Workflow Task open via a Heartbeat | Duration |
| setStartToCloseTimeout | Maximum time of a single Activity execution attempt | Duration |
| setRetryOptions | Define how an Activity is retried in case of failure | RetryOptions |
| setDoNotIncludeArgumentsIntoMarker | Set if the serialized arguments of the local Activity are not included in the Marker Event that stores local activity result | Map<String, Object> |

#### RetryOptions

* Options for how retries should be performed

| Option | Description | Type |
| --- | --- | --- |
| setInitialInterval | Interval of the first retry. If coefficient is 1.0 then it is used for all retries | Duration |
| setBackoffCoefficient | Coefficient used to calculate the next retry interval | double |
| setMaximumAttempts | Maximum number of attempts | int |
| setMaximumInterval | Maximum interval between retries | Duration |
| setDoNotRetry | List of application failures types to not retry | String[] |

#### RpcRetryOptions

* Options for how retries for RPC calls to the server should be performed

| Option | Description | Type |
| --- | --- | --- |
| setInitialInterval | Interval of the first retry. If coefficient is 1.0 then it is used for all retries | Duration |
| setExpiration | Maximum time to retry | Duration |
| setBackoffCoefficient | Coefficient used to calculate the next retry interval | double |
| setMaximumInterval | Maximum interval between retries | Duration |
| setMaximumAttempts | Maximum number of attempts | int |
| setDoNotRetry | List of status codes for which not to retry | List<DoNotRetryPair> |

#### WorkerFactoryOptions

* Options used to configure worker factory

| Option | Description | Type |
| --- | --- | --- |
| setWorkflowCacheSize | Set workflow cache size. Shared across all workers created from same factory | int |
| setMaxWorkflowThreadCount | Maximum number of threads available for workflow execution across all workers created by same factory | int |
| setWorkflowHostLocalTaskQueueScheduleToStartTimeout | Timeout for a workflow task routed to the the host that caches a workflow object. | Duration |
| setWorkerInterceptors | Set worker interceptors | WorkerInterceptor[] |
| setEnableLoggingInReplay | Set, unset logging in replay | boolean |
| setWorkflowHostLocalPollThreadCount | Set local thread poll count | int |

#### WorkerOptions

* Options used to configure worker

| Option | Description | Type |
| --- | --- | --- |
| setMaxWorkerActivitiesPerSecond | Maximum number of activities started per second | double |
| setMaxConcurrentActivityExecutionSize | Maximum number of activities executed in parallel | int |
| setMaxConcurrentWorkflowTaskExecutionSize | Maximum number of simultaneously executed workflow tasks | int |
| setMaxConcurrentLocalActivityExecutionSize | Maximum number of local activities executed in parallel | int |
| setMaxTaskQueueActivitiesPerSecond | Sets the rate limiting on number of activities that can be executed per second | double |
| setWorkflowPollThreadCount | Number of simultaneous poll requests on workflow task queue | int |
| setActivityPollThreadCount | Sets if worker should only handle workflow tasks and local activities | boolean |
| setLocalActivityWorkerOnly | Number of simultaneous poll requests on workflow task queue | int |
| setDefaultDeadlockDetectionTimeout | Time period in ms that will be used the detect workflows deadlock | long |

#### WorkflowClientOptions

* Options used to configure workflow client

| Option | Description | Type |
| --- | --- | --- |
| setDataConverter | Set data converter | DataConverter |
| setInterceptors | Set interceptors used to intercept workflow client calls | WorkflowClientInterceptor[] |
| setIdentity | Set human readable identity of the worker | String |
| setBinaryChecksum | Sets worker binary checksum | String |
| setContextPropagators | Sets the context propagators | List<ContextPropagator> |
| setQueryRejectCondition | Should a query be rejected by closed and failed workflows | QueryRejectCondition |

#### WorkflowImplementationOptions

* Options used to configure workflow implementation

| Option | Description | Type |
| --- | --- | --- |
| setFailWorkflowExceptionTypes | Sets how workflow worker deals with exceptions thrown from the workflow code which include non-deterministic history events | DataConverter |
| setActivityOptions | Set individual activity options per activityType | Map<String, ActivityOptions>[] |
| setDefaultActivityOptions | Set default activity options | ActivityOptions |

#### WorkflowOptions

* Options used to configure workflow

| Option | Description | Type |
| --- | --- | --- |
| setWorkflowId | Set workflow id to use when starting | String |
| setWorkflowIdReusePolicy | Specifies server behavior if a completed workflow with the same id exists | WorkflowIdReusePolicy |
| setWorkflowRunTimeout | Set the time after which workflow run is automatically terminated by Temporal service | Duration |
| setWorkflowExecutionTimeout | Set time after which workflow execution (which includes run retries and continue as new) is automatically terminated | Duration |
| setWorkflowTaskTimeout | Set the maximum execution time of a single Workflow Task | Duration |
| setTaskQueue | Set the task queue | string |
| setRetryOptions | Set the retry options | RetryOptions |
| setCronSchedule | Set the cron schedule | String |
| setMemo | Set additional non-indexed information in result of list workflow | string |
| setSearchAttributes | Set additional indexed information in result of list workflow | Map<String, Object> |
| setContextPropagators | Set the cron schedule | List<ContextPropagator> |

#### WorkflowServiceStubsOptions

* Options used to configure workflow service stub

| Option | Description | Type |
| --- | --- | --- |
| setChannel | Sets gRPC channel to use. Exclusive with target and sslContext | ManagedChannel |
| setSslContext | Sets gRPC SSL Context to use | SslContext |
| setEnableHttps | Sets option to enable SSL/TLS/HTTPS for gRPC | boolean |
| setTarget | Sets a target string | String |
| setRpcTimeout | Sets the rpc timeout value for non query and non long poll calls | Duration |
| setRpcLongPollTimeout | Sets the rpc timeout value | Duration |
| setRpcQueryTimeout | Sets the rpc timeout for queries | Duration |
| setRpcRetryOptions | Set the rpc retry options | RpcRetryOptions |
| setConnectionBackoffResetFrequency | Sets frequency at which gRPC connection backoff should be reset practically | Duration |
| setGrpcReconnectFrequency | Sets frequency at which gRPC channel will be moved into an idle state | Duration |
| setQueryRpcTimeout | Set the query rpc options | Duration |
| setHeaders | Set the headers | Metadata |
| setBlockingStubInterceptor | Set blocking stub interceptor | Function |
| setFutureStubInterceptor | Set the future stub interceptor | Function |
| setMetricsScope | Set the metric scope | Scope |
| setDisableHealthCheck | Set client to make a request to health check endpoint to make sure that the server is accessible | boolean |
| setHealthCheckAttemptTimeout | Set the time to wait between service responses on each health check | Duration |
| setHealthCheckTimeout | Set a HealthCheckTimeout after which to stop waiting while checking server connection when creating a new client | Duration |
| setEnableKeepAlive | Set keep alive ping from client to the server | boolean |
| setKeepAliveTime | Set the keep alive time | Duration |
| setKeepAliveTimeout | Set the keep alive timeout | Duration |
| setKeepAlivePermitWithoutStream | Set if client sends keepalive pings even with no active RPCs | boolean |

### Testing

#### TestEnvironmentOptions

* Options used to configure test environment

| Option | Description | Type |
| --- | --- | --- |
| setWorkflowClientOptions | Set workflow client options | WorkflowClientOptions |
| setWorkerFactoryOptions | Set worker factory options | WorkerFactoryOptions |
| setMetricsScope | Set metric scope | Scope |
| setUseExternalService | Set if test env should use external temporal service | boolean |
| setTarget | Set endpoint for comminication with Temporal service (if external) | String |
| setInitialTimeMillis | Initial time for the workflow virtual clock | long |
| setInitialTime | Enable/disable logging in relay | Instant |

### Internal

#### PollerOptions

* Options for component that polls Temporal task queues for tasks

| Option | Description | Type |
| --- | --- | --- |
| setMaximumPollRatePerSecond | Maximum rate of polling | double |
| setPollBackoffCoefficient | Coefficient to use when calculating exponential delay in case of failures | double |
| setPollBackoffInitialInterval | Initial delay in case of failure. If backoff coefficient is 1 then it would be the constant | Duration |
| setPollBackoffMaximumInterval | Maximum interval between polls in case of failures | Duration |
| setPollThreadCount | Number of parallel polling threads | int |
| setUncaughtExceptionHandler | Called to report unexpected exceptions in the poller threads | Thread.UncaughtExceptionHandler |
| setPollThreadNamePrefix | Prefix to use when naming poller threads | String |


#### SingleWorkflowOptions

* Internal options to configure a single worker

| Option | Description | Type |
| --- | --- | --- |
| setIdentity | Set worker identity | String |
| setBinaryChecksum | Worker binary checksum | String |
| setDataConverter | Data converter to be used with this worker | DataConverter |
| setTaskExecutorThreadPoolSize | Worker task executor thread pool size | int |
| setPollerOptions | Set poller options | PollerOptions |
| setMetricsScope | Set the metric scope | Scope |
| setEnableLoggingInReplay | Enable/disable logging in relay | boolean |
| setContextPropagators | Specifies the list of context propagators to use during this workflow | List<ContextPropagator> |
| setDefaultDeadlockDetectionTimeout | Initial delay in case of failure. If backoff coefficient is 1 then it would be the constant | long |
