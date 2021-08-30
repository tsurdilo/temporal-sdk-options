## NodeJS SDK Options

- [ActivityOption](#activityoption)
    * [LocalActivityOptions](#localactivityoptions)
    * [RemoteActivityOptions](#remoteactivityoptions)
- [ServerOptions](#serveroptions)
- [WorkflowOptions](#workflowoptions)
- [ContinueAsNewOptions](#continueasnewoptions)
- [ChildWorkflowOptions](#childworkflowoptions)

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
