---
id: errors
title: Errors
sidebar_label: Errors
description: This reference lists possible Workflow Task errors and how to resolve them.
toc_max_heading_level: 4
---

<!-- THIS FILE IS GENERATED. DO NOT EDIT THIS FILE DIRECTLY -->

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

This reference lists possible [Workflow Task](/tasks/#workflow-task) errors and how to resolve them.

> For other types of errors, see [Temporal Failures](https://docs.temporal.io/kb/failures).

Each of the below errors corresponds with a [WorkflowTaskFailedCause](https://api-docs.temporal.io/#temporal.api.enums.v1.WorkflowTaskFailedCause), which appears in [Events](/workflows#event) under `workflow_task_failed_event_attributes`.

## Bad Cancel Timer Attributes

This error indicates that the [Workflow Task](/tasks#workflow-task) failed while attempting to cancel a <a class="tdlp" href="/application-development/features#timers">Timer<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Timer?</span><br /><br /><span class="tdlppd">A Timer lets a Workflow sleep for a fixed time period.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/application-development/features#timers">Learn more</a></span></span></a>.

Check your Timer attributes for a missing Timer Id value.
Add a valid Timer Id and redeploy the code.

## Bad Cancel Workflow Execution Attributes

The [Workflow Task](/tasks#workflow-task) failed due to unset [CancelWorkflowExecution](/references/commands/#cancelworkflowexecution) attributes.

Reset any missing attributes and redeploy the Workflow Task.

## Bad Complete Workflow Execution Attributes

This error indicates that the [Workflow Task](/tasks#workflow-task) failed due to unset attributes on [CompleteWorkflowExecution](/references/commands/#completeworkflowexecution).

Reset any missing attributes.
Adjust the size of your Payload if it exceeds size limits.

## Bad Continue as New Attributes

This error indicates that the [Workflow Task](/tasks#workflow-task) failed to validate a [ContinueAsNew](/references/commands/#continueasnew) attribute.
The attribute could be unset or invalid.

Reset any missing attributes.
If the payload or memo exceeded size limits, adjust the input size.

Check that the [Workflow](/workflows) is validating search attributes after unaliasing keys.

## Bad Fail Workflow Execution Attributes

This error indicates that the [Workflow Task](/tasks#workflow-task) failed due to unset [FailWorkflowExecution](/references/commands/#failworkflowexecution) attributes.

If you encounter this error, make sure that `StartToClostTimeout` or `ScheduleToCloseTimeout` are set.
Restart the [Worker](/workers) that the [Workflow](/workflows) and [Activity](/activities) are registered to.

## Bad Modify Workflow Properties Attributes

This error indicastes that the [Workflow Task](/tasks/#workflow-task) failed to validate attributes on a property in the Upsert Memo or in a payload.
These attributes are either unset or exceeding size limits.

Reset any unset and empty atrributes.
Adjust the size of the [Memo](/workflows/#memo) or payload to fit within the system's limits.

## Bad Record Marker Attributes

This error indicates that the [Workflow Task](/tasks#workflow-task) failed due to an unset or incorrect [Marker](/references/events/#markerrecorded) name.

Enter a valid Marker name and redeploy the Task.

## Bad Request Cancel Activity Attributes

This error either indicates the possibility of unset attributes for [RequestCancelActivity](/references/commands/#requestcancelactivity), or an invalid History Builder state.

Update the [Temporal SDK](/temporal/#temporal-sdk) to the most recent release.
Reset any unset attributes before retrying the [Workflow Task](/tasks#workflow-task).

If you continue to see this error, review your code for [nondeterministic causes](/workflows/#code-changes-can-cause-non-deterministic-behavior).

## Bad Request Cancel External Workflow Execution

This error indicates that the [Workflow Task](/tasks#workflow-task) failed while trying to cancel an [external Workflow](/workflows/#external-workflows).
Unset or invalid attributes can cause this to occur.

Reset any missing attributes, such as Workflow Id or Run Id.
Adjust any fields that exceed length limits.

If a [Child Workflow](/workflows/#child-workflows) is set to `Start` and `RequestCancel`, remove one of these attributes.
A Child Workflow cannot perform both actions in the same Workflow Task.

## Bad Schedule Activity Attributes

This error indicates unset or invalid attributes for [`ScheduleActivityTask`](/references/commands/#scheduleactivitytask) or [`CompleteWorkflowExecution`](/references/commands/#completeworkflowexecution).

Reset any unset or empty attributes.
Adjust the size of the received payload to stay within the given size limit.

## Bad Search Attributes

This error indicates that the [Workflow Task](/tasks#workflow-task) has unset or invalid <a class="tdlp" href="/application-development/observability#search-attributes">Search Attributes<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">How to use Search Attributes</span><br /><br /><span class="tdlppd">Search Attributes enable complex List Filters to find the exact of Workflow Executions you are looking for.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/application-development/observability#search-attributes">Learn more</a></span></span></a>.
This can cause Workflow Tasks to continue to retry without success.

Make sure that all attributes are defined before retrying the Task.
Adjust the size of the Payload to fit within the system's size limits.

## Bad Signal Input Size

This error indicates that the Payload has exceeded the [Signal's](/application-development/features/#signals) available input size.

Adjust the size of the Payload, and redeploy the [Workflow Task](/tasks/#workflow-task).

## Bad Signal Workflow Execution Attributes

This error indicates that the [Workflow Task](/tasks#workflow-task) failed to validate attributes for [SignalExternalWorkflowExecution](/references/commands/#signalexternalworkflowexecution).

Reset any unset, missing, nil, or invalid attributes.
Adjust the input to fit within the system's size limits.

## Bad Start Child Execution Attributes

This error indicates that the [Workflow Task](/tasks#workflow-task) failed to validate attributes for [`StartChildWorkflowExecution`](/references/commands/#startchildworkflowexecution)

Adjust the input size of the attributes to fall within the system's size limits.

Make sure that <a class="tdlp" href="/application-development/observability#search-attributes">Search Attribute<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">How to use Search Attributes</span><br /><br /><span class="tdlppd">Search Attributes enable complex List Filters to find the exact of Workflow Executions you are looking for.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/application-development/observability#search-attributes">Learn more</a></span></span></a> validation is performed after unaliasing keys.

## Bad Start Timer Attributes

This error indicates that the scheduled [Event](/workflows/#event) is missing a <a class="tdlp" href="/application-development/features#timers">Timer Id<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Timer?</span><br /><br /><span class="tdlppd">A Timer lets a Workflow sleep for a fixed time period.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/application-development/features#timers">Learn more</a></span></span></a>.

Set a valid Timer Id and retry the [Workflow Task](/tasks/#workflow-task).

## Cause Bad Binary

This error indicates that the [Worker](/workers) deployment returned a bad binary checksum.

<!-- TODO: get more information about binary -->

## Cause Reset Workflow

This error indicates that the [Workflow Task](/tasks#workflow-task) failed due to a request to reset the [Workflow](/workflows).

If the system hasn't started a new Workflow, manually reset the Workflow.

## Cause Unspecified

This error indicates that the [Workflow Task](/tasks#workflow-task) has failed for an unknown reason.

If you see this error, contact your administrator to file a support ticket or report it [here](https://github.com/temporalio/temporal/issues).

<!--TODO: add link above -->

## Failover Close Command

This error indicates that a [Namespace](/namespaces) failover forced the [Workflow Task](/tasks#workflow-task) to close.
The system automatically schedules a retry when this error occurs.

<!--TODO: troubleshooting -->

## Force Close Command

This error indicates that the [Workflow Task](/tasks#workflow-task) was forced to close.
A retry will be scheduled if the error is recoverable.

<!-- TODO: more info-->

## Non-Deterministic Error

The [Workflow Task](/tasks#workflow-task) failed due to a [nondeterministic error](/workflows/#code-changes-can-cause-non-deterministic-behavior).

<!-- TODO: info -->

## Pending Activities Limit Exceeded

The [Workflow](/workflows) has reached capacity for pending [Activities](/activities).
Therefore, the [Workflow Task](/tasks#workflow-task) was failed to prevent the creation of another Activity.

Let the Workflow complete any current Activities before redeploying the code.

## Pending Child Workflows Limit Exceeded

This error indicates that the [Workflow](/workflows) has reached capacity for pending [Child Workflows](/workflows/#child-workflows).
Therefore, the [Workflow Task](/tasks/#workflow-task)was failed to prevent additional Child Workflows from being added.

Wait for the system to finish any currently running Child Workflows before redploying this Task.

## Pending Request Cancel Limit Exceeded

This error indicates that the [Workflow Task](/tasks/#workflow-task) failed after attempting to add more cancel requests.
The [Workflow](/workflows) has reached capacity for pending requests to cancel other Workflows, and cannot accept more requests.

If you see this error, give the system time to process pending requests before retrying the Task.

## Pending Signals Limit Exceeded

The Workflow has reached capacity for pending Signals.
Therefore, the [Workflow Task](/tasks#workflow-task) was failed after attempting to add more [Signals](/application-development/features/#signals) to an external Workflow.

Wait for Signals to be processed by the Workflow before retrying the Task.

## Reset Sticky Task Queue

This error indicates that the Sticky [Task Queue](/tasks#task-queue)needs to be reset.

If you see this error, reset the Sticky Task Queue.
The system will retry automatically.

## Resource Exhausted Cause Concurrent Limit

This error indicates that the concurrent [poller count](/application-development/worker-performance/#poller-count) has been reached.

<!--TODO: more info needed -->

Adjust the poller count per [Worker](/workers).

## Resource Exhausted Cause Persistence Limit

This error indicates that the persistence rate limit has been reached.

<!--TODO: more info needed -->

## Resource Exhausted Cause RPS Limit

This error indicates that the [Workflow](/workflows) has reached its RPS limit.

<!--TODO: more info needed -->

## Resource Exhausted Cause System Overload

This error indicates that the system is overloaded and cannot allocate further resources to [Workflow Tasks](/tasks#workflow-task).

<!--TODO: more info needed -->

## Resource Exhausted Cause Unspecified

This error indicates that an unknown cause is preventing resources from being allocated to further [Workflow Tasks](/tasks#workflow-task).

<!--TODO: more info needed -->

## Schedule Activity Duplicate Id

The [Workflow Task](/tasks#workflow-task) failed because the [Activity](/activities) Id is already in use.

Check your code to see if you've already specified the same Activity Id in your [Workflow](/workflows).
Enter another Activity Id, and try running the Workflow Task again.

## Start Timer Duplicate Id

This error indicates that a <a class="tdlp" href="/application-development/features#timers">Timer<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Timer?</span><br /><br /><span class="tdlppd">A Timer lets a Workflow sleep for a fixed time period.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/application-development/features#timers">Learn more</a></span></span></a> with the given Timer Id has already started.

Try entering a different Timer Id, and retry the [Workflow Task](/tasks/#workflow-task).

## Unhandled Command

This error indicates new available [Events](/references/events) since the last [Workflow Task](/tasks/#workflow-task) started.
The Workflow Task was failed because the [Workflow](/workflows) attempted to close itself without handling the new Events.

`UnhandledCommand` can happen when the Workflow is receiving a high number of [Signals](/application-development/features/#signals).
If the Workflow doesn't have enough time to handle these Signals, a RetryWorkflow Task is scheduled to handle these new Events.

To prevent this error, drain the Signal Channel with the ReceiveAsync function.

If you continue to see this error, check your logs for failing Workflow Tasks.
The Workflow may have been picked up by a different [Worker](/workers).

## Workflow Worker Unhandled Failure

This error indicates that the [Workflow Task](/tasks#workflow-task) encountered an unhandled failure from the [Workflow Definition](/workflows/#workflow-definition).

<!--TODO: more info needed -->

