## NodeJS SDK Options

- [ActivityOption](#activityoption)
  * [LocalActivityOptions](#localactivityoptions)
  * [RemoteActivityOptions](#remoteactivityoptions)
- [ServerOptions](#serveroptions)
- [WorkflowOptions](#workflowoptions)
- [ContinueAsNewOptions](#continueasnewoptions)
- [ChildWorkflowOptions](#childworkflowoptions)
- [RetryOptions](#retryoptions)
- [WorkerOptions](#workeroptions)
- [ConnectionOptions](#connectionoptions)
- [WorkflowClientOptions](#workflowclientoptions)

### ActivityOption

* Options used to specify activity options

#### LocalActivityOptions

| Option | Description | Type |
| --- | --- | --- |
| type | Activity type set to 'local' | string |

#### RemoteActivityOptions

| Option | Description | Type |
| --- | --- | --- |
| type | Activity type set to 'remote' | string |
| activityId | Set the identifier to use for tracking the activity in Workflow history | string |
| namespace | Set the Namespace to schedule this activity in | string |
| taskQueue | Set the task queue | string |
| heartbeatTimeout | Set the heartbeat interval | string or number |
| retry | Set the RetryOptions that define how activity is retried in case of failure | RetryOptions |
| startToCloseTimeout | Set the maximum time of a single Activity execution attempt | string or number |
| scheduleToStartTimeout | Set the Time that the Activity Task can stay in the Task Queue before it is picked up by a Worker | string or number |
| scheduleToCloseTimeout | Set the Total time that a workflow is willing to wait for Activity to complete. | string or number |
| cancellationType | Set what the SDK does when the Activity is cancelled | ActivityCancellationType |

### ServerOptions

* Options used to specify server options

| Option | Description | Type |
| --- | --- | --- |
| address | Set the host and optional port of the Temporal server to connect to | string |
| namespace | Set the namespace will we operate under | string |
| identity | Set the identity | string |
| workerBinaryId | Set the worker binary id | string |
| longPollTimeout | Set the Timeout for long polls (polling of task queues) | string |
| tls | Set the TLS configuration options | TLSConfig |

### WorkflowOptions

* Options used to specify workflow options

| Option | Description | Type |
| --- | --- | --- |
| workflowId | Set the workflow id | string |
| workflowIdReusePolicy | Set the workflow id reuse policy | WorkflowIdReusePolicy |
| taskQueue | Set workflow task queue | string |
| retryPolicy | Set the workflow retry policy | IRetryPolicy |
| cronSchedule | Set the workflow cron schedule | string |
| memo | Set the workflow memo | Record<string, any> |
| searchAttributes | Set workflow search attributes | Record<string, string / number / boolean> |
| workflowIdReusePolicy | Set the workflow id reuse policy | WorkflowIdReusePolicy |

### ContinueAsNewOptions

* Options used to specify continue as new options

| Option | Description | Type |
| --- | --- | --- |
| workflowType | Set the continue as new workflow type | string |
| taskQueue | Set the continue as new workflow task queue | string |
| workflowRunTimeout | Set the continue as new workflow run timeout | string |
| workflowTaskTimeout | Set the continue as new workflow task timeout | string |
| memo | Set the continue as new workflow memo | Record<string, any> |
| searchAttributes | Set the continue as new workflow search attributes | Record<string, any> |

### ChildWorkflowOptions

* Options used to specify child workflow options

| Option | Description | Type |
| --- | --- | --- |
| workflowId | Set the workflow id | string |
| workflowIdReusePolicy | Set the workflow id reuse policy | WorkflowIdReusePolicy |
| taskQueue | Set workflow task queue | string |
| retryPolicy | Set the workflow retry policy | IRetryPolicy |
| cronSchedule | Set the workflow cron schedule | string |
| memo | Set the workflow memo | Record<string, any> |
| searchAttributes | Set workflow search attributes | Record<string, string / number / boolean> |
| workflowIdReusePolicy | Set the workflow id reuse policy | WorkflowIdReusePolicy |
| cancellationType | Set child workflow cancellation type | ChildWorkflowCancellationType |
| parentClosePolicy | Set the child workflow parent close policy | ParentClosePolicy |


### RetryOptions

* Options used to specify activity retries

| Option | Description | Type |
| --- | --- | --- |
| backoffCoefficient | Coefficient used to calculate the next retry interval. The next retry interval is previous interval multiplied by this coefficient | number |
| initialInterval | Interval of the first retry. If coefficient is 1 then it is used for all retries | string / number |
| maximumAttempts | Maximum number of attempts. When exceeded the retries stop even if not expired yet | number |
| maximumInterval | Maximum interval between retries. Exponential backoff leads to interval increase. This value is the cap of the increase | string / number |
| nonRetryableErrorTypes | List of application failures types to not retry | string[] |


### WorkerOptions

* Options used to specify worker configuration

| Option | Description | Type |
| --- | --- | --- |
| activitiesPath | Path to look up activities in. Automatically discovered if workDir is provided | string |
| activityDefaults | Activities created in workflows will default to having these options | ActivityOptions |
| dataConverter | Set the data converter | DataConverters |
| interceptors | A mapping of interceptor type to a list of factories or module paths | WorkerInterceptors |
| isolateExecutionTimeout | List of application failures types to not retry | string[] |
| isolatePoolSize | Controls number of v8 isolates the Worker should create | number |
| logger | Custom logger for the worker, by default we log everything to stderr | Logger |
| maxCachedWorkflows | The number of Workflow isolates to keep in cached in memory | number |
| maxConcurrentActivityTaskExecutions | Maximum number of Activity tasks to execute concurrently | number |
| maxConcurrentActivityTaskPolls | Maximum number of concurrent poll Activity task requests to perform at a time | number |
| maxConcurrentWorkflowTaskExecutions | Maximum number of Workflow tasks to execute concurrently | number |
| maxConcurrentWorkflowTaskPolls | Maximum number of concurrent poll Workflow task requests to perform at a time | number |
| maxIsolateMemoryMB | Memory limit in MB for the Workflow v8 isolate | number |
| nodeModulesPath | Path for webpack to look up modules in for bundling the Workflow code | string |
| nonStickyToStickyPollRatio | maxConcurrentWorkflowTaskPolls * this number = the number of max pollers that will be allowed for the sticky queue | number |
| shutdownGraceTime | Time to wait for pending tasks to drain after shutdown was requested. | string / number |
| shutdownSignals | Automatically shut down worker on any of these signals. | Signals[] |
| stickyQueueScheduleToStartTimeout | How long a workflow task is allowed to sit on the sticky queue before it is timed out and moved to the non-sticky | string |
| taskQueue | The task queue the worker will pull from | string |
| workDir | If provided, automatically discover Workflows and Activities relative to path | string |
| workflowsPath | Path to look up workflows in. Automatically discovered if workDir is provided | string |


### ConnectionOptions

* Options used to specify connection configuration

| Option | Description | Type |
| --- | --- | --- |
| address | Server hostname and optional port. Port defaults to 7233 if address contains only host. | string |
| channelArgs | GRPC Channel arguments | Record<string, any> |
| credentials | Channel credentials, create using the factory methods defined here | ChannelCredentials |
| tls | TLS configuration | WorkerInterceptors |

### WorkflowClientOptions

* Options used to specify workflow client options

| Option | Description | Type |
| --- | --- | --- |
| dataConverter | DataConverter to use for serializing and deserializing payloads | DataConverter |
| identity | Identity to report to the server | string |
| interceptors | Used to override and extend default Connection functionality | WorkflowClientInterceptors |
| namespace | Server namespace | string |
| queryRejectCondition | Should a query be rejected by closed and failed workflows | QueryRejectCondition |