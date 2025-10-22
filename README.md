# Workflow Run Policies – Testing Detections
 
Workflow Run Policies allow you to enforce security controls by blocking GitHub Actions workflow runs that violate organization-defined policies. For more information, see [here](https://docs.stepsecurity.io/workflow-run-policies). 

This Repository contains some basic workflows that will trigger for all 4 available policy rule types for testing purposes:

* **Compromised Actions** - Blocks workflow runs containing a known compromised action
* **Allowed Actions** - Blocks workflow runs that do not explicitly allow actions (by specific version, or all versions)
* **Runner Label Dissallow** - Blocks workflow runs that attempt to run on specified runner labels
* **Secret Exfiltration Policy** - Blocks workflows where a non-default branch's workflow file is attempting to access secrets and differes from default branch

## Setting up and Testing Policies
Triggering workflow run policies is very straight forward:
* Set up a policy from the Workflow Run Policies tab on the StepSecurity dashboard for each policy type
* Trigger a workflow that fails for each respective policy type and observe the cancellation on the non-compliant workflow
* Optionally, triggered any one of the workflows via a PR - this also comments the PR with failure context which can be seen here

Below are details on how to set up a rule for each policy type and trigger a detection

### 1. Compromised Actions Policy 
* Create a Workflow Run Policy on app.stepsecurity.io [here]()
* Ensure the policy is set as a **Compromised Actions Policy** and apply it to the repository **workflow-run-policy-workflows**
* Run the workflow [compromised-action.yml]() and observe the job cancellation
* This workflow also triggers on pull_request - take a look at the PR details for failure context 

### 2. Allowed Actions Policy
* Create a Workflow Run Policy on app.stepsecurity.io [here]()
* Ensure the policy is set as a **Allowed Actions Policy** and apply it to the repository **workflow-run-policy-workflows**. You can delete this policy afterwards so it does not block other actions from running. 
* Run the workflow [allowed-action-policy.yml]() and observe the job cancellation

### 3. Runner Label Policy 
* Create a Workflow Run Policy on app.stepsecurity.io [here]()
* Ensure the policy is set as a **Runner Label Policy** and apply it to the repository **workflow-run-policy-workflows**. Set the disallowed runner label as 'windows-latest'
* Run the workflow [runner-label-block.yml]() and observe the job cancellation

### 4. Secret Exfiltration Policy
* Create a Workflow Run Policy on app.stepsecurity.io [here]()
* Ensure the policy is set as a **Secret Exfiltration Policy** and apply it to the repository **workflow-run-policy-workflows**
* **Create a new branch** with the `secret-exfiltration-workflow.yml` (you can open a PR to see the PR comment context)
* Within the new branch, make a dummy commit to trigger the workflow. This simulates a workflow in a non-default branch that attempts to export all repository secrets


 

 

 

 
