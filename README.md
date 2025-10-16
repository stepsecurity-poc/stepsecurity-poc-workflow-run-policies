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

Below are details on how to set up a rule for each policy type

### Compromised Actions Policy 
1) Create a Workflow Run Policy on app.stepsecurity.io
2) Run the workflow [compromised action.yml] and observe the job cancellation




 

 

 

 
