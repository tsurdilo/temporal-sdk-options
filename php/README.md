## PHP SDK Options

- [ActivityOption](#activityoption)
- [ChildWorkflowOptions](#childworkflowoptions)
- [ClientOptions](#clientoptions)
- [ContinueAsNewOptions](#continueasnewoptions)
- [RetryOptions](#retryoptions)
- [WorkerOptions](#workeroptions)
- [WorkflowOptions](#workflowoptions)

### ActivityOption

* Options used to specify activity options

| Option | Description | Type |
| --- | --- | --- |
| $taskQueue | Set the activity task queue | string |
| $scheduleToCloseTimeout | Set the end to end timeout for the activity | DateIntervalType |
| $scheduleToStartTimeout | Set the queue timeout before the activity starts executed | DateIntervalType |
| $startToCloseTimeout | Set the timeout from the start of activity execution to end of it | DateIntervalType |
| $heartbeatTimeout | Set the periodic timeout while the activity is in execution | DateIntervalType |
| $cancellationType | Set the queue timeout before the activity starts executed | ActivityCancellationType |
| $activityId | Set the business level activity ID | string |
| $retryOptions | Set how to retry an Activity if an error occurs | RetryOptions |

### ChildWorkflowOptions

* Options used to specify child workflow options

| Option | Description | Type |
| --- | --- | --- |
| $namespace | Set the child workflow namespace | string |
| $workflowId | Set the child workflow id | string |
| $taskQueue | Set child workflow task queue | string |
| $workflowExecutionTimeout | Set the child workflow execution timeout | DateIntervalType |
| $workflowRunTimeout | Set the child workflow run timeout | DateIntervalType |
| $workflowTaskTimeout | Set the child workflow task timeout | DateIntervalType |
| $cancellationType | Set child workflow cancellation type | ChildWorkflowCancellationType |
| $workflowIdReusePolicy | Set the child workflow id reuse policy | IdReusePolicy |
| $retryOptions | Set child workflow retry options | RetryOptions |
| $cronSchedule | Set the child workflow cron schedule | CronType |
| $parentClosePolicy | Set the child workflow parent close policy | ParentClosePolicy |
| $memo | Set child workflow memo | ArrayType |
| $searchAttributes | Set the child workflow search attributes | ArrayType |

### ClientOptions

* Options used to specify client options

| Option | Description | Type |
| --- | --- | --- |
| $namespace | Set the name space to be used | string |
| $identity | Set the identity | string |
| $queryRejectionCondition | Set the query reject conditions | QueryRejectCondition |

### ContinueAsNewOptions

* Options used to for continue as new

| Option | Description | Type |
| --- | --- | --- |
| $workflowRunTimeout | Set the timeout for a single run of the child workflow execution | DateIntervalType |
| $taskQueue | Set the continue as new task queue | string |
| $workflowTaskTimeout | Set the continue as new workflow timeout | QueryRejectCondition |

### RetryOptions

* Options used for retry options

| Option | Description | Type |
| --- | --- | --- |
| $initialInterval | Set the backoff interval for the first retry | DateIntervalType |
| $backoffCoefficient | Set the coefficient used to calculate the next retry backoff interval | float |
| $maximumInterval | Set the maximum backoff interval between retries | DateIntervalType |
| $maximumAttempts | Set the maximum number of attempts | int |
| $nonRetryableExceptions | Set the non-retryable errors | array |

### WorkerOptions

* Options used to specify worker options

| Option | Description | Type |
| --- | --- | --- |
| $maxConcurrentActivityExecutionSize | Set max concurrent activity exec size | int |
| $workerActivitiesPerSecond | Set max worker activities per second | float |
| $maxConcurrentLocalActivityExecutionSize | Set max concurrent local activities execution size | int |
| $workerLocalActivitiesPerSecond | Set local activities per scond | float |
| $taskQueueActivitiesPerSecond | Set the task queue activities per second | float |
| $maxConcurrentActivityTaskPollers | Set the concurrent activity task pollers | int |
| $maxConcurrentWorkflowTaskExecutionSize | Set the max concurrent workflow task execution size | int |
| $maxConcurrentWorkflowTaskPollers | Set the maximum concurrent workflow task pollers | int |
| $stickyScheduleToStartTimeout | Set the sticky schedule to start timeout | DateInterval |
| $workerStopTimeout | Set worker stop timeout | DateInterval |
| $enableSessionWorker | Set to enable session worker | bool |
| $sessionResourceId | Set the session resource id | string |
| $maxConcurrentSessionExecutionSize | Set the max concurrent session execution size | int |

### WorkflowOptions

* Options used to specify workflow options

| Option | Description | Type |
| --- | --- | --- |
| $workflowId | Set the workflow id | string |
| $taskQueue | Set the workflow task queue | string |
| $workflowExecutionTimeout | Set the workflow execution timeout | DateInterval |
| $workflowRunTimeout | Set the workflow run timeout | DateIntervalType |
| $workflowTaskTimeout | Set workflow task timeout | DateIntervalType |
| $workflowIdReusePolicy | set the workflow id reuse policy | IdReusePolicy |
| $retryOptions | Set the workflow retry options | RetryOptions |
| $cronSchedule | Set the workflow cron schedule | CronType |
| $memo | Set the workflwo memo | ArrayType |
| $searchAttributes | Set the workflow search attributes| ArrayType |

