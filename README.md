# Workflow Run Policies – Testing Detections
 
Workflow Run Policies allow you to enforce security controls by blocking GitHub Actions workflow runs that violate organization-defined policies. For more information, see [here](https://docs.stepsecurity.io/workflow-run-policies). 

This Repository contains some basic workflows that will trigger for all 4 available policy rule types for testing purposes:

* **Compromised Actions** - Blocks workflow runs containing a known compromised action
* **Allowed Actions** - Blocks workflow runs that do not explicitly allow actions (by specific version, or all versions)
* **Runner Label Dissallow** - Blocks workflow runs that attempt to run on specified runner labels
* **Secret Exfiltration Policy** - Blocks workflows where a non-default branch's workflow has been modified to access repository secrets 

## Setting up and Testing Policies
Triggering workflow run policies is straight forward:
1. Set up a policy from the Workflow Run Policies tab on the StepSecurity dashboard for each policy type
2. Trigger a workflow that fails for each respective policy type and observe the cancellation on the non-compliant workflow
3. (Optional) Trigger any one of the workflows via a PR - StepSecurity will comment on the PR with the failure information for developer context 

Below are details on how to set up a rule for each policy type and trigger a detection

### 1. Compromised Actions Policy 
* Create a Workflow Run Policy on app.stepsecurity.io. You can create a new policy under `Workflow Run Policies -> Policies -> Create Policy`
* Ensure the policy type is set as a `Compromised Actions Policy` and apply it to the repository **workflow-run-policy-workflows**
* Run the workflow [compromised-action.yml](https://github.com/stepsecurity-poc/stepsecurity-poc-workflow-run-policies/blob/main/.github/workflows/compromised-action-block.yml) and observe the job cancellation
* This workflow also triggers on pull_request - take a look at the PR details for failure context 

### 2. Allowed Actions Policy
* Create a Workflow Run Policy on app.stepsecurity.io
* Ensure the policy type is set as an `Allowed Actions Policy` and apply it to the repository **workflow-run-policy-workflows**. 
* Run the workflow [allowed-action-policy.yml](https://github.com/stepsecurity-poc/stepsecurity-poc-workflow-run-policies/blob/main/.github/workflows/allowed-actions-policy.yml) and observe the job cancellation. Any Actions not explicitly allowed will prevent the run from executing

### 3. Runner Label Policy 
* Create a Workflow Run Policy on app.stepsecurity.io
* Ensure the policy type is set as a `Runner Label Policy` and apply it to the repository **workflow-run-policy-workflows**. Set the disallowed runner label as `windows-latest` or any other label to test
* Run the workflow [runner-label-block.yml](https://github.com/stepsecurity-poc/stepsecurity-poc-workflow-run-policies/blob/main/.github/workflows/runner-label-block.yml) and observe the job cancellation

### 4. Secret Exfiltration Policy
* Create a Workflow Run Policy on app.stepsecurity.io 
* Ensure the policy is set as a `Secret Exfiltration Policy` and apply it to the repository **workflow-run-policy-workflows**
* **Create a new branch** that contains the [secret-exfiltration-workflow.yml](https://github.com/stepsecurity-poc/stepsecurity-poc-workflow-run-policies/blob/main/.github/workflows/secret-exfiltration.yml). You can also open a PR to see the PR comment context
* From the new branch, make a dummy commit to trigger the workflow. This simulates a workflow in a non-default branch that attempts to export all repository secrets


 

 

 

 
